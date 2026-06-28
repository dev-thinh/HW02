# TC-CAT-005: Normal user tạo danh mục mới

## Requirement ID

FR-14, FR-12

## Module / Test type / Technique

Category / Functional / Domain Testing – EP (COMBO-05)

## Preconditions

- Người dùng đã đăng nhập với tài khoản User thường (`test@eshop.com` / `Test1234!`)
- Gửi yêu cầu qua API POST `/api/categories` bằng token của User thường

## Test data

| Field            | Value      |
| ---------------- | ---------- |
| Tên danh mục mới | `Gia dụng` |

## Test steps

1. Đăng nhập bằng tài khoản `test@eshop.com`.
2. Gửi request POST tới `http://localhost:3000/api/categories` với payload `{ "name": "Gia dụng" }` kèm JWT Token của user trong header `Authorization`.

## Expected result

- Yêu cầu bị từ chối với mã lỗi 403 Forbidden.
- Danh mục mới không được tạo trong cơ sở dữ liệu.

## Status / Related bugs

Fail / #5
