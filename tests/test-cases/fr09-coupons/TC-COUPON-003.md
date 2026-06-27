# TC-COUPON-003: Áp dụng mã giảm giá không tồn tại trong hệ thống

## Requirement ID
FR-09 (C1)

## Module / Test type / Technique
Coupons / Functional / Domain Testing – EP (EP-CODE-03)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `NOTEXIST` |
| Cart total | `500,000` ₫ |

## Test steps
1. Nhập mã coupon `NOTEXIST` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result
- Áp dụng thất bại.
- Hiển thị thông báo lỗi: "Mã giảm giá không tồn tại hoặc đã bị vô hiệu hóa".

## Status / Related bugs
Not Run / None
