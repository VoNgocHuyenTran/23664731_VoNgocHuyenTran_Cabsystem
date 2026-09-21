# Tài liệu thiết kế API CAB System

## 1. Bảng mapping Domain → Use Case → API

| Domain | Use Case | Operation | Method | Endpoint | Auth |
| ------ | -------- | --------- | ------ | -------- | ---- |
| Authentication | Đăng ký tài khoản | Tạo tài khoản khách hàng | POST | /auth/register | Không |
| Authentication | Đăng nhập | Xác thực người dùng | POST | /auth/login | Không |
| Customer Management | Quản lý khách hàng | Lấy hồ sơ cá nhân | GET | /customers/me | JWT |
| Customer Management | Quản lý khách hàng | Cập nhật hồ sơ cá nhân | PATCH | /customers/me | JWT |
| Customer Management | Lịch sử chuyến đi | Lấy lịch sử chuyến | GET | /customers/me/trips | JWT |
| Driver Management | Quản lý tài xế | Lấy hồ sơ tài xế | GET | /drivers/me | JWT |
| Driver Management | Quản lý tài xế | Cập nhật hồ sơ tài xế | PATCH | /drivers/me | JWT |
| Driver Management | Quản lý tài xế | Cập nhật trạng thái sẵn sàng | PATCH | /drivers/me/availability | JWT |
| Driver Management | Theo dõi vị trí | Cập nhật vị trí hiện tại | PATCH | /drivers/me/location | JWT |
| Trip Management | Đặt chuyến | Tạo yêu cầu đặt xe | POST | /trips | JWT |
| Trip Management | Tìm tài xế | Lấy thông tin chuyến theo ID | GET | /trips/{tripId} | JWT |
| Trip Management | Tìm tài xế | Xác nhận nhận chuyến | POST | /trips/{tripId}/accept | JWT |
| Trip Management | Tìm tài xế | Từ chối chuyến | POST | /trips/{tripId}/reject | JWT |
| Trip Management | Quản lý chuyến đi | Cập nhật trạng thái chuyến | PATCH | /trips/{tripId}/status | JWT |
| Trip Management | Theo dõi chuyến đi | Lấy theo dõi chuyến | GET | /trips/{tripId}/tracking | JWT |
| Trip Management | Thanh toán | Tạo giao dịch thanh toán | POST | /trips/{tripId}/payments | JWT |
| Trip Management | Đánh giá tài xế | Tạo đánh giá | POST | /trips/{tripId}/ratings | JWT |
| Report Management | Báo cáo | Lấy báo cáo tổng hợp | GET | /reports/summary | JWT |

## 2. Tổng quan thiết kế API

Các API được xác định từ SRS tập trung vào các miền nghiệp vụ chủ đạo sau:

- Authentication
- Customer Management
- Driver Management
- Trip Management
- Payment & Billing
- Reporting
- Notification (không thiết kế API riêng nếu SRS không mô tả endpoint rõ ràng; chỉ phản ánh qua thông báo trong luồng nghiệp vụ)

Các API dưới đây xuất phát trực tiếp từ:

- BR-01 đến BR-15
- FR-01 đến FR-70
- BC02, BC03, BC04, BC05, BC06, BC07, BC08, BC09, BC10, BC11, BC12
- Quy tắc nghiệp vụ BRULE-01 đến BRULE-06

## 3. Mapping Requirement → API

### 3.1. BR-01 – Đặt chuyến
- Yêu cầu: khách hàng nhập điểm đón, điểm đến, loại xe, gửi yêu cầu đặt xe.
- Business Operation: tạo yêu cầu đặt chuyến.
- API: `POST /api/v1/trips`

### 3.2. BR-02 – Tìm tài xế
- Yêu cầu: hệ thống tự động tìm tài xế phù hợp theo vị trí, trạng thái sẵn sàng, loại xe.
- Business Operation: nhận thông tin chuyến, tìm tài xế phù hợp, gửi yêu cầu nhận chuyến, tiếp tục tìm người khác nếu từ chối hoặc không phản hồi.
- API liên quan: `GET /api/v1/trips/{tripId}`, `POST /api/v1/trips/{tripId}/accept`, `POST /api/v1/trips/{tripId}/reject`.

### 3.3. BR-03 – Theo dõi chuyến đi
- Yêu cầu: khách hàng theo dõi vị trí tài xế, trạng thái và thời gian dự kiến.
- Business Operation: lấy thông tin vị trí và trạng thái chuyến.
- API: `GET /api/v1/trips/{tripId}/tracking`

### 3.4. BR-04 – Quản lý tài xế
- Yêu cầu: nhân viên vận hành quản lý hồ sơ, phương tiện, trạng thái hoạt động.
- Business Operation: xem/cập nhật hồ sơ tài xế và cập nhật trạng thái hoạt động.
- API: `GET /api/v1/drivers/me`, `PATCH /api/v1/drivers/me`, `PATCH /api/v1/drivers/me/availability`

### 3.5. BR-05 – Quản lý chuyến đi
- Yêu cầu: tài xế nhận/từ chối chuyến và cập nhật trạng thái từ khi đến điểm đón đến khi hoàn thành.
- Business Operation: nhận chuyến, từ chối chuyến, cập nhật trạng thái.
- API: `POST /api/v1/trips/{tripId}/accept`, `POST /api/v1/trips/{tripId}/reject`, `PATCH /api/v1/trips/{tripId}/status`

### 3.6. BR-06 – Thanh toán
- Yêu cầu: khách hàng thanh toán sau khi hoàn thành chuyến bằng tiền mặt hoặc điện tử.
- Business Operation: tạo giao dịch thanh toán và ghi nhận trạng thái.
- API: `POST /api/v1/trips/{tripId}/payments`

### 3.7. BR-07 – Tính cước
- Yêu cầu: xác định số tiền dựa trên loại dịch vụ và thông tin chuyến đi.
- Business Operation: xác định và lưu thông tin cước.
- API được phản ánh trong payload của `POST /api/v1/trips` và `POST /api/v1/trips/{tripId}/payments`.

### 3.8. BR-08 – Thông báo
- Yêu cầu: hệ thống gửi thông báo cho khách hàng/tài xế khi có sự kiện liên quan đến chuyến.
- Business Operation: phát thông báo.
- SRS không mô tả endpoint cụ thể cho hệ thống thông báo. Vì vậy, API notification được coi là công việc tích hợp ngoại vi và không được tạo endpoint độc lập nếu không xác định rõ. 
- Ký hiệu: [NEED CLARIFICATION]

### 3.9. BR-09 – Quản lý khách hàng
- Yêu cầu: đăng ký, đăng nhập, cập nhật thông tin cá nhân, tra cứu tài khoản.
- API: `POST /auth/register`, `POST /auth/login`, `GET /customers/me`, `PATCH /customers/me`

### 3.10. BR-10 – Quản lý vận hành
- Yêu cầu: nhân viên quản lý khách hàng, tài xế, phương tiện, chuyến đi, xử lý sự cố.
- Business Operation: tra cứu và cập nhật dữ liệu hệ thống.
- API được mô tả thông qua `GET/PATCH` trên khách hàng, tài xế, chuyến đi và báo cáo.

### 3.11. BR-11 – Báo cáo
- Yêu cầu: báo cáo số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy, hiệu quả tài xế.
- Business Operation: xem báo cáo tổng hợp.
- API: `GET /reports/summary`

### 3.12. BR-12 – Đánh giá tài xế
- Yêu cầu: khách hàng đánh giá tài xế sau khi hoàn thành chuyến.
- API: `POST /trips/{tripId}/ratings`

### 3.13. BR-13 – Phân quyền
- Yêu cầu: xác thực người dùng và kiểm soát quyền truy cập chức năng theo vai trò.
- Business Operation: xác thực và kiểm tra phân quyền.
- API: security scheme `bearerAuth`, và role-based access được mô tả ở `Authorization` của từng endpoint.

### 3.14. BR-14 – Lịch sử chuyến đi
- Yêu cầu: tra cứu lịch sử từng chuyến và thông tin giao dịch.
- API: `GET /customers/me/trips`, `GET /trips/{tripId}`

### 3.15. BR-15 – Mở rộng hệ thống
- Yêu cầu: cho phép bổ sung loại dịch vụ, phương thức thanh toán và kênh thông báo.
- SRS chưa mô tả các cấu hình cụ thể. Do đó, các endpoint cấu hình mở rộng không được tạo thêm ngoài phạm vi này.
- Ký hiệu: [NEED CLARIFICATION]

## 4. API Contract

### 4.1. Endpoint chính

- `POST /api/v1/auth/register`
- `POST /api/v1/auth/login`
- `GET /api/v1/customers/me`
- `PATCH /api/v1/customers/me`
- `GET /api/v1/customers/me/trips`
- `GET /api/v1/drivers/me`
- `PATCH /api/v1/drivers/me`
- `PATCH /api/v1/drivers/me/availability`
- `PATCH /api/v1/drivers/me/location`
- `POST /api/v1/trips`
- `GET /api/v1/trips/{tripId}`
- `POST /api/v1/trips/{tripId}/accept`
- `POST /api/v1/trips/{tripId}/reject`
- `PATCH /api/v1/trips/{tripId}/status`
- `GET /api/v1/trips/{tripId}/tracking`
- `POST /api/v1/trips/{tripId}/payments`
- `POST /api/v1/trips/{tripId}/ratings`
- `GET /api/v1/reports/summary`

### 4.2. Chuẩn xác thực và phân quyền

- Authentication: JWT Bearer
- Authorization theo vai trò: `customer`, `driver`, `operator`, `admin`
- Quy tắc ưu tiên: người dùng chỉ truy cập dữ liệu thuộc quyền của mình, trừ nhân viên vận hành có thể xem/điều hành dữ liệu đối tượng liên quan.

## 5. Schema Design

### 5.1. Request Schema
- `RegisterRequest`
- `LoginRequest`
- `CustomerUpdateRequest`
- `DriverUpdateRequest`
- `TripCreateRequest`
- `TripStatusUpdateRequest`
- `PaymentRequest`
- `RatingRequest`

### 5.2. Response Schema
- `AuthTokenResponse`
- `CustomerResponse`
- `DriverResponse`
- `TripResponse`
- `TrackingResponse`
- `PaymentResponse`
- `ReportSummaryResponse`
- `ErrorResponse`

### 5.3. Entity Schema
- `Customer`
- `Driver`
- `Vehicle`
- `Trip`
- `PricingDetail`
- `Payment`
- `Rating`

## 6. Common Components

### 6.1. Parameters
- `tripId`
- `customerId`
- `driverId`
- `page`
- `limit`
- `sort`

### 6.2. Responses
- `400 Bad Request`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `409 Conflict`
- `500 Internal Server Error`

### 6.3. Security
- Bearer JWT

## 7. API Document Structure

```text
api-document/
├── README.md
├── openapi.yaml
├── paths/
│   ├── auth/
│   │   └── auth.yaml
│   ├── customers/
│   │   └── customers.yaml
│   ├── drivers/
│   │   └── drivers.yaml
│   ├── trips/
│   │   └── trips.yaml
│   └── reports/
│       └── reports.yaml
├── schemas/
│   ├── auth/
│   │   └── AuthToken.yaml
│   ├── customer/
│   │   └── Customer.yaml
│   ├── driver/
│   │   └── Driver.yaml
│   ├── trip/
│   │   ├── Trip.yaml
│   │   ├── TripCreateRequest.yaml
│   │   └── TrackingResponse.yaml
│   ├── payment/
│   │   └── Payment.yaml
│   └── common/
│       └── ErrorResponse.yaml
├── parameters/
│   └── common.yaml
├── responses/
│   └── common.yaml
├── security/
│   └── bearerAuth.yaml
├── docs/
│   ├── authentication.md
│   ├── authorization.md
│   ├── error-codes.md
│   └── conventions.md
├── dist/
│   └── openapi.bundle.yaml
└── examples/
    └── sample-data.yaml
```

## 8. [Cần làm rõ]

### Vấn đề 1:
Thông tin đang thiếu: Chính sách tính cước và cách xác định giá cuối cùng không được mô tả chi tiết trong SRS.
API/Use Case bị ảnh hưởng: `POST /api/v1/trips`, `POST /api/v1/trips/{tripId}/payments`, `BR-07`.
Thông tin cần bổ sung: Quy tắc tính cước theo khoảng cách/thời gian/loại xe, phí phụ thu, điều kiện ưu tiên giá, cách áp dụng khuyến mãi.

### Vấn đề 2:
Thông tin đang thiếu: Chính sách hủy chuyến, thời điểm cho phép hủy và phí hủy chưa được thống nhất.
API/Use Case bị ảnh hưởng: `BR-01`, `BR-05`, `POST /api/v1/trips`, `POST /api/v1/trips/{tripId}/reject`.
Thông tin cần bổ sung: Điều kiện hủy, thời hạn cho phép hủy, phí hủy, chính sách cho trường hợp tài xế từ chối hoặc không phản hồi.

### Vấn đề 3:
Thông tin đang thiếu: Chi tiết cấu hình tiêu chí tìm tài xế, ưu tiên theo vị trí, khoảng cách, trạng thái và loại xe chưa được định nghĩa rõ.
API/Use Case bị ảnh hưởng: `BR-02`, tìm tài xế và vòng lặp nhận chuyến.
Thông tin cần bổ sung: Bảng ưu tiên, ngưỡng khoảng cách, mức độ ưu tiên theo loại xe, thời gian chờ phản hồi tối đa.

### Vấn đề 4:
Thông tin đang thiếu: Cấu hình phương thức thanh toán điện tử và xác thực giao dịch với nhà cung cấp thanh toán chưa đủ cụ thể.
API/Use Case bị ảnh hưởng: `BR-06`, `BRULE-04`, `POST /api/v1/trips/{tripId}/payments`.
Thông tin cần bổ sung: Loại payment gateway, mã giao dịch, callback URL, trạng thái giao dịch, retry policy.

### Vấn đề 5:
Thông tin đang thiếu: Hệ thống thông báo liên quan đến nhà cung cấp thông báo chưa xác định rõ giao diện tích hợp.
API/Use Case bị ảnh hưởng: `BR-08`, `BC07`.
Thông tin cần bổ sung: kênh gửi (push/email/SMS), payload thông báo, điều kiện kích hoạt, retry và nhật ký thông báo.

### Vấn đề 6:
Thông tin đang thiếu: Vai trò chi tiết và phân quyền cho từng actor chưa nêu rõ đến mức endpoint và chức năng cụ thể.
API/Use Case bị ảnh hưởng: `BR-13`, `BC10`.
Thông tin cần bổ sung: Danh sách quyền `customer`, `driver`, `operator`, `admin` và phạm vi dữ liệu cho từng vai trò.

## 9. Validation

- API được xây dựng dựa trên SRS, không dựa trên suy đoán database.
- Mọi endpoint đều có nguồn từ use case hoặc business requirement chính xác.
- Các phần chưa đủ thông tin đã được đánh dấu [NEED CLARIFICATION].
- Đặc tả này vẫn cần bổ sung từ BA/Business Owner trước khi triển khai production.

---

> Ghi chú: Tài liệu này tuân thủ nguyên tắc thiết kế API theo business requirement, không tạo CRUD duy nhất dựa trên bảng dữ liệu.
