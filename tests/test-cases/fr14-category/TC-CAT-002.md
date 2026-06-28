# TC-CAT-002: Admin tạo danh mục trùng tên

## Requirement ID

FR-14

## Module / Test type / Technique

Category / Functional / Domain Testing – EP (COMBO-02)

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin
- Danh mục `Điện thoại` đã tồn tại trong hệ thống

## Test data

| Field            | Value        |
| ---------------- | ------------ |
| Tên danh mục mới | `Điện thoại` |

## Test steps

1. Nhập tên danh mục: `Điện thoại` vào ô nhập liệu.
2. Bấm nút **Thêm mới**.

## Expected result

- Danh mục không được tạo và báo lỗi "Tên danh mục đã tồn tại".

## Status / Related bugs

Fail / #3
