# Giới thiệu
> Viết ứng dụng cùng Sapo
Bạn là nhà phát triển đang có nhu cầu viết ứng dụng cho Sapo?
Sapo API cho phép thiết lập phần lớn tính năng từ các ứng dụng của bạn trên nền tảng CMS. Web app hoặc các phần mềm từ bên thứ 3 tương thích với nền tảng của Sapo. 
Sapo Embedded App SDK sẽ giúp bạn tạo ra những sản phẩm gần gũi với khách hàng hơn khi được trở thành những Admin của chính ứng dụng của mình.
Bạn có thể dễ dàng bắt đầu với Sapo API. Sapo đem đến cho bạn những hướng dẫn chi tiết để bắt đầu xây dựng ứng dụng, cùng với đó là những lưu ý cần nhớ khi bạn gặp các vấn đề khó khăn, cùng với đó là API Reference để tìm hiểu chính xác những gì bạn có thể thực hiện với API.

# Cấu hình chung
## Môi trường
* URL môi trường thật, production: https://www.sapo.vn/
## Xác thực tài khoản
Sau khi đối tác đăng ký và kích hoạt tài khoản trên hệ thống của Sapo, tài khoản đối tác sẽ được nhận được một chuỗi API token thông qua email.
> Tất cả các request đến API service của Sapo sẽ được xác thực theo giá trị `Token` trong header của request.
## Request Format
Sapo hỗ trợ định dạng dữ liệu mặc định `Content-Type` `application/json`. 
## Response Format 
Kết quả trả về sẽ có 3 định dạng:
* Xác thực không thành công, hay token không hợp lệ
* Request thành công và không có lỗi xảy ra, kết quả trả về ở dạng JSON
* Request thành công và có lỗi xảy ra, kết quả trả về ở dạng JSON
## Webhooks
Một Webhook là một công cụ để truy vấn và lưu trữ dữ liệu của một Event xác định. Bạn có thể đăng ký đường dẫn http:// hoặc https:// - nơi mà dữ liệu của Event được lưu trữ dưới dạng XML hoặc JSON. Webhook có thể được đăng ký cho các Event sau

| Chức năng| Method |
| ------------- |:-------------|
| App	| installed |
| Product |	create/update/delete |
| Order |	create/update/cancelled/delete/active/finalized/invoiced/partial_invoiced/fulfilled/partial_fulfilled/paid/partial_paid |
| Order | Transaction	create |
| Customer | create/delete/update |
| Order Return | create/update/cancelled/returned/partial_refund/refund |
| Inventory |	update |
### Bạn có thể làm gì với Webhook?
Sapo API cho phép bạn thực hiện các thao tác sau với tài nguyên Product. Các phiên bản chi tiết hơn của những thao tác này có thể có
[GET /admin/webhooks.json]
Lấy danh sách tất cả các Webhook
[GET /admin/webhooks/#{id}.json]
Lấy một Webhook
[POST /admin/webhooks.json]
Tạo mới một Webhook
[PUT /admin/webhooks/#{id}.json]
Cập nhật một Webhook

### Các thuộc tính của Webhook
|  |  |
| ------------- |:-------------|
| address | { "address" : "http://whatever.hostname.com/" } . Địa chỉ URI mà Webhook sẽ gửi một POST Request đến khi có Event xảy ra. |
| created_on | { "created_on" : "2012-09-28T11:50:07-04:00" } Thời gian Webhook được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601. |
| format | { "format" : "json" } . Định dạng kiểu dữ liệu mà Webhook trả về. Các giá trị hợp lệ là json và xml. |
| id | { "id" : 4759306 } . Số duy nhất định danh Webhook. |
| topic | { "topic" : "orders/create" } . Event mà khi xảy ra sẽ thực hiện lời gọi Webhook. Các giá trị hợp lệ là: products/create, products/delete, products/update, orders/create, orders/update, orders/cancelled, orders/delete, orders/active, orders/finalized, orders/invoiced, orders/partial_invoiced, orders/fulfilled, orders/partial_fulfilled, orders/paid, orders/partial_paid, customers/create, customers/update, customers/delete, suppliers/create, suppliers/update, suppliers/delete, order_returns/create, order_returns/update, order_returns/cancelled, order_returns/returned, order_returns/partial_refund, order_returns/refund, inventories/update |
| modified_on | { "modified_on" : "2012-09-28T11:50:07-04:00" } . Thời gian Webhook được cập nhật. API trả về kết quả theo định dạng chuẩn ISO 8601. |


# Đơn hàng
## Đơn hàng mới
Đối tác gửi danh sách đơn hàng sang hệ thống của Sapo thông qua APIs. Sau khi các đơn hàng được lưu thành công vào hệ thống của Sapo, hệ thống sẽ trả về danh sách đơn hàng tương ứng chứa các thông tin liên quan của mỗi đơn hàng.
### Các tham số 
| Tham số| Bắt buộc | Mô tả |
| ------------- |:-------------:| -----:|


