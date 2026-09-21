# Xác thực và đăng nhập

## Mục tiêu

Tài liệu này mô tả cách xác thực người dùng trong CAB System theo SRS. Hệ thống hỗ trợ đăng ký và đăng nhập cho khách hàng, tài xế và nhân viên vận hành dựa trên tài khoản chung.

## Quy tắc nghiệp vụ

- Mỗi người dùng phải có tài khoản để truy cập hệ thống.
- Hệ thống xác thực bằng JWT Bearer token.
- Tài khoản có vai trò theo người dùng: khách hàng, tài xế hoặc nhân viên vận hành.
- Người dùng chỉ được phép truy cập dữ liệu phù hợp với vai trò và quyền của mình.

## API liên quan

- `POST /api/v1/auth/register`
- `POST /api/v1/auth/login`

## Lưu ý

- SRS không mô tả chi tiết về refresh token, expiry policy hay password reset. Những phần này cần bổ sung trước khi triển khai production.
- Đánh dấu [NEED CLARIFICATION] cho các trường này.
