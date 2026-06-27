# TC-COUPON-BVA-012: Áp dụng coupon với expired_at bằng thời gian quá khứ (MIN-1)

## Requirement ID
FR-09 (C2)

## Module / Test type / Technique
Coupons / Functional / BVA (expired_at MIN-1)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Có một coupon trong database với `expired_at` ở quá khứ (ví dụ mã `EXPIRED`, ngày hết hạn `2020-01-01`)

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `EXPIRED` |
| Cart total | `500,000` ₫ |

## Test steps
1. Nhập mã coupon `EXPIRED` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result
- Áp dụng thất bại.
- Hiển thị thông báo lỗi: "Mã giảm giá đã hết hạn".

## Status / Related bugs
Not Run / None
