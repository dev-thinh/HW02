# TC-CAT-009: Guest user xóa danh mục

## Requirement ID
FR-14, FR-12

## Module / Test type / Technique
Category / Functional / Domain Testing – EP (COMBO-09)

## Preconditions
- Người dùng chưa đăng nhập (không có JWT Token)
- Danh mục có ID = `1` đang tồn tại trong hệ thống

## Test data
| Field | Value |
|-------|-------|
| ID danh mục cần xóa | `1` |

## Test steps
1. Gửi request DELETE tới `http://localhost:3000/api/categories/1` mà không có header `Authorization` (hoặc rỗng).

## Expected result
- Yêu cầu bị từ chối với mã lỗi 401 Unauthorized.
- Danh mục có ID = 1 không bị xóa.

## Status / Related bugs
Not Run / None
