# TC-COUPON-BVA-006: Áp dụng BIGBUY với giỏ hàng có tổng tiền 500,001 ₫ (MIN+1)

## Requirement ID

FR-09 (C3)

## Module / Test type / Technique

Coupons / Functional / BVA (total_amount MIN+1 for BIGBUY)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)

## Test data

| Field       | Value       |
| ----------- | ----------- |
| Coupon code | `BIGBUY`    |
| Cart total  | `500,001` ₫ |

## Test steps

1. Thêm sản phẩm vào giỏ sao cho tổng tiền là `500,001` ₫
2. Đi tới trang Checkout
3. Nhập mã coupon `BIGBUY` vào ô coupon
4. Bấm nút **Áp dụng**

## Expected result

- Mã giảm giá được áp dụng thành công.

## Status / Related bugs

Pass / None
