## Lý thuyết ngày 2
# Chuỗi
1. Định dạng chuỗi
    - cách định dạng chuỗi để trong dấu ' ' hoặc " "
    - Các chuỗi có thể được nối bằng dấu .
    - Một giá trị được chuyển đổi thành một chuỗi bằng cách sử dụng hàm ép kiểu string hoặc hàm strval ()
    - Các hàm xử lý chuỗi hay dùng 
        + strlen(): đếm số phần tử của chuỗi
        + str_word_count() : đếm số từ của chuỗi
        + strrev() : đảo ngược chuỗi
        + strpos() : tìm văn bản trong chuỗi
        + str_replace() : thay thế văn bản trong chuỗi
        + md5(): mã hóa chuỗi theo md5
        + sha1() : mã hóa chuỗi theo sha1
        + htmlentities():  chuyển các thể html trong chuỗi sang  dạng thực thể của chúng
        + trim() : loại bỏ khoảng trắng
        + json_decode(): chuyển chuỗi dạng JSON sang các đối tượng mảng hoặc object
        + addcslashes ($str, $char_list): thêm dấu gạch chéo (\) đằng trước những ký tự trong chuỗi $str mà ta liệt kê ở $char_list.
        + addslashes ( $str ):thêm dấu gách chéo trước những ký tự (‘, “, \) trong chuỗi $str.
        + stripslashes ($str): xóa các ký tự \ trong chuỗi $str.
        + crc32 ( $str ): chuyển chuỗi $str thành một dãy số nguyên
    - Các hàm xử lý đặc biệt mb_xxx(Mulibyte)
        + mbstring xử lý chuyển đổi mã hóa ký tự giữa các cặp mã hóa có thể có. mbstring được thiết kế để xử lý các mã hóa dựa trên Unicode như UTF-8 và UCS-2 và nhiều mã hóa byte đơn để thuận tiện
    - Magic Quotes 
        + magic_quotes cho các hoạt động GPC (Get / Post / Cookie). Khi bật magic_quotes, tất cả '(dấu nháy đơn), "(dấu nháy kép), \ (dấu gạch chéo ngược) và NUL sẽ tự động thoát ra bằng dấu gạch chéo ngược.
        + magic_quotes_runtime: Nếu magic_quotes_runtime được bật, hầu hết các hàm trả về dữ liệu từ bất kỳ loại nguồn bên ngoài nào bao gồm cơ sở dữ liệu và tệp văn bản sẽ có dấu ngoặc kép được thoát bằng dấu gạch chéo ngược. 

2. PHP và form HTML
    - Form HTML
        + Được sử dụng để thu thập thông tin đầu vào của người dùng. Đầu vào của người dùng thường được gửi đến máy chủ để xử lý
        + Thành phần HTML  
            * <input>: có thể được hiển thị theo nhiều cách, tùy thuộc vào type thuộc tính.
            * <label>: xác định nhãn cho một số phần tử biểu mẫu.
            * <select>: xác định danh sách thả xuống
            * <textarea>: xác định trường nhập nhiều dòng
            * <button>: xác định một nút có thể nhấn
            * <fieldset>: sử dụng để nhóm dữ liệu liên quan trong một biểu mẫu
            * <legend>: chú thích cho cho fieldset
            * <datalist>: danh sách các tùy chọn được xác định trước cho một phần tử input
            * <output>: đại diện cho kết quả của một phép tính 
            * <option>: định nghĩa một tùy chọn trong một danh sách lựa chọn.
            * <optgroup>: sử dụng để lựa chọn nhóm liên quan trong một phần tử select
        + Phương thức GET 
            * Gửi dữ liệu thông qua đường dẫn URL nằm trên thanh địa chỉ của Browser
            * Phương thức GET được giới hạn gửi tối đa chỉ 2048 ký tự
            * Dữ liệu gửi đi được lưu lại trong lịch sử web và có thể xem lại
            * Không được bảo mật
        + Phương thức POST
            * Được bảo mật
            * Không hạn chế kích thước dữ liệu sẽ gửi
            * Truyền thông tin thông qua HTTP header
        + Validate đơn giản
            * email: chỉ cho phép nhập địa chỉ email
            * number: chỉ cho phép nhập số
            * url: chỉ cho phép nhập dạng đường dẫn url
            * required: check trống
            * minlength, maxlength, min, max: quy định số từ nhập vào
            * pattern: 
        + Thuộc tính HTML
            * action: định nghĩa các hành động được thực hiện khi biểu mẫu được gửi
            * targetquy: để hiển thị câu trả lời đó là nhận được sau khi nộp mẫu đơn.
        
5. Tái sử dụng Code và cách viết Function 
    - Include File 
        + Require : Dùng để import một file PHP khác vào file hiện tại, lúc này file hiện tại có thể sử dụng mọi tài nguyên của file import đó
        + Require_once : giống require nhưng chỉ import 1 lần
        + Khác nhau giữa require và include: nếu chương trình bị lỗi thì lập tức trình biên dịch sẽ dừng và xuất ra thông báo lỗi. Còn include thì đó chỉ là một cảnh báo nên chương trình vẫn chạy cho đến cuối chương trình.
    - Function
        + function là một khối chứa các câu lệnh sử dụng lại nhiều lần
        + Gọi function : nameFunction()
        + Cách gọi function thông qua tên của 1 biến số : nameFunction($name)
        + Giá trị mặc định : nameFunction($name='giá trị truyền vào')
        + Phạm vi của biến số sử dụng trong hàm, ngoài hàm phải khai báo $global
        + Tham trị: tác động và thay đổi nó ở bên trong hàm thì khi kết thúc hàm biến đó lại trở về vị trí ban đầu.
            * Khai báo function nameFunction($a)
        + Tham chiếu: nếu như một biến được tham chiếu bởi một biến khác thì khi biến này thay đổi biến kia cũng thay đổi theo.
            * Khai báo function nameFunction(&$a)
    - Function __construct(): là hàm khởi tạo sẽ được chạy đầu tiên. các hàm khác có thể sử dụng các thuộc tính của hàm construct