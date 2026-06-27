# TC-COUPON-012: Xác minh công thức tính giảm giá loại cố định (fixed)

## Requirement ID
FR-09

## Module / Test type / Technique
Coupons / Functional / Calculation Verification (fixed logic)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Mã giảm giá `BIGBUY` (giảm cố định 50,000 ₫, ngưỡng tối thiểu 500,000 ₫) có hiệu lực
- Giỏ hàng có tổng tiền `600,000` ₫

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `BIGBUY` |
| Cart total | `600,000` ₫ |

## Test steps
1. Nhập mã coupon `BIGBUY` vào ô coupon
2. Bấm nút **Áp dụng**
3. Kiểm tra số tiền giảm giá và số tiền phải trả hiển thị trên màn hình

## Expected result
- Số tiền giảm giá kỳ vọng: `50,000` ₫.
- Số tiền phải trả (Thành tiền) kỳ vọng: `550,000` ₫.
- Hệ thống phải tính toán chính xác và hiển thị đúng cả hai số liệu.

## Status / Related bugs
Not Run / None
