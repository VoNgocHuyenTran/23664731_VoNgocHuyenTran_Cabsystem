# B1. Ngữ cảnh nghiệp vụ và vấn đề nghiệp vụ

## 1. Ngữ cảnh nghiệp vụ

Công ty ABC cung cấp dịch vụ **đặt xe trực tuyến**. Hệ thống hiện tại cho phép khách hàng đặt xe qua tổng đài hoặc ứng dụng đơn giản nhưng còn nhiều hạn chế.

**Các bên sử dụng chính:**

* Khách hàng
* Tài xế
* Nhân viên vận hành

**Quy trình chính:**

`Đặt xe → Tìm tài xế → Nhận chuyến → Thực hiện chuyến → Tính cước → Thanh toán → Đánh giá`

## 2. Vấn đề nghiệp vụ

* Phân công tài xế chủ yếu **thủ công**, mất thời gian và khó mở rộng.
* Khách hàng **khó theo dõi trạng thái chuyến đi** và vị trí tài xế.
* Thông tin **thanh toán chưa được quản lý tập trung**.
* Nhân viên vận hành **khó giám sát và xử lý sự cố**.
* Hệ thống cũ **khó mở rộng** khi số lượng khách hàng, tài xế và chuyến đi tăng.
* Thiếu dữ liệu và báo cáo để **hỗ trợ quản lý, ra quyết định**.

## 3. Khách hàng muốn giải quyết

* Tự động hóa việc **tìm và phân công tài xế**.
* Cho khách hàng **theo dõi chuyến đi**.
* Quản lý **tính cước và thanh toán tập trung**.
* Hỗ trợ nhân viên **quản lý khách hàng, tài xế, phương tiện và chuyến đi**.
* Xây dựng nền tảng **có khả năng mở rộng và phát triển lâu dài**.

## 4. Mục tiêu kinh doanh

* **Tăng hiệu quả vận hành**.
* **Cải thiện trải nghiệm khách hàng**.
* **Giảm thời gian và công việc thủ công**.
* **Giảm tỷ lệ chuyến hủy/thất bại**.
* **Tăng khả năng kiểm soát hoạt động**.
* **Hỗ trợ ra quyết định bằng dữ liệu**.
* Có khả năng **mở rộng quy mô và bổ sung dịch vụ mới**.

## 5. Giá trị hệ thống mới so với hệ thống cũ

| Hệ thống cũ               | Hệ thống CAB mới           | Giá trị                       |
| ------------------------- | -------------------------- | ----------------------------- |
| Phân công tài xế thủ công | Tự động tìm tài xế         | Tiết kiệm thời gian           |
| Khó theo dõi chuyến       | Theo dõi trạng thái chuyến | Tăng trải nghiệm              |
| Thanh toán chưa tập trung | Quản lý thanh toán         | Dễ kiểm soát giao dịch        |
| Khó xử lý tài xế từ chối  | Tự động tìm tài xế khác    | Giảm thất bại                 |
| Khó giám sát              | Giao diện vận hành         | Tăng hiệu quả quản lý         |
| Báo cáo hạn chế           | Báo cáo hoạt động          | Hỗ trợ ra quyết định          |
| Khó mở rộng               | Kiến trúc linh hoạt        | Dễ phát triển trong tương lai |

## 6. Tóm tắt

> **Vấn đề:** Hệ thống cũ còn thủ công, khó theo dõi, khó quản lý và khó mở rộng.
> **Nhu cầu:** Tự động hóa quy trình đặt xe và quản lý tập trung.
> **Mục tiêu:** Tăng hiệu quả vận hành, cải thiện trải nghiệm khách hàng và hỗ trợ tăng trưởng.
> **Giá trị:** Tiết kiệm thời gian, giảm sai sót/thất bại, tăng khả năng kiểm soát và tạo nền tảng linh hoạt cho tương lai.
> 
# B2. Xác định các bên liên quan

## 1. Danh sách các bên liên quan

| Bên liên quan                    | Vai trò                                                                              |
| -------------------------------- | ------------------------------------------------------------------------------------ |
| **Ban giám đốc Công ty ABC**     | Định hướng, xác định mục tiêu kinh doanh, phê duyệt dự án và theo dõi kết quả        |
| **Nhân viên vận hành**           | Quản lý khách hàng, tài xế, phương tiện, chuyến đi và xử lý các trường hợp phát sinh |
| **Khách hàng**                   | Đăng ký, đặt xe, theo dõi chuyến, thanh toán và đánh giá tài xế                      |
| **Tài xế**                       | Nhận chuyến, thực hiện chuyến, cập nhật trạng thái và thông tin vị trí               |
| **Nhà cung cấp thanh toán**      | Cung cấp dịch vụ thanh toán điện tử và xử lý giao dịch                               |
| **Nhà cung cấp thông báo**       | Cung cấp dịch vụ gửi thông báo đến khách hàng và tài xế                              |
| **Business Analyst (BA)**        | Thu thập, phân tích và làm rõ yêu cầu với các bên liên quan                          |
| **Đội phát triển hệ thống**      | Thiết kế, xây dựng, kiểm thử và triển khai hệ thống                                  |
| **Bộ phận IT/Quản trị hệ thống** | Quản lý hạ tầng, bảo mật, vận hành và đảm bảo hệ thống hoạt động ổn định             |

---

## 2. Ma trận Stakeholder
                    MỨC ĐỘ QUAN TÂM
                 Thấp                 Cao
              ┌─────────────────┬─────────────────────┐
              │                 │                     │
  CAO         │ GIỮ HÀI LÒNG   │ QUẢN LÝ CHẶT CHẼ   │
              │                 │                     │
ẢNH HƯỞNG     │ - Nhà cung cấp  │ - Ban giám đốc      │
              │   thanh toán    │ - Nhân viên vận hành│
              │ - Nhà cung cấp  │ - BA                │
              │   thông báo     │ - Đội phát triển    │
              │                 │ - IT                │
              ├─────────────────┼─────────────────────┤
              │                 │                     │
  THẤP        │ THEO DÕI       │ GIỮ THÔNG TIN       │
              │                 │                     │
              │ - Bên hỗ trợ    │ - Khách hàng        │
              │   gián tiếp     │ - Tài xế             │
              │                 │                     │
              └─────────────────┴─────────────────────┘
---

## 3. Mức độ ảnh hưởng của các bên liên quan

| Bên liên quan           | Mức độ ảnh hưởng | Mức độ quan tâm |
| ----------------------- | ---------------- | --------------- |
| Ban giám đốc            | **Cao**          | **Cao**         |
| Nhân viên vận hành      | **Cao**          | **Cao**         |
| Khách hàng              | **Thấp**         | **Cao**         |
| Tài xế                  | **Thấp**         | **Cao**         |
| Nhà cung cấp thanh toán | **Cao**          | **Thấp**        |
| Nhà cung cấp thông báo  | **Cao**          | **Thấp**        |
| BA                      | **Cao**          | **Cao**         |
| Đội phát triển          | **Cao**          | **Cao**         |
| IT/Quản trị hệ thống    | **Cao**          | **Cao**         |

## 4. Kết luận

* **Ảnh hưởng cao + Quan tâm cao:** cần **quản lý chặt chẽ**.
* **Ảnh hưởng cao + Quan tâm thấp:** cần **giữ hài lòng**.
* **Ảnh hưởng thấp + Quan tâm cao:** cần **cung cấp thông tin và thu thập phản hồi**.
* **Ảnh hưởng thấp + Quan tâm thấp:** chỉ cần **theo dõi**.

**Stakeholder quan trọng nhất:** Ban giám đốc và nhân viên vận hành vì có ảnh hưởng và mức độ quan tâm cao đối với hệ thống.
# Quy trình nghiệp vụ

| Mã BC    | Quy trình nghiệp vụ                 | Mục tiêu                                                                                                                 |
| -------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **BC01** | **Hỗ trợ thanh toán**               | Hỗ trợ khách hàng thanh toán bằng tiền mặt hoặc điện tử, xử lý kết quả giao dịch và thanh toán thất bại                  |
| **BC02** | **Giảm thời gian tìm tài xế**       | Tự động tìm tài xế phù hợp, ưu tiên tài xế gần khách hàng và tiếp tục tìm tài xế khác nếu bị từ chối hoặc không phản hồi |
| **BC03** | **Hỗ trợ đặt xe**                   | Cho phép khách hàng nhập điểm đón, điểm đến, chọn loại xe và gửi yêu cầu đặt xe                                          |
| **BC04** | **Theo dõi chuyến đi**              | Cho phép khách hàng theo dõi tài xế, thời gian dự kiến đến và trạng thái chuyến                                          |
| **BC05** | **Quản lý và thực hiện chuyến**     | Cho phép tài xế nhận/từ chối chuyến và cập nhật trạng thái từ khi đến điểm đón đến khi hoàn thành                        |
| **BC06** | **Quản lý tài xế và phương tiện**   | Quản lý hồ sơ tài xế, thông tin phương tiện và trạng thái hoạt động                                                      |
| **BC07** | **Hỗ trợ thông báo**                | Gửi thông báo cho khách hàng và tài xế về yêu cầu đặt xe, nhận chuyến, trạng thái chuyến và thanh toán                   |
| **BC08** | **Hỗ trợ vận hành**                 | Cho phép nhân viên quản lý khách hàng, tài xế, phương tiện, chuyến đi và xử lý các trường hợp phát sinh                  |
| **BC09** | **Báo cáo và thống kê**             | Cung cấp báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế                                 |
| **BC10** | **Quản lý tài khoản và phân quyền** | Xác thực người dùng và kiểm soát quyền truy cập các chức năng                                                            |
| **BC11** | **Đánh giá tài xế**                 | Cho phép khách hàng đánh giá tài xế sau khi hoàn thành chuyến                                                            |
| **BC12** | **Quản lý lịch sử chuyến đi**       | Cho phép tra cứu lịch sử chuyến đi, số tiền thanh toán và giao dịch                                                      |

## Các quy trình nghiệp vụ chính

### BC01 – Hỗ trợ thanh toán

Khách hàng thanh toán sau khi chuyến đi hoàn thành. Hệ thống tính cước, hỗ trợ thanh toán tiền mặt hoặc điện tử, tích hợp với nhà cung cấp thanh toán bên ngoài và thông báo kết quả giao dịch.

### BC02 – Giảm thời gian tìm tài xế

Khi khách hàng đặt xe, hệ thống tự động tìm tài xế phù hợp dựa trên **vị trí, trạng thái sẵn sàng và các tiêu chí vận hành**. Hệ thống ưu tiên tài xế phù hợp và gần khách hàng. Nếu tài xế từ chối hoặc không phản hồi, hệ thống tiếp tục tìm tài xế khác mà khách hàng không cần tạo lại yêu cầu.

### BC03 – Hỗ trợ đặt xe

Khách hàng nhập **điểm đón, điểm đến, loại xe** và gửi yêu cầu đặt xe. Hệ thống tiếp nhận và bắt đầu quá trình tìm tài xế.

### BC04 – Theo dõi chuyến đi

Khách hàng theo dõi **tài xế, vị trí, thời gian dự kiến đến và trạng thái chuyến đi** từ lúc đặt xe đến khi hoàn thành.

### BC05 – Quản lý và thực hiện chuyến

Tài xế nhận hoặc từ chối chuyến, sau đó cập nhật các trạng thái:

`Đã nhận → Đã đến điểm đón → Đã đón khách → Đang di chuyển → Hoàn thành`

### BC06 – Quản lý tài xế và phương tiện

Nhân viên vận hành quản lý **tài khoản, hồ sơ, phương tiện và trạng thái hoạt động** của tài xế.

### BC07 – Hỗ trợ thông báo

Hệ thống gửi thông báo khi:

* Yêu cầu đặt xe được tiếp nhận.
* Tài xế nhận chuyến.
* Tài xế đến điểm đón.
* Chuyến đi hoàn thành.
* Thanh toán có kết quả.
* Có chuyến mới hoặc thay đổi liên quan đến chuyến.

### BC08 – Hỗ trợ vận hành

Nhân viên vận hành quản lý **khách hàng, tài xế, phương tiện và chuyến đi**, đồng thời hỗ trợ xử lý các chuyến bị lỗi hoặc các trường hợp phát sinh.

### BC09 – Báo cáo và thống kê

Hệ thống cung cấp báo cáo về:

* Số lượng chuyến.
* Doanh thu.
* Tỷ lệ chuyến hoàn thành.
* Tỷ lệ chuyến hủy.
* Hiệu quả hoạt động của tài xế.

### BC10 – Quản lý tài khoản và phân quyền

Hệ thống hỗ trợ **đăng ký, đăng nhập, xác thực và phân quyền**, đảm bảo người dùng chỉ được thực hiện các chức năng phù hợp với vai trò.

### BC11 – Đánh giá tài xế

Sau khi chuyến hoàn thành, khách hàng có thể **đánh giá tài xế** dựa trên trải nghiệm chuyến đi.

### BC12 – Quản lý lịch sử chuyến đi

Khách hàng và nhân viên có thể **tra cứu lịch sử chuyến đi, số tiền phải trả và thông tin giao dịch**.

