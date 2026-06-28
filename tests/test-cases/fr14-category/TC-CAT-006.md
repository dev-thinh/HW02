# TC-CAT-006: Gửi yêu cầu tạo danh mục với token không hợp lệ

## Requirement ID
FR-14, FR-12

## Module / Test type / Technique
Category / Security / Domain Testing – EP (COMBO-06)

## Preconditions
- Đang gửi request API trực tiếp

## Test data
| Field | Value |
|-------|-------|
| Tên danh mục mới | `Gia dụng` |
| Token | `invalid_or_expired_jwt_string` |

## Test steps
1. Gửi request POST tới `http://localhost:3000/api/categories` với payload `{ "name": "Gia dụng" }` kèm JWT Token không hợp lệ hoặc đã hết hạn trong header `Authorization`.

## Expected result
- Yêu cầu bị từ chối với mã lỗi 403 Forbidden hoặc 401 Unauthorized.
- Danh mục không được tạo.

## Status / Related bugs
Not Run / None
