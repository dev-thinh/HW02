# TC-CAT-BVA-001: Tên danh mục đúng 1 ký tự (BVA – MIN boundary)

## Requirement ID
FR-14

## Module / Test type / Technique
Category / Functional / Boundary Value Analysis (MIN boundary – Category name length)

## Preconditions
- User đã đăng nhập với role **Admin**
- Giả định: tên danh mục phải có **ít nhất 1 ký tự** và **tối đa N ký tự** (cần verify từ spec/code)

## Test data
| Field | Value |
|-------|-------|
| Category name | `A` (1 ký tự – MIN) |

## Test steps
1. Truy cập `/admin/categories`
2. Bấm **Add Category**
3. Nhập tên danh mục: `A` (chỉ 1 ký tự)
4. Bấm **Save**

## Expected result
- Danh mục được tạo thành công (1 ký tự là hợp lệ nếu MIN = 1)
- HOẶC: hệ thống báo lỗi nếu MIN > 1 (cần xác định từ spec)

## BVA Note
| Boundary | Name Length | Expected |
|----------|-------------|----------|
| MIN–1 | 0 (empty) | REJECTED – required field |
| MIN | 1 | ACCEPTED (nếu min=1) |
| MIN+1 | 2 | ACCEPTED |
| MAX–1 | N–1 | ACCEPTED |
| MAX | N | ACCEPTED |
| MAX+1 | N+1 | REJECTED – too long |

*(Cần xác định N từ database schema hoặc UI validation)*

## Status / Related bugs
Not Run / None
