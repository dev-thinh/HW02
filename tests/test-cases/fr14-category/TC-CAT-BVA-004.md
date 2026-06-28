# TC-CAT-BVA-004: Admin xóa danh mục với ID bằng 0 (MIN-1)

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / BVA (id MIN-1)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)

## Test data
| Field | Value |
|-------|-------|
| ID danh mục cần xóa | `0` |

## Test steps
1. Gửi request DELETE tới `http://localhost:3000/api/categories/0` kèm theo JWT Token của Admin.

## Expected result
- Yêu cầu thất bại hoặc bị chặn do ID bằng 0 không hợp lệ.
- Hệ thống không thực hiện xóa và trả về mã lỗi 400 Bad Request.

## Status / Related bugs
Not Run / None
