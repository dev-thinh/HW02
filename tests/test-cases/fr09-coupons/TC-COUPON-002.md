# TC-COUPON-002: Áp dụng coupon fixed hợp lệ (BIGBUY) thành công

## Requirement ID
FR-09

## Module / Test type / Technique
Coupons / Functional / Domain Testing – EP (COMBO-02)

## Preconditions
- Người dùng đã đăng nhập với tài khoản `test@eshop.com`
- Đang ở trang Checkout (`/checkout`)
- Giỏ hàng có tổng số tiền `600,000` ₫ (lớn hơn ngưỡng 500,000 ₫)
- Mã giảm giá `BIGBUY` tồn tại, đang hoạt động, còn hạn dùng và người dùng chưa từng sử dụng

## Test data
| Field | Value |
|-------|-------|
| Coupon code | `BIGBUY` |
| Cart total | `600,000` ₫ |

## Test steps
1. Đăng nhập bằng tài khoản `test@eshop.com` / `Test1234!`
2. Thêm sản phẩm vào giỏ hàng sao cho tổng tiền là `600,000` ₫
3. Đi tới trang Checkout
4. Nhập mã coupon `BIGBUY` vào ô coupon
5. Bấm nút **Áp dụng**

## Expected result
- Mã giảm giá được áp dụng thành công.
- Số tiền giảm giá hiển thị chính xác là `50,000` ₫.
- Thành tiền hiển thị chính xác: `550,000` ₫.

## Status / Related bugs
Not Run / None
