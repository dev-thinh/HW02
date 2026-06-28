# TC-CAT-007: Admin xóa danh mục đang tồn tại

## Requirement ID

FR-14, FR-12

## Module / Test type / Technique

Category / Functional / Domain Testing – EP (COMBO-07)

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Có một danh mục đang tồn tại trong hệ thống (ví dụ: ID = `3`, tên danh mục: `Phụ kiện`)
- Đang ở trang quản lý danh mục trên Web Admin

## Test data

| Field               | Value |
| ------------------- | ----- |
| ID danh mục cần xóa | `3`   |

## Test steps

1. Truy cập trang Quản lý danh mục.
2. Tìm danh mục `Phụ kiện` có ID = 3.
3. Bấm nút **Xóa** ở cột Hành động bên cạnh danh mục.

## Expected result

- Danh mục `Phụ kiện` bị xóa khỏi danh sách trên giao diện.
- Cơ sở dữ liệu xóa dòng có ID = 3 khỏi bảng `categories`.

## Status / Related bugs

Pass / None
