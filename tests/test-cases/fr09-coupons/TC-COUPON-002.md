# TC-COUPON-002: Áp dụng coupon đã hết hạn bị từ chối

## Requirement ID
FR-09

## Module / Test type / Technique
Coupons / Functional / Domain Testing – Equivalence Partitioning (Invalid Class: Expired)

## Preconditions
- User đã đăng nhập
- Giỏ hàng có sản phẩm
- Coupon tồn tại trong DB nhưng **expired_date < today**

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `EXPIRED20` |
| Expiry date | Ngày trong quá khứ |
| Cart total | `300,000 VND` |

## Test steps
1. Thêm sản phẩm vào giỏ hàng
2. Vào trang Checkout
3. Nhập mã coupon `EXPIRED20`
4. Bấm **Apply**

## Expected result
- Coupon bị từ chối
- Hiển thị thông báo lỗi: "Mã coupon đã hết hạn" hoặc tương đương
- Tổng đơn hàng **không thay đổi**
- Không áp dụng discount

## Status / Related bugs
Not Run / None
