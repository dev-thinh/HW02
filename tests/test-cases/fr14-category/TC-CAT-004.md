# TC-CAT-004: Admin tạo danh mục với tên chỉ chứa khoảng trắng

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / Domain Testing – EP (COMBO-04)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin

## Test data
| Field | Value |
|-------|-------|
| Tên danh mục mới | `"   "` (3 dấu cách) |

## Test steps
1. Nhập `"   "` vào ô nhập liệu tên danh mục.
2. Bấm nút **Thêm mới**.

## Expected result
- Spec: Yêu cầu thất bại, hệ thống báo lỗi không cho phép tạo danh mục trống/khoảng trắng.
- *Lưu ý (SUT Bug):* Trên ứng dụng thực tế, hệ thống vẫn chấp nhận tạo danh mục chỉ gồm các khoảng trắng.

## Status / Related bugs
Not Run / None
