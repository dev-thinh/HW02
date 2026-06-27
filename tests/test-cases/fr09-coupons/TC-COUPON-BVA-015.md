# TC-COUPON-BVA-015: Áp dụng coupon với expired_at bằng ngày hiện tại (today)

## Requirement ID
FR-09 (C2)

## Module / Test type / Technique
Coupons / Functional / BVA (expired_at = today)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Có một coupon trong database với ngày hết hạn `expired_at` bằng ngày hiện tại (ví dụ: ngày hết hạn lúc 00:00:00 ngày hôm nay)

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `TODAY_COUPON` |
| Cart total | `500,000` ₫ |

## Test steps
1. Nhập mã coupon `TODAY_COUPON` vào ô coupon
2. Bấm nút **Áp dụng**

## Expected result
- Áp dụng thất bại.
- Vì spec quy định `today < expired_at` nên ngày hiện tại bằng ngày hết hạn sẽ bị Reject.
- Hiển thị thông báo lỗi: "Mã giảm giá đã hết hạn".

## Status / Related bugs
Not Run / None
