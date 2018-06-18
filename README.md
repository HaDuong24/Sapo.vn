# Cấu hình chung
## Môi trường
* URL môi trường thật, production: https://www.sapo.vn/
## Xác thực tài khoản
Sau khi đối tác đăng ký và kích hoạt tài khoản trên hệ thống của Sapo, tài khoản đối tác sẽ được nhận được một chuỗi API token thông qua email.
> Tất cả các request đến API service của Sapo sẽ được xác thực theo giá trị `Token` trong header của request.
