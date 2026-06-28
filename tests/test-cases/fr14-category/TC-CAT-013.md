# TC-CAT-013: Admin xóa danh mục với ID không phải là số (Non-numeric ID)

## Requirement ID

FR-14

## Module / Test type / Technique

Category / Functional / Domain Testing – EP (EP-ID-07)

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)

## Test data

| Field               | Value |
| ------------------- | ----- |
| ID danh mục cần xóa | `abc` |

## Test steps

1. Gửi request DELETE tới `http://localhost:3000/api/categories/abc` kèm theo JWT Token của Admin.

## Expected result

- Yêu cầu thất bại hoặc bị chặn do tham số ID không hợp lệ.
- Hệ thống trả về lỗi 400 Bad Request.

## Status / Related bugs

Fail / #8
