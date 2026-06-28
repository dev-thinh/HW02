# TC-CAT-012: Admin xóa danh mục với ID âm (Negative ID)

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / Domain Testing – EP (EP-ID-04)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)

## Test data
| Field | Value |
|-------|-------|
| ID danh mục cần xóa | `-5` |

## Test steps
1. Gửi request DELETE tới `http://localhost:3000/api/categories/-5` kèm theo JWT Token của Admin.

## Expected result
- Yêu cầu thất bại do ID âm không hợp lệ.
- Hệ thống không thực hiện xóa và trả về mã lỗi 400 Bad Request.

## Status / Related bugs
Not Run / None
