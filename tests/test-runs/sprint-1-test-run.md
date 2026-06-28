# Sprint 1 – Test Run Log

**Date:** 29/06/2026  
**Tester:** Nguyễn Đặng Đức Thịnh  
**Environment:** Browser: Chrome (Web) / Expo Go (Mobile) | OS: Windows 11 / iOS | URL: https://github.com/ttbhanh/eshop-sut

---

## Test Execution Results

| Test Case ID      | Module         | Tester                | Result | Related Bug | Note                                         |
| ----------------- | -------------- | --------------------- | ------ | ----------- | -------------------------------------------- |
| TC-LOGIN-001      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Đăng nhập thành công với admin               |
| TC-LOGIN-002      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi email không tồn tại                  |
| TC-LOGIN-003      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi email sai format                     |
| TC-LOGIN-004      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Chặn bởi browser required validator          |
| TC-LOGIN-005      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Được xử lý an toàn (SQL Injection email)     |
| TC-LOGIN-006      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Đăng nhập thất bại khi sai mật khẩu          |
| TC-LOGIN-007      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Chặn bởi browser required validator          |
| TC-LOGIN-008      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Được xử lý an toàn (SQL Injection password)  |
| TC-LOGIN-009      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Tải khoản bị khóa sau 3 lần sai              |
| TC-LOGIN-010      | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi tài khoản đang bị khóa               |
| TC-LOGIN-BVA-001  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Mật khẩu 7 ký tự bị từ chối                  |
| TC-LOGIN-BVA-002  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Mật khẩu 8 ký tự được chấp nhận              |
| TC-LOGIN-BVA-003  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Mật khẩu 9 ký tự được chấp nhận              |
| TC-LOGIN-BVA-004  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Mật khẩu 12 ký tự được chấp nhận             |
| TC-LOGIN-BVA-005  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Mật khẩu 254 ký tự được chấp nhận            |
| TC-LOGIN-BVA-006  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Mật khẩu 255 ký tự được chấp nhận            |
| TC-LOGIN-BVA-007  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | Mật khẩu 256 ký tự bị từ chối                |
| TC-LOGIN-BVA-008  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | login_attempts = 0                           |
| TC-LOGIN-BVA-009  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | login_attempts = 1                           |
| TC-LOGIN-BVA-010  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | login_attempts = 2                           |
| TC-LOGIN-BVA-011  | Login          | Nguyễn Đặng Đức Thịnh | Pass   | None        | login_attempts = 3 (Bị khóa)                 |
| TC-COUPON-001     | Coupons        | Nguyễn Đặng Đức Thịnh | Fail   | #1          | Lỗi tính sai giá trị percent giảm giá        |
| TC-COUPON-002     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Áp dụng BIGBUY giảm 50k thành công           |
| TC-COUPON-003     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi mã không tồn tại                     |
| TC-COUPON-004     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi mã bị vô hiệu hóa                    |
| TC-COUPON-005     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi mã rỗng                              |
| TC-COUPON-006     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | SQL Injection được xử lý an toàn             |
| TC-COUPON-007     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Yêu cầu đăng nhập trước khi áp dụng          |
| TC-COUPON-008     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi không đạt min order value            |
| TC-COUPON-009     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi mã hết hạn sử dụng                   |
| TC-COUPON-010     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Báo lỗi vượt quá số lần sử dụng              |
| TC-COUPON-011     | Coupons        | Nguyễn Đặng Đức Thịnh | Fail   | #1          | Percent giảm giá bị nhân ngược lên           |
| TC-COUPON-012     | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Công thức giảm giá fixed chính xác           |
| TC-COUPON-BVA-001 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | order_total = 299,999 ₫ (Bị từ chối)         |
| TC-COUPON-BVA-002 | Coupons        | Nguyễn Đặng Đức Thịnh | Fail   | #2          | order_total = 300,000 ₫ (Bị từ chối sai)     |
| TC-COUPON-BVA-003 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | order_total = 300,001 ₫ (Thành công)         |
| TC-COUPON-BVA-004 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | order_total = 499,999 ₫ (Bị từ chối)         |
| TC-COUPON-BVA-005 | Coupons        | Nguyễn Đặng Đức Thịnh | Fail   | #2          | order_total = 500,000 ₫ (Bị từ chối sai)     |
| TC-COUPON-BVA-006 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | order_total = 500,001 ₫ (Thành công)         |
| TC-COUPON-BVA-007 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | order_total = 299,999 ₫ VIP100 (Từ chối)     |
| TC-COUPON-BVA-008 | Coupons        | Nguyễn Đặng Đức Thịnh | Fail   | #2          | order_total = 300,000 ₫ VIP100 (Từ chối sai) |
| TC-COUPON-BVA-009 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | order_total = 300,001 ₫ VIP100 (Thành công)  |
| TC-COUPON-BVA-010 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Đã dùng 1 lần (Đạt max)                      |
| TC-COUPON-BVA-011 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Đã dùng 2 lần (Từ chối)                      |
| TC-COUPON-BVA-012 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Hết hạn hôm qua (Từ chối)                    |
| TC-COUPON-BVA-013 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Hết hạn ngày mai (Thành công)                |
| TC-COUPON-BVA-014 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Chưa dùng lần nào (Thành công)               |
| TC-COUPON-BVA-015 | Coupons        | Nguyễn Đặng Đức Thịnh | Pass   | None        | Hết hạn hôm nay (Thành công)                 |
| TC-CAT-001        | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Tạo danh mục thành công                      |
| TC-CAT-002        | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #3          | Cho phép tạo danh mục trùng tên              |
| TC-CAT-003        | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #4          | Cho phép tạo danh mục tên rỗng               |
| TC-CAT-004        | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #4          | Cho phép tạo danh mục tên khoảng trắng       |
| TC-CAT-005        | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #5          | Normal user tạo danh mục thành công          |
| TC-CAT-006        | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Yêu cầu token hợp lệ khi tạo                 |
| TC-CAT-007        | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Admin xóa danh mục đang có                   |
| TC-CAT-008        | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #6          | Normal user xóa danh mục thành công          |
| TC-CAT-009        | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Guest user bị chặn khi xóa                   |
| TC-CAT-010        | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Xóa ID không tồn tại không lỗi               |
| TC-CAT-011        | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Xóa danh mục đã xóa không lỗi                |
| TC-CAT-012        | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #7          | API xóa ID âm trả về 200 OK                  |
| TC-CAT-013        | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #8          | API xóa ID chữ trả về 200 OK                 |
| TC-CAT-SEC-001    | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | XSS script text được render an toàn          |
| TC-CAT-BVA-001    | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #4          | Cho phép tạo tên dài 0 ký tự                 |
| TC-CAT-BVA-002    | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Tạo danh mục tên dài 1 ký tự thành công      |
| TC-CAT-BVA-003    | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Tạo danh mục tên dài 2 ký tự thành công      |
| TC-CAT-BVA-004    | Category       | Nguyễn Đặng Đức Thịnh | Fail   | #7, #8      | Cho phép xóa ID bằng 0                       |
| TC-CAT-BVA-005    | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Xóa danh mục ID = 1 thành công               |
| TC-CAT-BVA-006    | Category       | Nguyễn Đặng Đức Thịnh | Pass   | None        | Xóa danh mục ID = 2 thành công               |
| TC-MPROD-001      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Chi tiết sản phẩm hiển thị đầy đủ            |
| TC-MPROD-002      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Thêm vào giỏ thành công số lượng > 0         |
| TC-MPROD-003      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Fail   | #9          | Thêm thành công khi số lượng = 0             |
| TC-MPROD-004      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Fail   | #10         | Thêm thành công khi số lượng âm (-3)         |
| TC-MPROD-005      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Fail   | #11         | Tự động làm tròn số lượng thập phân (1.5)    |
| TC-MPROD-006      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Fail   | #12         | Tự động add 1 khi số lượng rỗng              |
| TC-MPROD-007      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Fail   | #13         | Tự động add 2 khi nhập "2a"                  |
| TC-MPROD-008      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Fail   | #14         | Tự động add 1 khi nhập chữ "abc"             |
| TC-MPROD-009      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Trạng thái loading quay vòng tròn            |
| TC-MPROD-010      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Màn hình báo sản phẩm không tồn tại          |
| TC-MPROD-011      | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Render an toàn khi thiếu price               |
| TC-MPROD-BVA-001  | Mobile-Product | Nguyễn Đặng Đức Thịnh | Fail   | #9          | Số lượng = 0 (MIN-1) được add vào giỏ        |
| TC-MPROD-BVA-002  | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Thêm số lượng = 1 thành công                 |
| TC-MPROD-BVA-003  | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Thêm số lượng = 2 thành công                 |
| TC-MPROD-BVA-004  | Mobile-Product | Nguyễn Đặng Đức Thịnh | Pass   | None        | Thêm số lượng = 5 thành công                 |

**Result legend:** `Pass` · `Fail` · `Blocked` · `Not Run`

---

## Summary

| Metric      | Count |
| ----------- | ----- |
| Total TCs   | 82    |
| Pass        | 61    |
| Fail        | 21    |
| Blocked     | 0     |
| Not Run     | 0     |
| Bugs opened | 14    |
