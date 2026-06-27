# TC-COUPON-004: Áp dụng mã giảm giá đã bị vô hiệu hóa

## Requirement ID

FR-09 (C1)

## Module / Test type / Technique

Coupons / Functional / Domain Testing – EP (EP-CODE-02)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Có một mã giảm giá tồn tại trong DB nhưng `is_active = 0` (ví dụ mã `INACTIVE_COUPON`)
- Đang ở trang Checkout (`/checkout`)

## Test data

| Field       | Value             |
| ----------- | ----------------- |
| Coupon code | `INACTIVE_COUPON` |
| Cart total  | `30,000,000` ₫    |

## Test steps

1. Nhập mã coupon `INACTIVE_COUPON` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result

- Áp dụng thất bại.
- Hiển thị thông báo lỗi: "Mã giảm giá không tồn tại hoặc đã bị vô hiệu hóa".

## Status / Related bugs

Pass / None
