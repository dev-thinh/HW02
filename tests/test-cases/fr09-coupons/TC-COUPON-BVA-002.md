# TC-COUPON-BVA-002: Áp dụng SAVE10 với giỏ hàng có tổng tiền 300,000 ₫ (MIN)

## Requirement ID

FR-09 (C3)

## Module / Test type / Technique

Coupons / Functional / BVA (total_amount MIN for SAVE10)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)

## Test data

| Field       | Value       |
| ----------- | ----------- |
| Coupon code | `SAVE10`    |
| Cart total  | `300,000` ₫ |

## Test steps

1. Thêm sản phẩm vào giỏ sao cho tổng tiền là `300,000` ₫
2. Đi tới trang Checkout
3. Nhập mã coupon `SAVE10` vào ô coupon
4. Bấm nút **Áp dụng**

## Expected result

- Mã giảm giá được áp dụng thành công (theo spec $\ge 300,000$ ₫).

## Status / Related bugs

Fail / #2
