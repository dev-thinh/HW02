# TC-COUPON-BVA-013: Áp dụng coupon với expired_at bằng thời gian tương lai (MIN+1)

## Requirement ID

FR-09 (C2)

## Module / Test type / Technique

Coupons / Functional / BVA (expired_at MIN+1)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Có một coupon trong database với `expired_at` ở tương lai (ví dụ mã `SAVE10`, ngày hết hạn `2099-12-31`)

## Test data

| Field       | Value       |
| ----------- | ----------- |
| Coupon code | `SAVE10`    |
| Cart total  | `500,000` ₫ |

## Test steps

1. Nhập mã coupon `SAVE10` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result

- Mã giảm giá được áp dụng thành công (đáp ứng điều kiện ngày hiện tại trước expired_at).

## Status / Related bugs

Pass / None
