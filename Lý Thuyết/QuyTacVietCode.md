# Quy tắc viết code chuẩn
1. PSR-1 - viết code
    - Các file code phải sử dụng các thẻ <?php <?= <?
        + <?php sử dụng cho code nhiều dòng
        + <? sử dụng cho code ít dòng
        + <?= chỉ viết echo không viết các biến
    - File code phải sử dụng encode: UTF-8
    - Tên lớp có dạng NameClass
    - Hằng số trong class tất cả phải viết hoa và chia ra bởi dấu _
    - Tên function của lớp phải ở dạng camelCase
2. PSR-2 - trình bày code
    - code phải dùng 4 ký tự space để lùi code( không dùng tab)
    - Dòng code thường dưới 80 ký tự
    - phải có 1 dòng trắng sau khi khai báo namespace và sau mỗi khối code
    - Kí tự mở { phải ở dòng tiếp theo sau Class
    - kí tự dóng } phải ở dòng tiếp theo sau thân class
    - Các từ khóa điều khiển khối (if, elseif, else) PHẢI có một khoảng trống sau chúng
    - Hằng số true, false, null PHẢI viết với chữ thường.
    - keyword var KHÔNG ĐƯỢC dùng sử dụng khai báo property.
    - Tên thuộc tính không có dấu _

# Quy tắc đặt tên trong laravel
1. Controllers
    - Tên Controller phải bắt đầu bằng 1 danh từ
    - Danh từ phải để dạng số ít
    - Theo sau đó là hậu tố Controller
    - Tên lớp phải trùng tên file
2. Models
    - Chữ cái đầu tiên của class phải viết hoa
    - Phải là danh từ dạng số ít
    - Phương thức định nghĩa hasOne, belongsTo phải là danh từ số ít
    - Các phương thức quan hệ khác phải là danh từ số nhiều
    - thuộc tinh Models phải ở dạng snake_case
    - Phương thức Model phải ở dạng camelCase
3. Function
    - Nếu function dài quá 25 dòng nên tách nhỏ function
    - Nên sử dụng autoload của Composer để load các function
4. Routes
    - Routes phải ở dạng số nhiều và các chữ cái đếu là chữ thường
    - Tên user phải ở dạng snake_case
5. Variables
    - Tên biến phải ở dạng camelCase
    - Tên 1 object đặt theo quy tắc mô tả + danh từ số ít
        VD: $activeUser = User::active()->first()
    - Tên 1 collection đặt theo quy tắc mô tả + danh từ số nhiều
6. View
    - Tên của view thường đặt ở dạng snake_case hoặc kebab-case
    - Không nên xử lý logic trong file view mà xử lý trong file controller
7. Database
    - Tên table phải là danh từ số nhiều
    - Tên cột phải có dạng snake_case
    - Khóa ngoại phải ở dạng tên Model + _id
    - Khóa trính phải là id
