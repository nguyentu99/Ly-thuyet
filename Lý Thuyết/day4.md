## Lý thuyết ngày 4
# Session & Cookies
1. Cookies
    - Lưu trữ thông tin và được lưu ở máy tính người dùng
    - Tạo cookies: một cookie được tạo với setcookie()
        + setcookie(name, value, expire, path, domain, secure, httponly);
    - Khai báo hoạc lấy cookies: sử dụng biến $_COOKIE
2. Session
    - Lưu trữ thông tin và được lưu trữ ở serve
    - Session bắt đầu làm việc khi có hàm session_start()
        + session_stat() phải khai báo trước html
    - Khai báo hoạc lấy cookies: sử dụng biến $_SESSION
    - session_unset(): loại bỏ tất cả các session
    - session_destroy(): hủy 1 session

# Object-Oriented PHP
* OOP có 2 thuật ngữ quan trọng là object & class 
    + Class: Là bản thiết kế
    +. Object: Thực hiện thiết kế 
* Có 4 tính chất chính:
    + Trừu tượng (abstraction)
    + Kế thừa (inheritance)
    + Đóng gói (encapsulation)
    + Đa hình (polymorphism)
1. Class & Object
    - Khai báo Class & Object
        + class nameClass {
            public $nameObject;
        }
2. Làm việc với Properties và Functions 
    - set_name () và get_name () để thiết lập và lấy thuộc tính từ Object
    - __construct() tự động gọi hàm này khi bạn tạo một đối tượng từ một lớp
    - __destruct() tự động gọi hàm này ở cuối tập lệnh.
3. Quyền truy cập
    - public: thuộc tính hoặc phương thức có thể được truy cập từ mọi nơi.
    - private: thuộc tính hoặc phương thức chỉ có thể được truy cập trong lớp (không được kế thừa)
    - protected: thuộc tính hoặc phương thức chỉ có thể được truy cập trong lớp và lớp con kế thừa nó
4. Kế thừa (extends)
    - Kế thừa các thuộc tính & phương thức của lớp cha 
    - Sử dụng từ khóa extends để khai báo.
    - Khi khai báo là protected thì lớp con phải gọi func đó.
    - Có thể bị ghi đè bằng cách sử dụng trùng tên với lớp cha.
5. Interfaces 
    - Cho phép chỉ định một lớp nên triển khai.
    - Nó như 1 bản thiết kế cho các class có chung cách hoạt động
    - Các phương thức được định nghĩa sẽ không được viết code trong hàm
    - không có khai niệm về phạm vi, tất cả đều public
    - 1 lớp có thể kế thừa nhiều interface
    - Lớp con kế thừa thì phải điịnh nghĩa lại các phương thức trong interface
    - ví dụ
        + interface chu{
            function a()
        }
        + class test implements chu{
            function a(){
            }
        }
6. Abstract
    - là lớp trìu tượng được xây dựng lên như 1 lớp cha cho các lớp con có cùng bản chất
    - 1 class có thể kế từ lớp abstract
    - có thể khai báo và phương thức như bình thường
    - các phương thức abstract trong lớp abstract không được viết code trong nó
    - các lớp con phải ghi đè (override) lại lớp cha để viết tiếp chức năng
    - Không được khởi tạo đối tượng cho lớp đấy
7. 3-TIERS 
    - Tầng Presentation: được dùng để giao tiếp với người dùng, nhiệm vụ chính là hiển thị dữ liệu và nhận dữ liệu từ người dùng.
    - Tầng Business Logic: nhiệm vụ chính là cung cấp các chức năng của phần mềm.
    - Tầng Data: lưu trữ dữ liệu, cho phép lớp Business Logic có thể tìm kiếm, trích xuất, cập nhật… dữ liệu.
    - Ưu điểm:
        + Dễ dàng mở rộng, thay đổi quy mô của hệ thống: Khi cần tải lớn, người quản trị có thể dễ dàng thêm các máy chủ vào nhóm, hoặc lấy bớt ra trong trường hợp ngược lại.
    - Nhược điểm:
        + Việc truyền dữ liệu giữa các tầng sẽ chậm hơn vì phải truyền giữa các tiến trình khác nhau (IPC), dữ liệu cần phải được đóng gói -> truyền đi -> mở gói trước khi có thể dùng được.
        + Việc phát triển ứng dụng phức tạp hơn.