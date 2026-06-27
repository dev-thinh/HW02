# TC-COUPON-008: Áp dụng coupon khi đơn hàng chưa đủ ngưỡng tối thiểu

## Requirement ID

FR-09 (C3)

## Module / Test type / Technique

Coupons / Functional / Domain Testing – EP (EP-TOTAL-02)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Giỏ hàng có tổng tiền `250,000` ₫ (thấp hơn ngưỡng `min_order_amount` là 300,000 ₫)

## Test data

| Field       | Value       |
| ----------- | ----------- |
| Coupon code | `SAVE10`    |
| Cart total  | `250,000` ₫ |

## Test steps

1. Thêm sản phẩm vào giỏ sao cho tổng tiền là `250,000` ₫
2. Đi tới trang Checkout
3. Nhập mã coupon `SAVE10` vào ô coupon
4. Bấm nút **Áp dụng**

## Expected result

- Áp dụng thất bại.
- Hiển thị thông báo lỗi: "Đơn hàng chưa đủ giá trị tối thiểu 300,000 ₫ để áp dụng mã này".

## Status / Related bugs

Pass / None
