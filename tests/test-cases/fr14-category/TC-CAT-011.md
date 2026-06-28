# TC-CAT-011: Admin xóa danh mục đã bị xóa trước đó (Xóa hai lần)

## Requirement ID
FR-14, FR-12

## Module / Test type / Technique
Category / Functional / Domain Testing – EP (COMBO-11)

## Preconditions
- Người dùng đã đăng nhập với tài khoản Admin (`admin@eshop.com` / `Admin123!`)
- Danh mục có ID = `5` đã bị xóa trước đó

## Test data
| Field | Value |
|-------|-------|
| ID danh mục cần xóa | `5` |

## Test steps
1. Gửi request DELETE tới `http://localhost:3000/api/categories/5` kèm theo JWT Token của Admin (lần thứ nhất - thành công nếu tồn tại).
2. Tiếp tục gửi lại request DELETE tới `http://localhost:3000/api/categories/5` một lần nữa (lần thứ hai).

## Expected result
- Gửi yêu cầu lần 2 thành công nhưng không có thay đổi nào trong cơ sở dữ liệu (0 thay đổi, do ID 5 đã bị xóa từ trước).
- Hệ thống trả về thành công mà không cảnh báo lỗi danh mục đã bị xóa.

## Status / Related bugs
Not Run / None
