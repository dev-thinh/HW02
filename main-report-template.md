# HW02 – Domain Testing on EShop

**Student ID:** `23127484`  
**Full name:** `Nguyễn Đặng Đức Thịnh`  
**Course:** `Software Testing`  
**Date:** `[29/06/2026]`

---

## Table of Contents

1. [Feature A – FR-02: Login & Account Lockout](#feature-a)
2. [Feature B – FR-09: Discount Coupons](#feature-b)
3. [Feature C – FR-14: Category Management CRUD](#feature-c)
4. [Feature D – FR-06 Mobile: Product Detail View](#feature-d)

---

# Feature A – FR-02: Login & Account Lockout <a name="feature-a"></a>

## A.1 Feature Overview

Tính năng Đăng nhập và Khóa tài khoản (FR-02) giúp quản lý truy cập người dùng vào EShop. Luồng chính cho phép đăng nhập thành công khi nhập đúng email và password. Luồng ngoại lệ tự động khóa tài khoản tạm thời trong 3 phút nếu sai mật khẩu liên tiếp $\ge 5$ lần (trong SUT thực tế là 3 lần và tăng 2 lần mỗi lần sai) để ngăn chặn các cuộc tấn công brute-force.

**Requirement ID:** FR-02

---

## A.2 Domain Testing

### A.2.1 Step 1 – Variable Identification

Được xác định dựa trên việc quan sát trực tiếp trang Đăng nhập trên Web UI kết hợp với phân tích backend endpoint `/api/login` xử lý đăng nhập và cập nhật trạng thái đếm số lần đăng nhập sai:

| #   | Variable       | Data Type | Valid Domain                                         | Invalid Domain                                                                                      | Constraints                                                                              |
| --- | -------------- | --------- | ---------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| 1   | email          | string    | Đúng định dạng `user@domain.com`, tồn tại trong CSDL | Sai định dạng (không có `@`, để trống, v.v.) hoặc đúng định dạng nhưng **không tồn tại** trong CSDL | Bắt buộc nhập, UI sử dụng ô nhập văn bản thông thường thay vì `email` type               |
| 2   | password       | string    | Mật khẩu đúng, khớp với bản ghi email trong CSDL     | Mật khẩu sai, để trống hoặc `null`                                                                  | Bắt buộc nhập, UI hiển thị dưới dạng văn bản thuần (`text` input)                        |
| 3   | login_attempts | integer   | Từ 0 đến 2 lần đăng nhập thất bại liên tiếp          | Lớn hơn hoặc bằng 3 lần đăng nhập thất bại liên tiếp                                                | Hệ thống tự quản lý (trường trong CSDL), tăng thêm **2** sau mỗi lần đăng nhập thất bại  |
| 4   | locked_until   | datetime  | `null` hoặc thời điểm trong quá khứ (đã hết khóa)    | Thời điểm trong tương lai                                                                           | Hệ thống tự quản lý, khóa tài khoản trong **180 giây (3 phút)** khi `login_attempts ≥ 3` |

**Inter-variable dependencies:**

- Khi `failed_attempts` đạt ngưỡng $\ge 5$ (SUT thực tế là `login_attempts` $\ge 3$), tài khoản tự động bị khóa (chuyển đổi trạng thái khóa).
- Việc đăng nhập thành công yêu cầu email và password khớp nhau và tài khoản không bị khóa.

---

### A.2.2 Step 2 – Equivalence Partitioning

Phân hoạch theo tính đúng đắn định dạng email, sự tồn tại của tài khoản, tính khớp của mật khẩu và trạng thái khóa của tài khoản:

| Class ID    | Variable       | Type    | Description                                         | Representative Value       | Expected Behavior                                                      |
| ----------- | -------------- | ------- | --------------------------------------------------- | -------------------------- | ---------------------------------------------------------------------- |
| EP-EMAIL-01 | email          | VALID   | Đúng định dạng, tồn tại trong CSDL                  | test@eshop.com             | Tiếp tục kiểm tra mật khẩu                                             |
| EP-EMAIL-02 | email          | INVALID | Đúng định dạng nhưng **không tồn tại** trong CSDL   | ghost@eshop.com            | Thất bại – trả về lỗi chung (401)                                      |
| EP-EMAIL-03 | email          | INVALID | Sai định dạng                                       | test_username              | Thất bại – trả về lỗi chung (401)                                      |
| EP-EMAIL-04 | email          | INVALID | Để trống                                            | `""`                       | Thất bại – bị trình duyệt chặn bởi validator `required`                |
| EP-EMAIL-05 | email          | INVALID | Thử tấn công SQL Injection                          | test' OR 1=1 -- @eshop.com | Thất bại – được xử lý an sau hoặc bị từ chối do sai định dạng          |
| EP-PASS-01  | password       | VALID   | Mật khẩu đúng với tài khoản                         | Test1234!                  | Đăng nhập thành công, tạo token                                        |
| EP-PASS-02  | password       | INVALID | Mật khẩu sai                                        | WrongPass123!              | Thất bại – trả về lỗi chung (401), `attempts += 2`                     |
| EP-PASS-03  | password       | INVALID | Để trống                                            | `""`                       | Thất bại – bị trình duyệt chặn bởi validator `required`                |
| EP-PASS-04  | password       | INVALID | Thử tấn công SQL Injection                          | password' OR '1'='1        | Thất bại – được xử lý an toàn, đăng nhập không thành công              |
| EP-ATT-01   | login_attempts | VALID   | Chưa đạt ngưỡng khóa (0, 1, 2)                      | 0                          | Tài khoản hoạt động bình thường, cho phép kiểm tra thông tin đăng nhập |
| EP-ATT-02   | login_attempts | INVALID | Đạt hoặc vượt ngưỡng khóa (≥ 3)                     | 4                          | Kích hoạt khóa tài khoản                                               |
| EP-LOCK-01  | locked_until   | VALID   | Không bị khóa (`null` hoặc thời điểm trong quá khứ) | `null`                     | Cho phép quy trình đăng nhập bình thường                               |
| EP-LOCK-02  | locked_until   | INVALID | Đang bị khóa (thời điểm trong tương lai)            | now + 2 minutes            | Thất bại – trả về thông báo tài khoản bị khóa (403), chặn đăng nhập    |

**Combination classes:**

| Combo ID | Variables                                                      | Description                                                                       | Expected Behavior                                                                                                 |
| -------- | -------------------------------------------------------------- | --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| COMBO-01 | EP-EMAIL-01 + EP-PASS-01 + EP-ATT-01 + EP-LOCK-01              | Đăng nhập thành công với tài khoản đang hoạt động và thông tin xác thực chính xác | Đăng nhập thành công, chuyển đến trang chủ, tạo token                                                             |
| COMBO-02 | EP-EMAIL-01 + EP-PASS-02 + EP-ATT-01 [attempts=0] + EP-LOCK-01 | Nhập sai mật khẩu với tài khoản đang hoạt động (lần đầu)                          | Đăng nhập thất bại (401), `login_attempts` tăng thành 2                                                           |
| COMBO-03 | EP-EMAIL-01 + EP-PASS-02 + EP-ATT-01 [attempts=2] + EP-LOCK-01 | Nhập sai mật khẩu với tài khoản đang hoạt động (lần thứ hai)                      | Đăng nhập thất bại (401), `login_attempts` tăng thành 4, `locked_until` được đặt bằng thời điểm hiện tại + 3 phút |
| COMBO-04 | EP-EMAIL-01 + EP-PASS-01 + EP-ATT-02 + EP-LOCK-02              | Thử đăng nhập bằng thông tin chính xác khi tài khoản đang bị khóa                 | Đăng nhập thất bại (403), hiển thị thông báo tài khoản bị khóa                                                    |
| COMBO-05 | EP-EMAIL-02 + EP-PASS-01 + EP-ATT-01 + EP-LOCK-01              | Email đúng định dạng nhưng không tồn tại trong CSDL, mật khẩu đúng định dạng      | Đăng nhập thất bại (401) ngay lập tức, không thay đổi `login_attempts` trong CSDL                                 |

---

### A.2.3 Test Cases – Domain Testing

Liệt kê tất cả TC files đã tạo trên GitHub. Mỗi dòng link đến file TC trên repo.

| TC ID        | Title                                                     | Class covered | GitHub link                                                    |
| ------------ | --------------------------------------------------------- | ------------- | -------------------------------------------------------------- |
| TC-LOGIN-001 | Đăng nhập thành công với credentials hợp lệ               | COMBO-01      | [TC-LOGIN-001.md](tests/test-cases/fr02-login/TC-LOGIN-001.md) |
| TC-LOGIN-002 | Đăng nhập thất bại với email không tồn tại trong hệ thống | EP-EMAIL-02   | [TC-LOGIN-002.md](tests/test-cases/fr02-login/TC-LOGIN-002.md) |
| TC-LOGIN-003 | Đăng nhập thất bại với email sai định dạng                | EP-EMAIL-03   | [TC-LOGIN-003.md](tests/test-cases/fr02-login/TC-LOGIN-003.md) |
| TC-LOGIN-004 | Đăng nhập thất bại với email để trống                     | EP-EMAIL-04   | [TC-LOGIN-004.md](tests/test-cases/fr02-login/TC-LOGIN-004.md) |
| TC-LOGIN-005 | Đăng nhập thất bại với email chứa ký tự SQL Injection     | EP-EMAIL-05   | [TC-LOGIN-005.md](tests/test-cases/fr02-login/TC-LOGIN-005.md) |
| TC-LOGIN-006 | Đăng nhập thất bại với mật khẩu sai (1st attempt)         | EP-PASS-02    | [TC-LOGIN-006.md](tests/test-cases/fr02-login/TC-LOGIN-006.md) |
| TC-LOGIN-007 | Đăng nhập thất bại với mật khẩu để trống                  | EP-PASS-03    | [TC-LOGIN-007.md](tests/test-cases/fr02-login/TC-LOGIN-007.md) |
| TC-LOGIN-008 | Đăng nhập thất bại với mật khẩu chứa ký tự SQL Injection  | EP-PASS-04    | [TC-LOGIN-008.md](tests/test-cases/fr02-login/TC-LOGIN-008.md) |
| TC-LOGIN-009 | Khóa tài khoản sau 2 lần đăng nhập sai liên tiếp          | COMBO-03      | [TC-LOGIN-009.md](tests/test-cases/fr02-login/TC-LOGIN-009.md) |
| TC-LOGIN-010 | Đăng nhập thất bại khi tài khoản đang bị khóa             | COMBO-04      | [TC-LOGIN-010.md](tests/test-cases/fr02-login/TC-LOGIN-010.md) |

**Total Domain Testing TCs:** 10

---

## A.3 Boundary Value Analysis

### A.3.1 Step 3 – BVA Table

BVA được áp dụng cho độ dài mật khẩu (giới hạn 8-32 ký tự theo spec, nhưng backend SUT thực tế hỗ trợ đến 255 ký tự) và số lần đăng nhập sai `login_attempts` (ngưỡng khóa thực tế của SUT là 3 lần):

| Variable          | Boundary | Concrete Value         | Domain  | Expected Behavior                                                      |
| ----------------- | -------- | ---------------------- | ------- | ---------------------------------------------------------------------- |
| password (length) | MIN-1    | 7 ký tự: Abc@123       | INVALID | Từ chối – mật khẩu quá ngắn (không đạt quy tắc kiểm tra)               |
| password (length) | MIN      | 8 ký tự: Abc@1234      | VALID   | Chấp nhận                                                              |
| password (length) | MIN+1    | 9 ký tự: Abc@12345     | VALID   | Chấp nhận                                                              |
| password (length) | NOM      | 12 ký tự: Abc@12345678 | VALID   | Chấp nhận                                                              |
| password (length) | MAX-1    | 254 ký tự              | VALID   | Chấp nhận                                                              |
| password (length) | MAX      | 255 ký tự              | VALID   | Chấp nhận                                                              |
| password (length) | MAX+1    | 256 ký tự              | INVALID | Từ chối – mật khẩu quá dài                                             |
| login_attempts    | MIN      | 0                      | VALID   | Tài khoản hoạt động bình thường, không có cảnh báo                     |
| login_attempts    | MAX-1    | 1                      | VALID   | Tài khoản hoạt động bình thường, không có cảnh báo                     |
| login_attempts    | MAX      | 2                      | VALID   | Tài khoản hoạt động bình thường, đây là lần sai cuối trước khi bị khóa |
| login_attempts    | MAX+1    | 3                      | INVALID | Tài khoản bị khóa (locked_until chuyển thành thời điểm tương lai)      |

**Skipped variables:** `email` — định dạng chuỗi email phân loại (categorical format), không có ranh giới thứ tự số lớn nhỏ.

---

### A.3.2 Test Cases – BVA

| TC ID            | Title                                        | Boundary covered     | GitHub link                                                            |
| ---------------- | -------------------------------------------- | -------------------- | ---------------------------------------------------------------------- |
| TC-LOGIN-BVA-001 | Đăng nhập với mật khẩu dài 7 ký tự (MIN-1)   | password MIN-1       | [TC-LOGIN-BVA-001.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-001.md) |
| TC-LOGIN-BVA-002 | Đăng nhập với mật khẩu dài 8 ký tự (MIN)     | password MIN         | [TC-LOGIN-BVA-002.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-002.md) |
| TC-LOGIN-BVA-003 | Đăng nhập với mật khẩu dài 9 ký tự (MIN+1)   | password MIN+1       | [TC-LOGIN-BVA-003.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-003.md) |
| TC-LOGIN-BVA-004 | Đăng nhập với mật khẩu dài 12 ký tự (NOM)    | password NOM         | [TC-LOGIN-BVA-004.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-004.md) |
| TC-LOGIN-BVA-005 | Đăng nhập với mật khẩu dài 254 ký tự (MAX-1) | password MAX-1       | [TC-LOGIN-BVA-005.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-005.md) |
| TC-LOGIN-BVA-006 | Đăng nhập với mật khẩu dài 255 ký tự (MAX)   | password MAX         | [TC-LOGIN-BVA-006.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-006.md) |
| TC-LOGIN-BVA-007 | Đăng nhập với mật khẩu dài 256 ký tự (MAX+1) | password MAX+1       | [TC-LOGIN-BVA-007.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-007.md) |
| TC-LOGIN-BVA-008 | Đăng nhập sai khi login_attempts = 0         | login_attempts MIN   | [TC-LOGIN-BVA-008.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-008.md) |
| TC-LOGIN-BVA-009 | Đăng nhập sai khi login_attempts = 1         | login_attempts MAX-1 | [TC-LOGIN-BVA-009.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-009.md) |
| TC-LOGIN-BVA-010 | Đăng nhập sai khi login_attempts = 2         | login_attempts MAX   | [TC-LOGIN-BVA-010.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-010.md) |
| TC-LOGIN-BVA-011 | Đăng nhập sai khi login_attempts = 3         | login_attempts MAX+1 | [TC-LOGIN-BVA-011.md](tests/test-cases/fr02-login/TC-LOGIN-BVA-011.md) |

**Total BVA TCs:** 11

---

## A.4 AI Gap Analysis

| Gap ID | Dimension   | Missing Scenario                                                               | Why Missed                                                                                              | Proposed TC ID   |
| ------ | ----------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- | ---------------- |
| GAP-01 | Security    | Thử tấn công SQL Injection trong trường email (`' OR 1=1 --`)                  | AI chỉ tập trung vào định dạng email thông thường mà bỏ qua các trường hợp kiểm thử bảo mật đầu vào.    | TC-LOGIN-005     |
| GAP-02 | Context     | Đăng nhập bằng email chứa ký tự Unicode/Tiếng Việt                             | AI mặc định email chỉ sử dụng bộ ký tự ASCII chuẩn.                                                     | TC-LOGIN-010     |
| GAP-03 | Combination | Thử đăng nhập bằng mật khẩu đúng khi tài khoản đang bị khóa                    | AI phân tích từng điều kiện riêng lẻ mà không kết hợp trạng thái khóa tài khoản với quá trình xác thực. | TC-LOGIN-010     |
| GAP-04 | BVA         | Đăng nhập đúng tại ranh giới thời gian khóa (giây thứ 179 so với giây thứ 180) | AI không mô hình hóa biến thời gian liên tục thành các giá trị biên cụ thể để kiểm thử.                 | TC-LOGIN-BVA-011 |

---

# Feature B – FR-09: Discount Coupons <a name="feature-b"></a>

## B.1 Feature Overview

Tính năng Mã giảm giá (FR-09) giúp khách hàng nhập coupon giảm giá tại checkout. Luồng chính áp dụng thành công khi thỏa mãn mã hoạt động, còn hạn dùng, giỏ hàng đạt tối thiểu và chưa vượt lượt dùng. Luồng ngoại lệ từ chối áp dụng và báo lỗi chi tiết khi vi phạm bất kỳ điều kiện nào.

**Requirement ID:** FR-09

---

## B.2 Domain Testing

### B.2.1 Step 1 – Variable Identification

| #   | Variable      | Data Type | Valid Domain                                                        | Invalid Domain                      | Constraints                     |
| --- | ------------- | --------- | ------------------------------------------------------------------- | ----------------------------------- | ------------------------------- |
| 1   | coupon_code   | string    | Chuỗi mã coupon có tồn tại và active (`SAVE10`, `BIGBUY`, `VIP100`) | Mã không tồn tại hoặc inactive      | Bắt buộc nhập                   |
| 2   | order_total   | decimal   | Giá trị giỏ hàng $\ge$ min_order_amount                             | Giá trị giỏ hàng < min_order_amount | Bắt buộc để tính toán           |
| 3   | coupon_status | enum      | Active / Inactive                                                   | null                                | Trạng thái hoạt động của coupon |
| 4   | usage_count   | integer   | Số lần sử dụng < max_uses_per_user                                  | $\ge$ max_uses_per_user             | Trạng thái sử dụng của user     |
| 5   | expiry_date   | date      | Ngày hiện tại < expired_at                                          | Ngày hiện tại $\ge$ expired_at      | Hạn sử dụng của coupon          |

**Inter-variable dependencies:**

- Mã coupon chỉ được áp dụng nếu `coupon_status` = Active, `expiry_date` còn hiệu lực, `usage_count` chưa vượt giới hạn, và `order_total` đủ ngưỡng.
- Giá trị giảm giá phụ thuộc loại coupon (`percent` hoặc `fixed`).

---

### B.2.2 Step 2 – Equivalence Partitioning

| Class ID    | Variable    | Type    | Description                   | Representative Value | Expected Behavior                   |
| ----------- | ----------- | ------- | ----------------------------- | -------------------- | ----------------------------------- |
| EP-CODE-01  | coupon_code | VALID   | Mã tồn tại, còn hạn, còn lượt | `SAVE10`             | Cho phép tiếp tục xác thực          |
| EP-CODE-02  | coupon_code | INVALID | Mã không tồn tại              | `NONEXIST`           | Báo lỗi: Mã giảm giá không tồn tại  |
| EP-CODE-03  | coupon_code | INVALID | Mã đã hết hạn                 | `EXPIRED_COUPON`     | Báo lỗi: Mã giảm giá đã hết hạn     |
| EP-CODE-04  | coupon_code | INVALID | Mã đã hết lượt dùng           | `EXHAUSTED`          | Báo lỗi: Mã đã đạt giới hạn sử dụng |
| EP-CODE-05  | coupon_code | INVALID | Mã rỗng                       | `""`                 | Báo lỗi: Mã giảm giá bắt buộc       |
| EP-ORDER-01 | order_total | VALID   | Đủ minimum order value        | `400,000` ₫          | Áp dụng coupon thành công           |
| EP-ORDER-02 | order_total | INVALID | Dưới minimum order value      | `200,000` ₫          | Báo lỗi: Đơn hàng không đủ ngưỡng   |

---

### B.2.3 Test Cases – Domain Testing

| TC ID         | Title                                                     | Class covered            | GitHub link                                                        |
| ------------- | --------------------------------------------------------- | ------------------------ | ------------------------------------------------------------------ |
| TC-COUPON-001 | Áp dụng coupon percent hợp lệ (SAVE10) thành công         | EP-CODE-01 + EP-ORDER-01 | [TC-COUPON-001.md](tests/test-cases/fr09-coupons/TC-COUPON-001.md) |
| TC-COUPON-002 | Áp dụng coupon fixed hợp lệ (BIGBUY) thành công           | EP-CODE-01 + EP-ORDER-01 | [TC-COUPON-002.md](tests/test-cases/fr09-coupons/TC-COUPON-002.md) |
| TC-COUPON-003 | Áp dụng mã giảm giá không tồn tại trong hệ thống          | EP-CODE-02               | [TC-COUPON-003.md](tests/test-cases/fr09-coupons/TC-COUPON-003.md) |
| TC-COUPON-004 | Áp dụng mã giảm giá đã bị vô hiệu hóa                     | EP-CODE-03 (inactive)    | [TC-COUPON-004.md](tests/test-cases/fr09-coupons/TC-COUPON-004.md) |
| TC-COUPON-005 | Áp dụng mã giảm giá để trống                              | EP-CODE-05               | [TC-COUPON-005.md](tests/test-cases/fr09-coupons/TC-COUPON-005.md) |
| TC-COUPON-006 | Áp dụng mã giảm giá chứa ký tự SQL Injection              | EP-CODE-05 (injection)   | [TC-COUPON-006.md](tests/test-cases/fr09-coupons/TC-COUPON-006.md) |
| TC-COUPON-007 | Áp dụng coupon khi chưa đăng nhập (guest user)            | Access Control           | [TC-COUPON-007.md](tests/test-cases/fr09-coupons/TC-COUPON-007.md) |
| TC-COUPON-008 | Áp dụng coupon khi đơn hàng chưa đủ ngưỡng tối thiểu      | EP-ORDER-02              | [TC-COUPON-008.md](tests/test-cases/fr09-coupons/TC-COUPON-008.md) |
| TC-COUPON-009 | Áp dụng coupon đã hết hạn sử dụng                         | EP-CODE-03 (expired)     | [TC-COUPON-009.md](tests/test-cases/fr09-coupons/TC-COUPON-009.md) |
| TC-COUPON-010 | Áp dụng coupon khi đã dùng hết số lần tối đa              | EP-CODE-04               | [TC-COUPON-010.md](tests/test-cases/fr09-coupons/TC-COUPON-010.md) |
| TC-COUPON-011 | Xác minh công thức tính giảm giá loại phần trăm (percent) | Calculation              | [TC-COUPON-011.md](tests/test-cases/fr09-coupons/TC-COUPON-011.md) |
| TC-COUPON-012 | Xác minh công thức tính giảm giá loại cố định (fixed)     | Calculation              | [TC-COUPON-012.md](tests/test-cases/fr09-coupons/TC-COUPON-012.md) |

**Total Domain Testing TCs:** 12

---

## B.3 Boundary Value Analysis

### B.3.1 BVA Table

| Variable    | Boundary | Concrete Value        | Domain  | Expected Behavior |
| ----------- | -------- | --------------------- | ------- | ----------------- |
| order_total | MIN-1    | `minimum - 1,000 VND` | INVALID | Coupon rejected   |
| order_total | MIN      | `minimum VND`         | VALID   | Coupon accepted   |
| order_total | MIN+1    | `minimum + 1,000 VND` | VALID   | Coupon accepted   |
| usage_count | MAX-1    | `max_usage - 1`       | VALID   | Coupon usable     |
| usage_count | MAX      | `max_usage`           | INVALID | Coupon exhausted  |
| expiry_date | MAX-1    | yesterday             | INVALID | Expired           |
| expiry_date | MAX      | today                 | VALID   | Still valid       |
| expiry_date | MAX+1    | tomorrow              | VALID   | Still valid       |

---

### B.3.2 Test Cases – BVA

| TC ID             | Title                                                          | Boundary          | GitHub link                                                                |
| ----------------- | -------------------------------------------------------------- | ----------------- | -------------------------------------------------------------------------- |
| TC-COUPON-BVA-001 | Áp dụng SAVE10 với giỏ hàng có tổng tiền 299,999 ₫ (MIN-1)     | order_total MIN-1 | [TC-COUPON-BVA-001.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-001.md) |
| TC-COUPON-BVA-002 | Áp dụng SAVE10 với giỏ hàng có tổng tiền 300,000 ₫ (MIN)       | order_total MIN   | [TC-COUPON-BVA-002.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-002.md) |
| TC-COUPON-BVA-003 | Áp dụng SAVE10 với giỏ hàng có tổng tiền 300,001 ₫ (MIN+1)     | order_total MIN+1 | [TC-COUPON-BVA-003.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-003.md) |
| TC-COUPON-BVA-004 | Áp dụng BIGBUY với giỏ hàng có tổng tiền 499,999 ₫ (MIN-1)     | order_total MIN-1 | [TC-COUPON-BVA-004.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-004.md) |
| TC-COUPON-BVA-005 | Áp dụng BIGBUY với giỏ hàng có tổng tiền 500,000 ₫ (MIN)       | order_total MIN   | [TC-COUPON-BVA-005.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-005.md) |
| TC-COUPON-BVA-006 | Áp dụng BIGBUY với giỏ hàng có tổng tiền 500,001 ₫ (MIN+1)     | order_total MIN+1 | [TC-COUPON-BVA-006.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-006.md) |
| TC-COUPON-BVA-007 | Áp dụng VIP100 với giỏ hàng có tổng tiền 299,999 ₫ (MIN-1)     | order_total MIN-1 | [TC-COUPON-BVA-007.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-007.md) |
| TC-COUPON-BVA-008 | Áp dụng VIP100 với giỏ hàng có tổng tiền 300,000 ₫ (MIN)       | order_total MIN   | [TC-COUPON-BVA-008.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-008.md) |
| TC-COUPON-BVA-009 | Áp dụng VIP100 với giỏ hàng có tổng tiền 300,001 ₫ (MIN+1)     | order_total MIN+1 | [TC-COUPON-BVA-009.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-009.md) |
| TC-COUPON-BVA-010 | Áp dụng VIP100 khi đã sử dụng 1 lần trước đó (MAX)             | usage_count MAX   | [TC-COUPON-BVA-010.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-010.md) |
| TC-COUPON-BVA-011 | Áp dụng VIP100 khi đã sử dụng 2 lần trước đó (MAX+1)           | usage_count MAX+1 | [TC-COUPON-BVA-011.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-011.md) |
| TC-COUPON-BVA-012 | Áp dụng coupon với expired_at bằng thời gian quá khứ (MIN-1)   | expiry_date MAX-1 | [TC-COUPON-BVA-012.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-012.md) |
| TC-COUPON-BVA-013 | Áp dụng coupon với expired_at bằng thời gian tương lai (MIN+1) | expiry_date MAX+1 | [TC-COUPON-BVA-013.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-013.md) |
| TC-COUPON-BVA-014 | Áp dụng coupon khi chưa từng sử dụng trước đó (MIN)            | usage_count MIN   | [TC-COUPON-BVA-014.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-014.md) |
| TC-COUPON-BVA-015 | Áp dụng coupon với expired_at bằng ngày hiện tại (today)       | expiry_date MAX   | [TC-COUPON-BVA-015.md](tests/test-cases/fr09-coupons/TC-COUPON-BVA-015.md) |

**Total BVA TCs:** 15

---

## B.4 AI Gap Analysis

| Gap ID | Dimension   | Missing Scenario                                                                                                      | Why Missed                                                                                                       | Proposed TC ID    |
| ------ | ----------- | --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------- |
| GAP-01 | Combination | Áp dụng đồng thời nhiều coupon khác nhau cho cùng một đơn hàng                                                        | AI giả định mỗi đơn hàng chỉ được áp dụng tối đa một coupon nên bỏ qua kịch bản kiểm thử tích hợp.               | TC-COUPON-007     |
| GAP-02 | Context     | Áp dụng coupon chỉ có hiệu lực với một danh mục sản phẩm cụ thể (Category-restricted coupon)                          | AI giả định mọi coupon đều áp dụng cho toàn bộ cửa hàng (Global coupons).                                        | TC-COUPON-008     |
| GAP-03 | Security    | Thử tấn công SQL Injection thông qua trường nhập mã coupon (`SAVE10' OR 1=1 --`)                                      | AI chỉ kiểm tra sự tồn tại của mã coupon trong CSDL mà bỏ qua các trường hợp kiểm thử bảo mật đầu vào.           | TC-COUPON-006     |
| GAP-04 | BVA         | Kiểm thử ranh giới thời gian hết hạn của coupon ở mức mili giây (23:59:59.999 so với 00:00:00.000 của ngày tiếp theo) | AI chỉ phân tích theo ngày dạng tĩnh mà không mô hình hóa dữ liệu `datetime` với độ chính xác và múi giờ cụ thể. | TC-COUPON-BVA-015 |

---

# Feature C – FR-14: Category Management CRUD <a name="feature-c"></a>

## C.1 Feature Overview

Tính năng Quản lý danh mục (FR-14) giúp Admin quản lý cây danh mục sản phẩm của EShop. Luồng chính tạo/xóa thành công danh mục khi có quyền Admin và tên hợp lệ. Luồng ngoại lệ từ chối tạo khi thiếu tên, trùng tên hoặc không đủ thẩm quyền Admin.

**Requirement ID:** FR-14

---

## C.2 Domain Testing

### C.2.1 Step 1 – Variable Identification

| #   | Variable        | Data Type | Valid Domain                            | Invalid Domain                       | Constraints      |
| --- | --------------- | --------- | --------------------------------------- | ------------------------------------ | ---------------- |
| 1   | category_name   | string    | Tên mới chưa tồn tại, dài $\ge 1$ ký tự | Tên rỗng hoặc chứa toàn khoảng trắng | Bắt buộc khi tạo |
| 2   | description     | string    | Chuỗi mô tả tùy ý                       | null                                 | Tùy chọn         |
| 3   | status          | enum      | Active / Inactive                       | null                                 | Mặc định Active  |
| 4   | parent_category | reference | ID danh mục cha hợp lệ                  | ID không tồn tại                     | Tùy chọn         |

**Inter-variable dependencies:**

- Việc thêm danh mục mới yêu cầu phân quyền của token gửi lên phải là Admin.
- Xóa danh mục bằng ID sẽ xóa liên kết danh mục cha-con và cập nhật các sản phẩm thuộc danh mục đó.

---

### C.2.2 Step 2 – Equivalence Partitioning

| Class ID     | Variable      | Type    | Description                | Representative Value   | Expected Behavior                |
| ------------ | ------------- | ------- | -------------------------- | ---------------------- | -------------------------------- |
| EP-CNAME-01  | category_name | VALID   | Tên mới, chưa tồn tại      | `Gia dụng`             | Tạo thành công                   |
| EP-CNAME-02  | category_name | INVALID | Tên đã tồn tại (duplicate) | `Điện thoại`           | Báo tên trùng lặp (SUT cho phép) |
| EP-CNAME-03  | category_name | INVALID | Tên rỗng                   | `""`                   | Báo lỗi tên bắt buộc             |
| EP-CNAME-04  | category_name | INVALID | Tên chỉ có ký tự đặc biệt  | `"   "` (khoảng trắng) | Báo lỗi tên bắt buộc             |
| EP-STATUS-01 | status        | VALID   | Active                     | `Active`               | Chấp nhận                        |
| EP-STATUS-02 | status        | VALID   | Inactive                   | `Inactive`             | Chấp nhận                        |

---

### C.2.3 Test Cases – Domain Testing

| TC ID      | Title                                                       | Class covered          | GitHub link                                                   |
| ---------- | ----------------------------------------------------------- | ---------------------- | ------------------------------------------------------------- |
| TC-CAT-001 | Admin tạo danh mục mới với tên hợp lệ                       | EP-CNAME-01 (admin)    | [TC-CAT-001.md](tests/test-cases/fr14-category/TC-CAT-001.md) |
| TC-CAT-002 | Admin tạo danh mục trùng tên                                | EP-CNAME-02            | [TC-CAT-002.md](tests/test-cases/fr14-category/TC-CAT-002.md) |
| TC-CAT-003 | Admin tạo danh mục với tên để trống                         | EP-CNAME-03            | [TC-CAT-003.md](tests/test-cases/fr14-category/TC-CAT-003.md) |
| TC-CAT-004 | Admin tạo danh mục với tên chỉ chứa khoảng trắng            | EP-CNAME-04            | [TC-CAT-004.md](tests/test-cases/fr14-category/TC-CAT-004.md) |
| TC-CAT-005 | Normal user tạo danh mục mới                                | Access Control (user)  | [TC-CAT-005.md](tests/test-cases/fr14-category/TC-CAT-005.md) |
| TC-CAT-006 | Gửi yêu cầu tạo danh mục với token không hợp lệ             | Access Control         | [TC-CAT-006.md](tests/test-cases/fr14-category/TC-CAT-006.md) |
| TC-CAT-007 | Admin xóa danh mục đang tồn tại                             | EP-ID-01               | [TC-CAT-007.md](tests/test-cases/fr14-category/TC-CAT-007.md) |
| TC-CAT-008 | Normal user xóa danh mục                                    | Access Control (user)  | [TC-CAT-008.md](tests/test-cases/fr14-category/TC-CAT-008.md) |
| TC-CAT-009 | Guest user xóa danh mục                                     | Access Control (guest) | [TC-CAT-009.md](tests/test-cases/fr14-category/TC-CAT-009.md) |
| TC-CAT-010 | Admin xóa danh mục không tồn tại                            | EP-ID-02               | [TC-CAT-010.md](tests/test-cases/fr14-category/TC-CAT-010.md) |
| TC-CAT-011 | Admin xóa danh mục đã bị xóa trước đó (Xóa hai lần)         | EP-ID-03               | [TC-CAT-011.md](tests/test-cases/fr14-category/TC-CAT-011.md) |
| TC-CAT-012 | Admin xóa danh mục với ID âm (Negative ID)                  | EP-ID-04 (negative)    | [TC-CAT-012.md](tests/test-cases/fr14-category/TC-CAT-012.md) |
| TC-CAT-013 | Admin xóa danh mục với ID không phải là số (Non-numeric ID) | EP-ID-07 (string)      | [TC-CAT-013.md](tests/test-cases/fr14-category/TC-CAT-013.md) |

**Total Domain Testing TCs:** 13

---

## C.3 Boundary Value Analysis

### C.3.1 BVA Table

| Variable               | Boundary | Concrete Value  | Domain  | Expected Behavior |
| ---------------------- | -------- | --------------- | ------- | ----------------- |
| category_name (length) | MIN-1    | 0 chars (empty) | INVALID | Reject – required |
| category_name (length) | MIN      | 1 char: `"A"`   | VALID   | Accept            |
| category_name (length) | MIN+1    | 2 chars: `"AB"` | VALID   | Accept            |
| category_name (length) | NOM      | 20 chars        | VALID   | Accept            |
| category_name (length) | MAX-1    | `254` chars     | VALID   | Accept            |
| category_name (length) | MAX      | `255` chars     | VALID   | Accept            |
| category_name (length) | MAX+1    | `256` chars     | INVALID | Reject – too long |

---

### C.3.2 Test Cases – BVA

| TC ID          | Title                                          | Boundary   | GitHub link                                                           |
| -------------- | ---------------------------------------------- | ---------- | --------------------------------------------------------------------- |
| TC-CAT-BVA-001 | Admin tạo danh mục với tên dài 0 ký tự (MIN-1) | name MIN-1 | [TC-CAT-BVA-001.md](tests/test-cases/fr14-category/TC-CAT-BVA-001.md) |
| TC-CAT-BVA-002 | Admin tạo danh mục với tên dài 1 ký tự (MIN)   | name MIN   | [TC-CAT-BVA-002.md](tests/test-cases/fr14-category/TC-CAT-BVA-002.md) |
| TC-CAT-BVA-003 | Admin tạo danh mục với tên dài 2 ký tự (MIN+1) | name MIN+1 | [TC-CAT-BVA-003.md](tests/test-cases/fr14-category/TC-CAT-BVA-003.md) |
| TC-CAT-BVA-004 | Admin xóa danh mục với ID bằng 0 (MIN-1)       | id MIN-1   | [TC-CAT-BVA-004.md](tests/test-cases/fr14-category/TC-CAT-BVA-004.md) |
| TC-CAT-BVA-005 | Admin xóa danh mục với ID bằng 1 (MIN)         | id MIN     | [TC-CAT-BVA-005.md](tests/test-cases/fr14-category/TC-CAT-BVA-005.md) |
| TC-CAT-BVA-006 | Admin xóa danh mục với ID bằng 2 (MIN+1)       | id MIN+1   | [TC-CAT-BVA-006.md](tests/test-cases/fr14-category/TC-CAT-BVA-006.md) |

**Total BVA TCs:** 6

---

## C.4 AI Gap Analysis

| Gap ID | Dimension   | Missing Scenario                                                                        | Why Missed                                                                                               | Proposed TC ID             |
| ------ | ----------- | --------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------- |
| GAP-01 | Combination | Admin thực hiện xóa danh mục cha đang chứa các danh mục con                             | AI bỏ sót kiểm thử tích hợp liên quan đến mối quan hệ cha–con (parent-child hierarchy).                  | TC-CAT-007                 |
| GAP-02 | Security    | Thử tấn công Stored XSS bằng cách chèn thẻ `<script>alert(1)</script>` vào tên danh mục | AI bỏ qua việc kiểm thử an toàn đầu vào (input sanitization) trước khi lưu vào CSDL.                     | TC-CAT-SEC-001             |
| GAP-03 | Context     | Người dùng có vai trò Normal User hoặc Guest gọi API để tạo/xóa danh mục                | AI giả định middleware luôn xử lý phân quyền chính xác nên không kiểm thử quyền truy cập dựa trên Token. | TC-CAT-005, TC-CAT-008     |
| GAP-04 | BVA         | Admin gửi yêu cầu xóa với ID bằng 0 (MIN-1) hoặc ID chứa ký tự không phải số            | AI chỉ áp dụng BVA cho độ dài tên danh mục mà bỏ qua giá trị biên của trường ID danh mục.                | TC-CAT-BVA-004, TC-CAT-013 |

---

# Feature D – FR-06 Mobile: Product Detail View <a name="feature-d"></a>

## D.1 Feature Overview

Tính năng Xem chi tiết sản phẩm trên Mobile App (FR-06) hiển thị hình ảnh sản phẩm, tên, giá, mô tả, danh mục, và cho phép chọn số lượng để thêm vào giỏ hàng. Sự khác biệt là mobile UI dễ bị tràn nội dung (overflow) và các tương tác chạm phải được phản hồi trực quan.

**Requirement ID:** FR-06 (Mobile – Pool D)

---

## D.2 Domain Testing

### D.2.1 Step 1 – Variable Identification

| #   | Variable | Data Type | Valid Domain                                                  | Invalid Domain                             | Constraints                  |
| --- | -------- | --------- | ------------------------------------------------------------- | ------------------------------------------ | ---------------------------- |
| 1   | quantity | string    | Chuỗi biểu diễn số nguyên dương $\ge 1$ (ví dụ: `"1"`, `"5"`) | Số `"0"`, âm, thập phân, rỗng hoặc chữ     | Bắt buộc nhập qua TextInput  |
| 2   | product  | object    | Đối tượng sản phẩm tồn tại đầy đủ thông tin bắt buộc          | undefined, null hoặc thiếu trường bắt buộc | Đối tượng bắt buộc để render |

**Inter-variable dependencies:**

- Nút "Thêm vào giỏ hàng" chỉ có tác dụng khi `product` hợp lệ và `quantity` được nhập.
- SUT thực tế sử dụng hàm `normalizeQuantity` tự động chuyển đổi các đầu vào không hợp lệ thành `1` (hoặc parse thành int).

---

### D.2.2 Step 2 – Equivalence Partitioning

| Class ID   | Variable | Type    | Description             | Representative Value   | Expected Behavior                                  |
| ---------- | -------- | ------- | ----------------------- | ---------------------- | -------------------------------------------------- |
| EP-QTY-01  | quantity | VALID   | Số nguyên dương         | `"5"`                  | Thêm vào giỏ thành công với số lượng 5             |
| EP-QTY-02  | quantity | INVALID | Giá trị bằng 0          | `"0"`                  | Báo lỗi số lượng phải $\ge 1$ (SUT fallback = 1)   |
| EP-QTY-03  | quantity | INVALID | Số nguyên âm            | `"-3"`                 | Báo lỗi số lượng phải $\ge 1$ (SUT fallback = 1)   |
| EP-QTY-04  | quantity | INVALID | Số thập phân            | `"1.5"`                | Báo lỗi số lượng phải $\ge 1$ (SUT fallback = 1)   |
| EP-QTY-05  | quantity | INVALID | Chuỗi rỗng/khoảng trắng | `""`                   | Báo lỗi số lượng phải $\ge 1$ (SUT fallback = 1)   |
| EP-QTY-06  | quantity | INVALID | Chuỗi hỗn hợp chữ số    | `"2a"`                 | Báo lỗi số lượng phải $\ge 1$ (SUT parses thành 2) |
| EP-QTY-07  | quantity | INVALID | Chuỗi chữ hoàn toàn     | `"abc"`                | Báo lỗi số lượng phải $\ge 1$ (SUT fallback = 1)   |
| EP-PROD-01 | product  | VALID   | Sản phẩm tồn tại        | `{id:1, price:100}`    | Hiển thị đầy đủ thông tin                          |
| EP-PROD-03 | product  | INVALID | Sản phẩm không tồn tại  | `undefined`            | Màn hình báo sản phẩm không tồn tại                |
| EP-PROD-04 | product  | INVALID | Thiếu trường bắt buộc   | `{id:2}` (thiếu price) | Xử lý an toàn, không crash                         |

---

### D.2.3 Test Cases – Domain Testing

| TC ID        | Title                                                               | Class covered    | GitHub link                                                           |
| ------------ | ------------------------------------------------------------------- | ---------------- | --------------------------------------------------------------------- |
| TC-MPROD-001 | Xem chi tiết sản phẩm thành công trên Mobile App                    | EP-PROD-01       | [TC-MPROD-001.md](tests/test-cases/fr-mobile-product/TC-MPROD-001.md) |
| TC-MPROD-002 | Thêm vào giỏ hàng thành công với số lượng nguyên dương              | COMBO-01         | [TC-MPROD-002.md](tests/test-cases/fr-mobile-product/TC-MPROD-002.md) |
| TC-MPROD-003 | Thêm vào giỏ hàng với số lượng bằng 0                               | COMBO-02         | [TC-MPROD-003.md](tests/test-cases/fr-mobile-product/TC-MPROD-003.md) |
| TC-MPROD-004 | Thêm vào giỏ hàng với số lượng âm                                   | COMBO-03         | [TC-MPROD-004.md](tests/test-cases/fr-mobile-product/TC-MPROD-004.md) |
| TC-MPROD-005 | Thêm vào giỏ hàng với số lượng thập phân                            | COMBO-04         | [TC-MPROD-005.md](tests/test-cases/fr-mobile-product/TC-MPROD-005.md) |
| TC-MPROD-006 | Thêm vào giỏ hàng với số lượng để trống hoặc chỉ có khoảng trắng    | COMBO-05         | [TC-MPROD-006.md](tests/test-cases/fr-mobile-product/TC-MPROD-006.md) |
| TC-MPROD-007 | Thêm vào giỏ hàng với số lượng chứa ký tự hỗn hợp (chữ và số)       | COMBO-06         | [TC-MPROD-007.md](tests/test-cases/fr-mobile-product/TC-MPROD-007.md) |
| TC-MPROD-008 | Thêm vào giỏ hàng với số lượng là chuỗi chữ hoàn toàn (Non-numeric) | COMBO-07         | [TC-MPROD-008.md](tests/test-cases/fr-mobile-product/TC-MPROD-008.md) |
| TC-MPROD-009 | Xem chi tiết sản phẩm khi sản phẩm đang tải (loading)               | State Transition | [TC-MPROD-009.md](tests/test-cases/fr-mobile-product/TC-MPROD-009.md) |
| TC-MPROD-010 | Xem chi tiết sản phẩm khi sản phẩm không tồn tại (undefined)        | COMBO-09         | [TC-MPROD-010.md](tests/test-cases/fr-mobile-product/TC-MPROD-010.md) |
| TC-MPROD-011 | Xem chi tiết sản phẩm bị thiếu trường thông tin bắt buộc            | COMBO-10         | [TC-MPROD-011.md](tests/test-cases/fr-mobile-product/TC-MPROD-011.md) |

**Total Domain Testing TCs:** 11

---

## D.3 Boundary Value Analysis

### D.3.1 BVA Table

| Variable | Boundary | Concrete Value | Domain  | Expected Behavior           |
| -------- | -------- | -------------- | ------- | --------------------------- |
| quantity | MIN-1    | `0`            | INVALID | Từ chối                     |
| quantity | MIN      | `1`            | VALID   | Chấp nhận và thêm 1 vào giỏ |
| quantity | MIN+1    | `2`            | VALID   | Chấp nhận và thêm 2 vào giỏ |
| quantity | NOM      | `5`            | VALID   | Chấp nhận và thêm 5 vào giỏ |

---

### D.3.2 Test Cases – BVA

| TC ID            | Title                                         | Boundary       | GitHub link                                                                   |
| ---------------- | --------------------------------------------- | -------------- | ----------------------------------------------------------------------------- |
| TC-MPROD-BVA-001 | Thêm vào giỏ hàng với số lượng bằng 0 (MIN-1) | quantity MIN-1 | [TC-MPROD-BVA-001.md](tests/test-cases/fr-mobile-product/TC-MPROD-BVA-001.md) |
| TC-MPROD-BVA-002 | Thêm vào giỏ hàng với số lượng bằng 1 (MIN)   | quantity MIN   | [TC-MPROD-BVA-002.md](tests/test-cases/fr-mobile-product/TC-MPROD-BVA-002.md) |
| TC-MPROD-BVA-003 | Thêm vào giỏ hàng với số lượng bằng 2 (MIN+1) | quantity MIN+1 | [TC-MPROD-BVA-003.md](tests/test-cases/fr-mobile-product/TC-MPROD-BVA-003.md) |
| TC-MPROD-BVA-004 | Thêm vào giỏ hàng với số lượng bằng 5 (NOM)   | quantity NOM   | [TC-MPROD-BVA-004.md](tests/test-cases/fr-mobile-product/TC-MPROD-BVA-004.md) |

**Total BVA TCs:** 4

---

## D.4 AI Gap Analysis

| Gap ID | Dimension    | Missing Scenario                                                                                                                       | Why Missed                                                                                              | Proposed TC ID |
| ------ | ------------ | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | -------------- |
| GAP-01 | Context      | Kiểm tra khả năng hiển thị và co giãn giao diện khi xoay màn hình thiết bị (portrait ↔ landscape)                                      | AI không có thiết bị vật lý để kiểm thử các thay đổi động của giao diện người dùng.                     | TC-MPROD-001   |
| GAP-02 | Verification | Kiểm chứng trạng thái giỏ hàng (Cart state) và số lượng trên biểu tượng giỏ hàng (Cart Badge) được cập nhật đúng sau khi thêm sản phẩm | AI chỉ xác thực thông báo Toast trên giao diện mà bỏ qua việc kiểm tra đồng bộ dữ liệu của giỏ hàng.    | TC-MPROD-002   |
| GAP-03 | Combination  | Người dùng nhấn liên tục hoặc nhấn đúp nút **"Thêm vào giỏ hàng"** gây ra race condition của API                                       | AI giả định các thao tác nhấn diễn ra tuần tự nên bỏ qua các tương tác đồng thời trên giao diện mobile. | TC-MPROD-002   |
| GAP-04 | BVA          | Nhập số lượng là một số nguyên cực lớn để kiểm tra khả năng xử lý tràn số                                                              | AI chỉ tập trung vào các giá trị biên nhỏ (0, 1, 2, 5) mà bỏ qua giới hạn trên của kiểu dữ liệu.        | TC-MPROD-008   |

---
