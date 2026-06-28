# TC-CAT-001: Admin tạo danh mục mới với tên hợp lệ

## Requirement ID

FR-14, FR-12

## Module / Test type / Technique

Category / Functional / Domain Testing – EP (COMBO-01)

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin (`http://localhost:5174`)

## Test data

| Field            | Value      |
| ---------------- | ---------- |
| Tên danh mục mới | `Gia dụng` |

## Test steps

1. Đăng nhập cổng Web Admin bằng tài khoản admin.
2. Điều hướng tới trang Quản lý danh mục.
3. Nhập tên danh mục: `Gia dụng` vào ô nhập liệu.
4. Bấm nút **Thêm mới**.

## Expected result

- Danh mục mới `Gia dụng` được tạo thành công.
- Danh mục xuất hiện trong danh sách hiển thị với ID mới.
- Cơ sở dữ liệu thêm dòng mới vào bảng `categories`.

## Status / Related bugs

Pass / None
