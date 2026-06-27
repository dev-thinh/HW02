# TC-COUPON-011: Xác minh công thức tính giảm giá loại phần trăm (percent)

## Requirement ID
FR-09

## Module / Test type / Technique
Coupons / Functional / Calculation Verification (percent logic)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Mã giảm giá `SAVE10` (giảm 10%, ngưỡng tối thiểu 300,000 ₫) có hiệu lực
- Giỏ hàng có tổng tiền `500,000` ₫

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `SAVE10` |
| Cart total | `500,000` ₫ |

## Test steps
1. Nhập mã coupon `SAVE10` vào ô coupon
2. Bấm nút **Áp dụng**
3. Kiểm tra số tiền giảm giá và số tiền phải trả hiển thị trên màn hình

## Expected result
- Số tiền giảm giá kỳ vọng: `50,000` ₫ (10% của 500,000 ₫).
- Số tiền phải trả (Thành tiền) kỳ vọng: `450,000` ₫.
- *Lưu ý (SUT Bug):* Hệ thống tính toán sai lệch do công thức lỗi ở backend (trả về giá trị giảm giá âm và cộng dồn vào tổng tiền thanh toán).

## Status / Related bugs
Not Run / None
