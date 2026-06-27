# TC-COUPON-007: Áp dụng coupon khi chưa đăng nhập (guest user)

## Requirement ID

FR-09 (C4)

## Module / Test type / Technique

Coupons / Functional / Domain Testing – EP (EP-USER-02)

## Preconditions

- Người dùng chưa đăng nhập (đang là khách vãng lai)
- Giỏ hàng có sản phẩm với tổng tiền đủ điều kiện áp dụng mã

## Test data

| Field       | Value          |
| ----------- | -------------- |
| Coupon code | `SAVE10`       |
| Cart total  | `30,000,000` ₫ |

## Test steps

1. Chọn sản phẩm và đi tới trang Checkout
2. Nhập mã coupon `SAVE10` vào ô coupon
3. Bấm nút **Áp dụng**

## Expected result

- Áp dụng thất bại (hoặc không cho phép Checkout khi chưa đăng nhập).
- Hệ thống chặn việc dùng mã giảm giá đối với khách vãng lai (yêu cầu đăng nhập trước).

## Status / Related bugs

Pass / None
