# Cấu trúc thư mục
    - app: chứa hầu hết lớp làm việc
    - bootstrap: chứa các tệp bộ nhớ cache của tuyến đường và dịch vụ (thường sẽ ko sửa đổi)
    - config: chứa tất cả các cấu hình của ứng dụng
    - database: sử dụng để chứa cơ sở dữ liệu SQLite.
    - public: chứa các nội dung như về phía font-end như css, js, image ...
    - resources: chứa tất cả các tệp ngôn ngữ của bạn.
    - routes: chứa các đường đẫn.
    - storage: tệp do người dùng tạo, chẳng hạn như ảnh đại diện hồ sơ
    - tests: chứa các bài kiểm tra tự động.
    - env: file chứa các cấu hình database

# Vòng đời Request
    - public/index.php -> App/Http/Kernel.php -> service provider -> autoload()
        ->Bootstrap Service provider -> Route -> Control -> View

# Route
1. Định tuyến cơ bản
    - VD: Route::get('/hello', function () {
        return 'Hello World';
    });
    - Khi người dùng chỉ dến url /hello thì sẽ  hiển thị "hello world" re màn hình
2. Định tuyến mặc định
    - CSRF: tạo ra 1 token mã hóa thông tin mà người dùng gửi
    - Route::get('/user', [NameController::class, 'index']);
        + /user: đường link khi nhập trên url
        + NameController: Tên controller xử lý
        + index: là tên hàm xử lý
3. Các phương pháp bộ định tuyến khả dụng
    - Route::get($uri, $callback);
    - Route::post($uri, $callback);
    - Route::put($uri, $callback);
    - Route::patch($uri, $callback);
    - Route::delete($uri, $callback);
    - Route::options($uri, $callback);
4. Các tuyến đường chuyển hướng
    - Route::redirect('/here', '/there')
        + here: trang hiện tại
        + there: trang chuyển hướng
    - Route::redirect('/here', '/there', 301);
        + 301: thông báo rằng trang web này đã chuyển hướng vĩnh viễn
        + Mặc định là 302: thông báo rằng trang web này đã chuyển hướng tạm thời
    - Tên Route: ->name('nameRoute'): thuận tiện hơn khi chuyển hướng các route
        + VD: Route::post('posts', 'PostController@store')->name('store');
            Route::get('/user', [UserController::class, 'index']);
    - Nhóm Route: những route có chung hành vi thì chúng ta sẽ nhóm route vào
        + VD:Route::group(['namespace' => 'Admin'], function () {
                Route::get('/', function ()    {
                    //code
                });

                Route::get('posts', function () {
                    //code
                });
            });
    - Prefix: để URL định nghĩa route ngắn gọn dễ nhìn hơn.
        + VD:Route::group(['prefix' => 'admin'], function () {
                Route::get('posts', 'PostController@index');
                Route::get('posts/create', 'PostController@create');
            };
    - Ràng buộc(->where()): nó chỉ được chứa các ký tự tring where
5. Tham số tùy chọn 
    - khi cần truyền tham số trên đường dẫn, chúng ta cũng có thể truyền trong route
    - VD:Route::get('user/{id}', function($id) {
            echo 'ID của user là: ' . $id;
        });

# Controller
1. Câu lệnh tạo controller
    - php artisan make:controller LoginController --resource
    - resource: để tạo sẵn các function
2. Khai báo
    - Route::resource('photos', 'PhotoController'); // khai báo từng thành phần
    - Route::resources([
        'photos' => 'PhotoController',
        'posts' => 'PostController'
    ]);   // khai báo gộp
3. Cách giả method
    - Trong HTML không có các method PUT, PATCH, DELETE nên cần dùng lệnh @method để gán
    - VD: <form action="/foo/bar" method="POST">
            @method('PUT')
        </form>

# Migrations 
    - Để chạy migration cần:
        + Kết nối database
        + Migrations muốn sử dụng được thì phải nằm trong thư mục App\database\migrations
    - Tạo migration
        + php artisan make:migration create_flights_table //tạo bảng flights
    - Rollback/Migrate
        + php artisan migrate:refresh(xóa hết csdl và chạy lại csdl migrate)
        + php artisan migrate:rollback -step=n(rollback data đến lần thứ n)
    - Schema
        + tạo 1 bảng mới trong database sử dụng Schema::create
        + kiểm tra xem table hoặc column có tồn tại không Schema::hasTable/hasColumn
        + đổi tên bảng từ post sang posts Schema::rename('post', 'posts')
        + xóa bảng thì có thể sử dụng Schema::drop() or Schema::dropIfExists();
    - Column Modifier:  $table->string('address')->nullable(); //ko được null
    - Modifying Columns 
        + Sử dụng để đổi tên cột trong bảng sử dụng thư viện doctrine(gõ lệnh composer require doctrine/dbal)
        + Schema::table('users', function ($table) {
            $table->string('name', 50)->nullable()->change();
        });
    - Khóa ngoại
        + $table->foreign('user_id')->references('id')->on('users');

# Seending
    - file tạo dữ liệu mẫu  
    - Tạo seender: php artisan make:seed seedName
    - Cách chạy seender
        + dùng lệnh: php artisan db:seed --class=Users
        + Vào file DatabaseSeeder.php thêm đoạn $this->call(Users::class); vào hàm run (Users có thể thay đổi bằng tên file của bạn muốn thực hiện lệnh) và chúng ta lại dùng lệnh php artisan db:seed

# Model
1. Tạo Model
    - php artisan make:model News
    - php arisan make:model News --migration(tạo luôn migration cho model)
2. Khai báo
    - Muốn sử dụng bảng dữ liệu nào trong database thì phải khai báo ở model
        + table: protected $table = 'tableName';
        + column: protected $fillable = ['column1', 'column2',.. , 'columnn'];
    - Khai báo timestamps: cung cấp biến có sử dụng timestamps

# Thao tác với Database qua Eloquent Model
1. thao dữ liệu
    - Khởi tạo thực thể ($product = new Product;)
    - Gán giá trị cho các thuộc tính rồi gọi đên phương thức như:
        + find(): lấy ra mảng id người dùng
        + save(): để insert và update dữ liệu
        + firstOrCreate: tìm thông tin trong CSDL nếu không có thì insert bản ghi

# Mối quan hệ trong Model
1. Laravel cung cấp 1 biến khóa ngoại với cú pháp
    - Quan hệ 1:1
        + hasOne('App\FeaturedImages', 'foreign_key');
        + belongTo là ngược lại với hasOne(cú pháp giống hasOne)
    - Quan hệ 1:n
        + hasMany('App\Posts', 'author_id', 'local_key');
    - Quan hệ n:n
        + belongstoMany('App\category', 'table_medium', 'posts_id', 'category_id');
        + Truy cập vào table trung gian qua qua hệ n:n sử dụng phương thức pivot attribute

# Truyền tham số từ Controller sang View
1. Dùng compact()
    view('tenview', compact('tencuabientruyenvao'));
2. Dùng with()
    view('tenview')->with('key', 'value');
3. Dùng mảng
    view('tenview', ['key' => 'value']);

# Varidate
    - xác thực nhanh dữ liệu trên ứng dụng
    - không nên viết validate bên trong controller nó khiến web nặng hơn
        + sử dụng câu lệnh 
            * php artisan make:request <className> để tạo forder Request 
            * sửa authorize thành true để sử dụng request
    - các trường validate hay dùng
        + alpha:  chữ cái
        + alpha_dash: chữ, số , kí tự _ -
        + alpha_num: chữ và số
        + min, max: kích thước tối đa của chuỗi
        + boolean: true, false, 1, 0, "1", "0"
        + same, confirmed: kiểm tra với form nhập trước có giống nhau không
        + numeric: số
        + required: check null
        + size: kích thước đầu vào
        + string: xác định chuỗi
        + timezone: xác định múi giờ
        + unique: xác định không tồn tại giá trị trong bảng đã cho

# In lỗi ra view
1. in lỗi re view có 3 cách
    - in từng 
        + cách 1: lỗi validate
        @if($errors->has('password'))
            <div class="alert alert-danger" role="alert">
                {{$errors->first('password')}}
            </div>
        @endif
        + cách 2: lỗi validate
        @error('username')
            <div class="alert alert-danger">{{ $message }}</div>
        @enderror
    - in tất cả lỗi
        @if ($errors->any())
            <div class="alert alert-danger">
                <ul>
                    @foreach ($errors->all() as $error)
                        <li>{{ $error }}</li>
                    @endforeach
                </ul>
            </div>
        @endif

# Database Query
1. Hiển thị thêm sử xóa
    - Lấy số cột nhất định
        + first(): lấy 1 cột
        + find(n): lấy ra n cột
        + pluck: lấy ra danh sách tiêu đề
        + chunk: chỉnh sửa số nhiều bản ghi cùng lúc
    - Lấy ra số cột null
        + whereNull / whereNotNull / orWhereNull / orWhereNotNull
    - Lấy ra thời gian nhập vào
        + whereDate / whereMonth / whereDay / whereYear / whereTime
    - lấy ra và so sánh các cột
        + whereColumn / orWhereColumn
    - xắp xếp có thể theo thời gian
        + latest và oldest
    

        

