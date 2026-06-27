# TC-CAT-002: Tạo danh mục thất bại khi tên đã tồn tại (duplicate)

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / Domain Testing – Equivalence Partitioning (Invalid Class: Duplicate Name)

## Preconditions
- User đã đăng nhập với role **Admin**
- Danh mục `Điện tử` **đã tồn tại** trong hệ thống

## Test data
| Field | Value |
|-------|-------|
| Category name | `Điện tử` (trùng với danh mục đã có) |
| Description | `Mô tả khác` |

## Test steps
1. Truy cập `/admin/categories`
2. Bấm **Add Category**
3. Nhập tên danh mục: `Điện tử` (trùng tên)
4. Nhập mô tả
5. Bấm **Save**

## Expected result
- Hệ thống từ chối tạo danh mục
- Hiển thị thông báo lỗi: "Tên danh mục đã tồn tại" hoặc tương đương
- Không có danh mục trùng nào được thêm vào DB

## Status / Related bugs
Not Run / None
