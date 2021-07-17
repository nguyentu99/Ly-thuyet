## Lý thuyết ngày 1 
# PHP căn bản
 1. PHP làm việc như thế nào 
 2. Cấu hình php.ini
    - Dùng để thay đổi cấu hình  
    - các cách thay đổi cấu hình php.ini 
        + Server API – Apache: chỉnh sửa các thiết lập thông qua một tập tin .htaccess
        + Server API – CGI : chỉnh sửa file php.ini để thay đổi các thiết lập PHP
    - Các thiết lập thường sử dụng: 
        + disable_functions: Vô hiệu hóa 1 số hàm có sẵn 
        + expose_php: Ẩn thông tin về PHP trên HTTP Header -> chỉ cần sửa giá trị thành off
        + max_execution_time: Gia hạn thời gian thực thi nếu cần trên 30s
        + memory_limit: Bộ nhớ của hệ thống
        + error_reporting: Hiển thị các lỗi như warning error, ... có thể tùy chọn hiển thị các lỗi nhất định 
        + display_errors: Tùy chọn hiển thị lỗi ra ngoài web -> nên sửa thành ol
        + log_errors: Lưu lỗi vào tập tin log
        + file_uploads: Cho phép upload tập tin thông qua php
        + upload_max_filesize: Dung lượng tối đa tập tin khi upload
 3.	PHP tag 
    - Là các kiểu thẻ đóng mở trong php 
        + <?php ?>
        + <?= ?>
        + <? ?>
        + <% %>
 4.	PHP statements & Whitespace
    - Statements: 
        + If else elseif
        + switch case

    - Whitespace: 
        + Là thứ không hiển thị trên màn hình  (Dấu cách, tab, ...)
        + Không phân biệt khoảng trắng, nhiều whitespace cũng coi như là 1 
 5. Comments
    - Không được thực thi
    - Ghi nhớ những gì đã làm
    - Giúp người khác có thể đọc được code 
    - Các loại comment:
        + //    : Comment 1 dòng
        + #     : Comment 1 dòng
        + /* */ : 1 khối bình luận nhiều dòng, giữa 1 đoạn code. VD: $a = 5 /*+ 10 */ + 5
 6. Php function 
    - Có hơn 1000 hàm có sẵn
    - Có thể tạo và tùy biến theo ý riêng: 
        + Là 1 khối có thể sử dụng được nhiều lần 
        + Không được thực thi khi reload pages mà phải được gọi 
        + Bắt đầu bằng chữ cái hoặc gạch dưới
        + Không phân biệt hoa thường 
        + Nên đặt tên phản ánh thứ cần làm 
    - Tạo 1 function:
        + function funcName(){
            //code
        }
    - Đối số function: 
        + Giống như 1 biến
        + Đối số nằm trong (), Có thể thêm nhiều đối số & sử dụng dấu phẩy để ngăn cách
            VD: 
                function vName($name){
                    echo "Do $name";
                }

                vName('Vu');  //-> Do Vu
        + Đối số mặc định: Khi không truyền đối số sẽ lấy đối số mặc định. 
            VD: 
                function vName($name = Vu){
                    echo "Hi $name";
                }

                vName('Nam');   //-> Do Nam
                vName();        //-> Do Vu
    - Trả về giá trị
        + Dùng 'return' để trả về giá trị
 7. Echo & Print
    - Cả 2 đề dùng để in ra màn hình 
    - Echo :   
        + Không trả về giá trị
        + Có thể lấy nhiều tham số 
        + Nhanh hơn print   

    - Print: 
        + Trả về giá trị là 1
        + Chỉ lấy được 1 tham số
        + Chậm hơn echo    
 8. Biến   
    - Dùng để lưu trữ dữ liệu 
    - Các loại biến: 
        + Biến toàn cục: Có thể sử dụng được ở mọi nơi
        + Biến cục bộ: Chỉ sử dụng được trong func
        + Biến static: 
    - Cách đặt tên và sử dụng: 
        + Bắt đầu bằng $ 
        + Tên phải bắt đầu bằng chữ hoặc _
        + Không được bắt đầu bằng số 
        + Có phân biệt hoa thường 
    - Superglobal
        + $GLOBALS : sử dụng để truy cập biến toàn cục từ bắt kì đâu
	    + $_SERVER : chứa thông tin về tiêu đề, đường dẫn, vị trí tập lệnh
	    + $_REQUEST : thu thập dữ liệu từ form html
	    + $_POST : thu thập dữ liệu thừ form html bằng phương thức post
	    + $_GET : thu thập dữ liệu thừ form html bằng phương thức get
	    + $_FILES : 
	    + $_ENV
	    + $_COOKIE : lưu trũ dữ liệu tạm thời trên trình duyệt
	    + $_SESSION : Lữu trữ dữ liệu tạm thời trên serve

    - Constant
        + Không thể thay đổi trong quá trình thực thi 
        + Dùng define để khai báo 
        + define(name, value, case-insensitive)
 9. Toán tử 
    - Số học: + , - , * , / , % , **
    - Toán tử gán: = , += , -= , ...
    - So sánh : == , === , != , <> , !== , >= , <= 
    - Tăng giảm : ++a, a++ , --a , a--
    - Logic : and, or , xor, && , || , !
    - Chuyển đổi :  ? : , ?? 
 10. Thứ tự toán tử 
    Loại	            Toán tử	            Thứ tự ưu tiên
    Unary	            ! ++ --	            Phải sang trái
    Tính nhân	         * / %	            Trái sang phải
    Tính cộng	          + -	            Trái sang phải
    Quan hệ	            < <= > >=	        Trái sang phải
    Tính bằng	          == !=	            Trái sang phải
    Logic AND	            &&	            Trái sang phải
    Logic OR	            ||	            Trái sang phải
    Điều kiện	            ?:	            Phải sang trái
    Gán             = += -= *= /= %=	    Phải sang trái

 11. Date time
    - Sử dụng hàm date() để định dạng ngày hoặc giờ 
    - Các ký tự thường sử dụng cho ngày tháng, giờ, phút, giây: 
        + d : Ngày trong tháng
        + m : Tháng
        + y : Năm
        + l : Ngày trong tuần 
        + H : 24 h 
        + h : 12h
        + i : 0 - 59 ( Phút)
        + s : 0 - 59 (giây)
        + a : am or pm 
    - Sử dụng hàm date_default_timezone_set() để set vị trí 
    - Sử dụng hàm mktime() Lấy giờ hiện tại truyền vào 

# Điều khiển flow
 1. Xử lý sự kiện
    - If else : Kiểm tra đk nếu đúng thì nhảy vào if không thì else
    - Switch ... case : Dùng khi phải if else nhiều 
 2. Vòng lặp 
    - while : Lặp với điều kiện đúng
    - do ... while: Lặp ít nhất 1 lần mới kiểm tra điều kiện
    - for : Lặp khối mã với số lần được chỉ định 
    - foreach : Lặp mảng 
    - Break & continue : 
        + Break: Thoát khỏi vòng lặp
        + Continue: Ngắt 1 lần lặp 

# Lý thuyết mảng
1. Mảng
    - Khởi tạo mảng
        + $name = array("x","y","z") hoặc $name = ["x","y","z"]
        + count trả lại chiều dài mảng
        + Các phần tử của mảng có thể lưu trữ ở bất kì biến nào
    - Thêm phần tử vào mảng
        + $name[] = "x"
    - Duyệt mảng
        + Sử dụng các vòng lặp để duyệt mảng (for, foreach, while)
        + foreach($name as $x){
            echo "$x";
        }

2. Mảng kết hợp
    - Khởi tạo mảng
        + $name = array(
            'chuỗi 1' => " giá trị 1 ",
            'chuỗi 2' => " giá trị 2 ",
            'chuỗi 3' => " giá trị 3 "
        )
        + $name = ['
            chuỗi 1' => " giá trị 1 ",
            'chuỗi 2' => " giá trị 2 ",
            'chuỗi 3' => " giá trị 3 "
        ]
    - Thêm phần tử vào mảng
        + $name[] = 'chuỗi thêm' => "giá trị thêm"
    - Duyệt mảng
        + Sử dụng các vòng lặp để duyệt mảng (for, foreach, while)
        + foreach($name => $key as $x){
            echo "chỉ số $key giá trị $x"
        }

3. Mảng 2 chiều
    - Khởi tạo mảng
        + $name = array(
            array("Volvo",22,18),
            array("BMW",15,13),
            array("Saab",5,2)
        )
        + $diem = [
            'Hùng' => [
                'Toán' => 8,
                'Lý' => 7,
                'Hóa'  => 9
            ],
        ];

