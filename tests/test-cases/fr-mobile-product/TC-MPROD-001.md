# TC-MPROD-001: Xem chi tiết sản phẩm thành công trên Mobile App

## Requirement ID
FR-06 (Mobile – Pool D)

## Module / Test type / Technique
Mobile-Product / Functional / Domain Testing – Equivalence Partitioning (Valid Class: Active Product)

## Preconditions
- Mobile app đã được cài đặt
- Sản phẩm tồn tại, có status = **Active**, có ảnh và đầy đủ thông tin
- User có thể ở trạng thái guest hoặc đã đăng nhập

## Test data
| Field | Value |
|-------|-------|
| Product | Sản phẩm Active, có ảnh, có giá, có mô tả |
| User state | Guest (không cần đăng nhập) |

## Test steps
1. Mở Mobile App
2. Từ trang Home hoặc danh sách sản phẩm, tap vào một sản phẩm
3. Quan sát trang Product Detail

## Expected result
- Hiển thị đầy đủ: tên sản phẩm, ảnh, giá, mô tả
- Nút **Add to Cart** hiển thị và có thể tap
- Giao diện hiển thị đúng trên màn hình mobile (không bị overflow, không mất nội dung)
- Ảnh sản phẩm load được

## Status / Related bugs
Not Run / None
