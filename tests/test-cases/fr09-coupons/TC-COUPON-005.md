# TC-COUPON-005: Áp dụng mã giảm giá để trống

## Requirement ID
FR-09

## Module / Test type / Technique
Coupons / Functional / Domain Testing – EP (EP-CODE-04)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `""` (để trống) |
| Cart total | `500,000` ₫ |

## Test steps
1. Để trống ô coupon code
2. Bấm nút **Áp dụng**

## Expected result
- Áp dụng thất bại.
- Hiển thị thông báo lỗi yêu cầu nhập mã giảm giá (ví dụ: "Vui lòng nhập mã giảm giá").

## Status / Related bugs
Not Run / None
