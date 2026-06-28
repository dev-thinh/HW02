# TC-CAT-BVA-006: Admin xóa danh mục với ID bằng 2 (MIN+1)

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / BVA (id MIN+1)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Danh mục có ID = `2` đang tồn tại trong hệ thống

## Test data
| Field | Value |
|-------|-------|
| ID danh mục cần xóa | `2` |

## Test steps
1. Gửi request DELETE tới `http://localhost:3000/api/categories/2` kèm theo JWT Token của Admin.

## Expected result
- Xóa thành công danh mục có ID = 2.
- Cơ sở dữ liệu cập nhật xóa bản ghi tương ứng.

## Status / Related bugs
Not Run / None
