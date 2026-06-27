# TC-COUPON-009: Áp dụng coupon đã hết hạn sử dụng

## Requirement ID

FR-09 (C2)

## Module / Test type / Technique

Coupons / Functional / Domain Testing – EP (EP-EXP-02)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Mã giảm giá `EXPIRED` có ngày hết hạn là `2020-01-01` (đã qua)

## Test data

| Field       | Value          |
| ----------- | -------------- |
| Coupon code | `EXPIRED`      |
| Cart total  | `30,000,000` ₫ |

## Test steps

1. Nhập mã coupon `EXPIRED` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result

- Áp dụng thất bại.
- Hiển thị thông báo lỗi: "Mã giảm giá đã hết hạn".

## Status / Related bugs

Pass / None
