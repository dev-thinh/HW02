# TC-CAT-BVA-002: Admin tạo danh mục với tên dài 1 ký tự (MIN)

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / BVA (name length MIN)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin

## Test data
| Field | Value |
|-------|-------|
| Tên danh mục mới | `"A"` (1 ký tự) |

## Test steps
1. Nhập `"A"` vào ô tên danh mục.
2. Bấm nút **Thêm mới**.

## Expected result
- Danh mục mới `"A"` được tạo thành công.

## Status / Related bugs
Not Run / None
