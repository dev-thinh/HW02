# TC-LOGIN-BVA-001: Đăng nhập với mật khẩu dài 7 ký tự (MIN-1)

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / BVA (password length MIN-1)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value               |
| -------- | ------------------- |
| Email    | `test@eshop.com`    |
| Password | `Abc@123` (7 ký tự) |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: `Abc@123`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thất bại (do password không khớp với cơ sở dữ liệu nếu tài khoản đã đăng ký dùng mật khẩu dài hơn).
- _Lưu ý:_ Về lý thuyết ở bước đăng ký, mật khẩu 7 ký tự bị chặn. Ở trang đăng nhập, do không khớp mật khẩu, hệ thống trả về thông báo lỗi "Đăng nhập thất bại. Vui lòng kiểm tra lại."

## Status / Related bugs

Pass / None
