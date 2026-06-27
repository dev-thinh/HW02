# TC-COUPON-BVA-008: Áp dụng VIP100 với giỏ hàng có tổng tiền 300,000 ₫ (MIN)

## Requirement ID

FR-09 (C3)

## Module / Test type / Technique

Coupons / Functional / BVA (total_amount MIN for VIP100)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)

## Test data

| Field       | Value       |
| ----------- | ----------- |
| Coupon code | `VIP100`    |
| Cart total  | `300,000` ₫ |

## Test steps

1. Thêm sản phẩm vào giỏ sao cho tổng tiền là `300,000` ₫
2. Đi tới trang Checkout
3. Nhập mã coupon `VIP100` vào ô coupon
4. Bấm nút **Áp dụng**

## Expected result

- Mã giảm giá được áp dụng thành công (theo spec $\ge 300,000$ ₫).
- _Lưu ý (SUT Bug):_ Hệ thống báo lỗi "Đơn hàng chưa đủ giá trị tối thiểu 300,000 ₫..." do code backend kiểm tra lớn hơn (`total_amount > min_order_amount`).

## Status / Related bugs

Fail / #2
