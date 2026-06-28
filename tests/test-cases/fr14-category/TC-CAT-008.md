# TC-CAT-008: Normal user xóa danh mục

## Requirement ID
FR-14, FR-12

## Module / Test type / Technique
Category / Functional / Domain Testing – EP (COMBO-08)

## Preconditions
- Người dùng đã đăng nhập với tài khoản User thường (`test@eshop.com` / `Test1234!`)
- Danh mục có ID = `1` đang tồn tại trong hệ thống
- Gửi yêu cầu qua API DELETE

## Test data
| Field | Value |
|-------|-------|
| ID danh mục cần xóa | `1` |

## Test steps
1. Gửi request DELETE tới `http://localhost:3000/api/categories/1` kèm theo JWT Token của User thường trong header `Authorization`.

## Expected result
- Yêu cầu bị từ chối với lỗi 403 Forbidden.
- Danh mục có ID = 1 không bị xóa khỏi cơ sở dữ liệu.

## Status / Related bugs
Not Run / None
