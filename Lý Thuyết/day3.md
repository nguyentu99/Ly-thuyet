## Lý thuyết ngày 3
1. Database
    - SQL cơ bản
        + SELECT : Lấy dữ liệu từ database
            * SELECT column1, column2, ... FROM table_name;
            * SELECT DISTINCT : lấy và loại bỏ các bản ghi trùng nhau từ database
        + INSERT : Thêm 1 bản ghi mới vào bảng
            * INSERT INTO table_name (column1, column2, column3, ...) VALUES (value1, value2, value3, ...);
        + UPDATE : Thay đổi dữ liệu của bản ghi trong bảng
            * UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;
        + DELETE : Xóa bản ghi trong bảng 
            * DELETE FROM table_name WHERE condition;
        + Một số lệnh SQL hay dùng
            * LIMIT : xác định số bản ghi trả về
            * LIKE : tìm kiếm thông tin trong bảng
            * JOIN (INNER JOIN, LEFT JOIN, RIGHT JOIN): lấy danh sách bản ghi tùy vào thuộc tính 
            * ORDER BY: Sắp xếp số bản ghi theo thuộc tính truyền vào
            * GROUP BY:  nhóm các hàng có cùng giá trị thành các hàng tóm tắt
            * WHERE : sử dụng để chọn lọc
            * COUNT : trả về số cột 
            * AVG :trả về giá trị trung bình của một cột số. 
            * SUM : trả về tổng của một cột số. 
            * HAVING : được thêm vào SQL bởi vì WHEREtừ khóa không thể được sử dụng với chức năng tổng hợp
    - Querying Database 
        + hàm MySQLi cho phép bạn truy cập các máy chủ cơ sở dữ liệu MySQL.
        + Prepared : Một mẫu câu lệnh SQL được tạo và gửi đến cơ sở dữ liệu
        + Cơ sở dữ liệu phân tích cú pháp, biên dịch và thực hiện tối ưu hóa truy vấn trên mẫu câu lệnh SQL và lưu trữ kết quả mà không cần thực thi nó
        + Execute : Liên kết các giá trị với các tham số và cơ sở dữ liệu thực thi câu lệnh.
        + bind_param: Liên kết các biến với một câu lệnh đã chuẩn bị dưới dạng tham số.