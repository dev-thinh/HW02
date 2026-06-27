# TC-COUPON-001: Áp dụng coupon percent hợp lệ (SAVE10) thành công

## Requirement ID

FR-09

## Module / Test type / Technique

Coupons / Functional / Domain Testing – EP (COMBO-01)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Giỏ hàng có tổng số tiền `30,000,000` ₫ (lớn hơn ngưỡng 300,000 ₫)
- Mã giảm giá `SAVE10` tồn tại, đang hoạt động, còn hạn dùng và người dùng chưa từng sử dụng

## Test data

| Field       | Value          |
| ----------- | -------------- |
| Coupon code | `SAVE10`       |
| Cart total  | `30,000,000` ₫ |

## Test steps

1. Đăng nhập bằng tài khoản `test@eshop.com` / `Test1234!`
2. Thêm sản phẩm vào giỏ hàng sao cho tổng tiền là `30,000,000` ₫
3. Đi tới trang Checkout
4. Nhập mã coupon `SAVE10` vào ô coupon
5. Bấm nút **Áp dụng**

## Expected result

- Mã giảm giá được áp dụng thành công.
- Giá trị giảm giá hiển thị chính xác: giảm 10% tức là giảm `3,000,000` ₫.

## Status / Related bugs

Fail / #1
