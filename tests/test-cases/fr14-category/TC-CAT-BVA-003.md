# TC-CAT-BVA-003: Admin tạo danh mục với tên dài 2 ký tự (MIN+1)

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / BVA (name length MIN+1)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin

## Test data
| Field | Value |
|-------|-------|
| Tên danh mục mới | `"AB"` (2 ký tự) |

## Test steps
1. Nhập `"AB"` vào ô tên danh mục.
2. Bấm nút **Thêm mới**.

## Expected result
- Danh mục mới `"AB"` được tạo thành công.

## Status / Related bugs
Not Run / None
