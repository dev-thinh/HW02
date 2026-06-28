# TC-CAT-003: Admin tạo danh mục với tên để trống

## Requirement ID

FR-14

## Module / Test type / Technique

Category / Functional / Domain Testing – EP (COMBO-03)

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin

## Test data

| Field            | Value           |
| ---------------- | --------------- |
| Tên danh mục mới | `""` (để trống) |

## Test steps

1. Để trống ô nhập liệu tên danh mục.
2. Bấm nút **Thêm mới**.

## Expected result

- Yêu cầu thất bại, hệ thống báo lỗi không cho phép tạo danh mục trống.

## Status / Related bugs

Fail / #4
