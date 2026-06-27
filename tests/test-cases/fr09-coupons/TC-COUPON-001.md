# TC-COUPON-001: Áp dụng coupon hợp lệ và được giảm giá đúng

## Requirement ID
FR-09

## Module / Test type / Technique
Coupons / Functional / Domain Testing – Equivalence Partitioning (Valid Class)

## Preconditions
- User đã đăng nhập
- Giỏ hàng có ít nhất 1 sản phẩm, tổng giá trị đủ điều kiện áp dụng coupon
- Coupon hợp lệ tồn tại trong hệ thống (chưa hết hạn, chưa dùng hết lượt)

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `SAVE10` (10% off) |
| Cart total | `500,000 VND` |
| Expected discount | `50,000 VND` |

## Test steps
1. Thêm sản phẩm vào giỏ hàng, tổng = 500,000 VND
2. Vào trang Checkout
3. Nhập mã coupon `SAVE10` vào ô coupon
4. Bấm **Apply**

## Expected result
- Coupon được chấp nhận
- Hiển thị thông báo áp dụng thành công
- Discount = 50,000 VND được trừ vào tổng đơn hàng
- Total mới = 450,000 VND

## Status / Related bugs
Not Run / None
