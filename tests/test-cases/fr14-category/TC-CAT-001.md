# TC-CAT-001: Tạo danh mục mới thành công với dữ liệu hợp lệ

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / Domain Testing – Equivalence Partitioning (Valid Class: Create)

## Preconditions
- User đã đăng nhập với role **Admin**
- Đang ở trang quản lý danh mục (`/admin/categories`)
- Tên danh mục chưa tồn tại trong hệ thống

## Test data
| Field | Value |
|-------|-------|
| Category name | `Điện tử` |
| Description | `Các sản phẩm điện tử` |
| Status | Active |

## Test steps
1. Truy cập `/admin/categories`
2. Bấm nút **Add Category** / **Thêm danh mục**
3. Nhập tên danh mục: `Điện tử`
4. Nhập mô tả (nếu có)
5. Chọn Status = Active
6. Bấm **Save**

## Expected result
- Danh mục được tạo thành công
- Hiển thị thông báo thành công
- Danh mục `Điện tử` xuất hiện trong danh sách
- Danh mục có thể được chọn khi thêm sản phẩm

## Status / Related bugs
Not Run / None
