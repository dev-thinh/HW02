# TC-COUPON-BVA-001: Coupon không áp dụng được khi tổng đơn hàng dưới minimum (BVA – MIN boundary)

## Requirement ID
FR-09

## Module / Test type / Technique
Coupons / Functional / Boundary Value Analysis (MIN boundary – minimum order value)

## Preconditions
- User đã đăng nhập
- Coupon `MINORDER` yêu cầu tổng đơn hàng tối thiểu = **200,000 VND**
- Giỏ hàng có tổng = **199,000 VND** (MIN – 1,000)

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `MINORDER` |
| Minimum order required | `200,000 VND` |
| Cart total | `199,000 VND` |

## Test steps
1. Thêm sản phẩm vào giỏ hàng sao cho tổng = 199,000 VND
2. Vào trang Checkout
3. Nhập mã coupon `MINORDER`
4. Bấm **Apply**

## Expected result
- Coupon bị từ chối
- Hiển thị thông báo: "Đơn hàng chưa đạt giá trị tối thiểu để áp dụng mã này"
- Không giảm giá

## BVA Note
| Boundary | Cart Total | Expected |
|----------|------------|----------|
| MIN–1 (this TC) | 199,000 VND | Coupon REJECTED |
| MIN | 200,000 VND | Coupon ACCEPTED |
| MIN+1 | 201,000 VND | Coupon ACCEPTED |

## Status / Related bugs
Not Run / None
