## Botble
# Tài khoản admin
    - Username: botble
    - Password: 159357
    - tạo tài khoản admin mới: php artisan cms:user:create

# Plugin
1. Lệnh
    - create plugin: php artisan cms:plugin:create <plugin name>
    - activate plugin: php artisan cms:plugin:activate <plugin name>
    - deactive plugin: php artisan cms:plugin:deactivate <plugin name>
    - romove plugin: php artisan cms:plugin:remove demo
2. Cấu trúc
    - plugin.json chứa thông tin về plugin
    - route, src, resoures, database giống laravel
    - Plugin xử lý sự kiện cho plugin( activate, remove, deactivate)
    
3. viết
    - Chạy migrate
        + migrate trong plugin: php artisan make:migration nameTable --path=đường đẫn (đường dẫn tương đối từ platform)
        + sửa Model theo table vừa migrate
        + add field từ form hiển thị ra
        + 
# Theme
1. Lệnh
    - create theme: php artisan cms:theme:create demo
    - remove theme: php artisan cms:theme:remove demo
2. Cắt layout
    - Trả về theme return Theme->scope('home.index', $view)->render();
    - Chỉ nhận phần nội dung Theme->of ('home.index') -> content ();
    - add css,js.. Theme::asset()->url('img/image.png'); (nó nhận ở public ngoài cùng)
