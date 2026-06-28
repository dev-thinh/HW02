# TC-CAT-BVA-001: Admin tạo danh mục với tên dài 0 ký tự (MIN-1)

## Requirement ID

FR-14

## Module / Test type / Technique

Category / Functional / BVA (name length MIN-1)

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Đang ở trang quản lý danh mục trên Web Admin

## Test data

| Field            | Value          |
| ---------------- | -------------- |
| Tên danh mục mới | `""` (0 ký tự) |

## Test steps

1. Để trống trường nhập liệu tên danh mục.
2. Bấm nút **Thêm mới**.

## Expected result

- Yêu cầu thất bại, hệ thống báo lỗi không cho phép tạo danh mục trống.

## Status / Related bugs

Fail / #4
