# TC-LOGIN-009: Khóa tài khoản sau 2 lần đăng nhập sai liên tiếp

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (COMBO-03)

## Preconditions

- Tài khoản `test@eshop.com` tồn tại và chưa bị khóa
- login_attempts = 2 (đã sai 1 lần trước đó)
- Đang ở trang `/login`

## Test data

| Field    | Value            |
| -------- | ---------------- |
| Email    | `test@eshop.com` |
| Password | `WrongPass123!`  |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test@eshop.com`
3. Nhập Password: `WrongPass123!`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thất bại.
- `login_attempts` trong database tăng lên 4 (đã vượt quá ngưỡng $\ge 3$).
- Tài khoản bị tạm khóa.
- Hệ thống thiết lập `locked_until` thành thời gian hiện tại cộng thêm 3 phút (180 giây).

## Status / Related bugs

Pass / None
