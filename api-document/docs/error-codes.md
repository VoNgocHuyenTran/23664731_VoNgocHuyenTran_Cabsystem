# Mã lỗi và xử lý lỗi

## Mã lỗi chung

- `INVALID_REQUEST`: dữ liệu đầu vào không hợp lệ.
- `UNAUTHORIZED`: chưa xác thực hoặc token hết hạn.
- `FORBIDDEN`: người dùng không có quyền thao tác.
- `NOT_FOUND`: dữ liệu không tồn tại.
- `CONFLICT`: trạng thái nghiệp vụ xung đột.
- `INTERNAL_SERVER_ERROR`: lỗi hệ thống.

## Quy ước

- Tất cả lỗi sẽ trả về JSON theo schema `ErrorResponse`.
- `details` dùng để mô tả chi tiết lỗi validation hoặc nghiệp vụ.
- `traceId` hỗ trợ theo dõi log khi mở đường xử lý lỗi.

## Lưu ý

- SRS không định nghĩa danh sách lỗi nghiệp vụ cụ thể cho từng trường hợp hủy chuyến, từ chối nhận chuyến hoặc thanh toán thất bại. Do đó, mã lỗi chi tiết cần bổ sung trong thiết kế triển khai.
- Đánh dấu [NEED CLARIFICATION].
