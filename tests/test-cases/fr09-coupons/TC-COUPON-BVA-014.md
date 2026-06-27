# TC-COUPON-BVA-014: Áp dụng coupon khi chưa từng sử dụng trước đó (MIN)

## Requirement ID

FR-09 (C5)

## Module / Test type / Technique

Coupons / Functional / BVA (coupon_usage MIN for SAVE10)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Người dùng chưa từng sử dụng mã `SAVE10` (`coupon_usage = 0`, giới hạn `max_uses_per_user = 1`)
- Đang ở trang Checkout (`/checkout`)
- Giỏ hàng có tổng tiền `500,000` ₫

## Test data

| Field       | Value       |
| ----------- | ----------- |
| Coupon code | `SAVE10`    |
| Cart total  | `500,000` ₫ |

## Test steps

1. Nhập mã coupon `SAVE10` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result

- Mã giảm giá được áp dụng thành công.

## Status / Related bugs

Pass / None
