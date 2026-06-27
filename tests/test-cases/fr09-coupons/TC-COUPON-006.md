# TC-COUPON-006: Áp dụng mã giảm giá chứa ký tự SQL Injection

## Requirement ID
FR-09, SEC-05

## Module / Test type / Technique
Coupons / Security / Domain Testing – EP (EP-CODE-05)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `' OR 1=1 --` |
| Cart total | `500,000` ₫ |

## Test steps
1. Nhập mã coupon `' OR 1=1 --` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result
- Áp dụng thất bại.
- Hệ thống xử lý an toàn và báo lỗi "Mã giảm giá không tồn tại hoặc đã bị vô hiệu hóa" thay vì gây lỗi cú pháp cơ sở dữ liệu.

## Status / Related bugs
Not Run / None
