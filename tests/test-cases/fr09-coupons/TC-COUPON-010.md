# TC-COUPON-010: Áp dụng coupon khi đã dùng hết số lần tối đa

## Requirement ID

FR-09 (C5)

## Module / Test type / Technique

Coupons / Functional / Domain Testing – EP (EP-USAGE-02)

## Preconditions

- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Tài khoản này đã sử dụng mã `SAVE10` đúng 1 lần trong lịch sử (đã đạt giới hạn tối đa `max_uses_per_user = 1`)
- Đang ở trang Checkout (`/checkout`)

## Test data

| Field       | Value       |
| ----------- | ----------- |
| Coupon code | `SAVE10`    |
| Cart total  | `500,000` ₫ |

## Test steps

1. Nhập mã coupon `SAVE10` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result

- Áp dụng thất bại.
- Hiển thị thông báo lỗi: "Bạn đã sử dụng mã này 1 lần (đã đạt giới hạn)".

## Status / Related bugs

Pass / None
