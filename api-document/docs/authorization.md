# Phân quyền trong hệ thống

## Vai trò

Theo SRS, hệ thống có các actor chính sau:

- Khách hàng
- Tài xế
- Nhân viên vận hành
- Ban giám đốc

## Quy tắc phân quyền

- Khách hàng chỉ có thể xem và cập nhật hồ sơ cá nhân, xem lịch sử chuyến đi, thanh toán và đánh giá tài xế.
- Tài xế chỉ có thể quản lý hồ sơ cá nhân, cập nhật vị trí, nhận/từ chối chuyến và cập nhật trạng thái chuyến.
- Nhân viên vận hành có quyền quản lý khách hàng, tài xế, phương tiện, chuyến đi và xử lý sự cố.
- Ban giám đốc có quyền xem báo cáo và thống kê.

## Mức độ xác thực

- Tất cả API thuộc phạm vi người dùng đều sử dụng `bearerAuth`.
- API không cần xác thực chỉ dành cho đăng ký và đăng nhập.

## Lưu ý

- SRS chưa mô tả danh sách quyền chi tiết từng màn hình hoặc từng endpoint. Do đó, mô hình phân quyền hiện tại là mức khung chung và cần bổ sung chi tiết trước triển khai hệ thống lớn.
- Đánh dấu [NEED CLARIFICATION].
