# Quy ước API

## 1. Chuẩn endpoint

- Sử dụng RESTful API.
- Tất cả endpoint bắt đầu bằng `/api/v1`.
- Dùng danh từ cho resource.
- Dùng path parameter cho resource identifier.
- Dùng query parameter cho filter, sort, pagination.

## 2. Chuẩn response

- Trả về JSON.
- Sử dụng HTTP status code chuẩn.
- Mỗi lỗi trả về `ErrorResponse`.

## 3. Quy ước naming

- Endpoint: tiếng Anh, theo dạng resource noun.
- Field JSON: tiếng Anh.
- Description: ưu tiên tiếng Việt.

## 4. Validation

- Kiểm tra hợp lệ đầu vào trước khi xử lý nghiệp vụ.
- Trạng thái thanh toán và chuyến đi phải được phân biệt rõ trong business rule.

## 5. Lưu ý

- SRS không quy định đầy đủ phép tính cước, thời hạn hủy chuyến, timeout nhận chuyến và default pagination. Các thông tin này cần được bổ sung từ BA/Owner.
