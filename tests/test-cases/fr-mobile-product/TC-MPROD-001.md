# TC-MPROD-001: Xem chi tiết sản phẩm thành công trên Mobile App

## Requirement ID
FR-06 (Mobile – Pool D)

## Module / Test type / Technique
Mobile-Product / Functional / Domain Testing – EP (EP-PROD-01)

## Preconditions
- Mobile app đã được cài đặt và đang chạy Expo Metro Bundler
- Sản phẩm tồn tại trong DB, có status = Active, có ảnh lớn, tên, giá, mô tả và danh mục.
- Người dùng có thể ở trạng thái khách vãng lai hoặc đã đăng nhập.

## Test data
| Field | Value |
|-------|-------|
| Product | iPhone 15 Pro Max (ID = 1) |

## Test steps
1. Mở Mobile App.
2. Từ màn hình Home, nhấn chọn sản phẩm `iPhone 15 Pro Max`.
3. Quan sát màn hình chi tiết sản phẩm.

## Expected result
- Hiển thị đầy đủ thông tin: Ảnh lớn sản phẩm, Tên sản phẩm, Giá sản phẩm, Mô tả sản phẩm.
- Nút **Thêm vào giỏ hàng** hiển thị đầy đủ và nhấn được.

## Status / Related bugs
Not Run / None
