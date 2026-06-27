# TC-COUPON-BVA-011: Áp dụng VIP100 khi đã sử dụng 2 lần trước đó (MAX+1)

## Requirement ID

FR-09 (C5)

## Module / Test type / Technique

Coupons / Functional / BVA (coupon_usage MAX+1 for VIP100)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Người dùng đã sử dụng mã `VIP100` đúng 2 lần trong lịch sử mua hàng (`coupon_usage = 2`, giới hạn `max_uses_per_user = 2`)
- Đang ở trang Checkout (`/checkout`)
- Giỏ hàng có tổng tiền `30,000,000` ₫

## Test data

| Field       | Value          |
| ----------- | -------------- |
| Coupon code | `VIP100`       |
| Cart total  | `30,000,000` ₫ |

## Test steps

1. Nhập mã coupon `VIP100` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result

- Áp dụng thất bại.
- Hiển thị thông báo lỗi: "Bạn đã sử dụng mã này 2 lần (đã đạt giới hạn)".

## Status / Related bugs

Pass / None
