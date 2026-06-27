# TC-COUPON-BVA-010: Áp dụng VIP100 khi đã sử dụng 1 lần trước đó (MAX)

## Requirement ID
FR-09 (C5)

## Module / Test type / Technique
Coupons / Functional / BVA (coupon_usage MAX for VIP100)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Người dùng đã sử dụng mã `VIP100` đúng 1 lần trong lịch sử mua hàng (`coupon_usage = 1`, giới hạn `max_uses_per_user = 2`)
- Đang ở trang Checkout (`/checkout`)
- Giỏ hàng có tổng tiền `500,000` ₫

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `VIP100` |
| Cart total | `500,000` ₫ |

## Test steps
1. Nhập mã coupon `VIP100` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result
- Mã giảm giá được áp dụng thành công (đây là lần sử dụng thứ 2, đạt giới hạn tối đa cho phép).
- Số tiền giảm giá hiển thị chính xác là `100,000` ₫.

## Status / Related bugs
Not Run / None
