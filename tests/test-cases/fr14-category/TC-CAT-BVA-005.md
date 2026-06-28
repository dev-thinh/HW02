# TC-CAT-BVA-005: Admin xóa danh mục với ID bằng 1 (MIN)

## Requirement ID

FR-14

## Module / Test type / Technique

Category / Functional / BVA (id MIN)

## Preconditions

- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Danh mục có ID = `1` đang tồn tại trong hệ thống

## Test data

| Field               | Value |
| ------------------- | ----- |
| ID danh mục cần xóa | `1`   |

## Test steps

1. Gửi request DELETE tới `http://localhost:3000/api/categories/1` kèm theo JWT Token của Admin.

## Expected result

- Xóa thành công danh mục có ID = 1.
- Cơ sở dữ liệu cập nhật xóa bản ghi tương ứng.

## Status / Related bugs

Pass / None
