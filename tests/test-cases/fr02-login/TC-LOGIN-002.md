# TC-LOGIN-002: Đăng nhập thất bại với email không tồn tại trong hệ thống

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (EP-EMAIL-02)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value             |
| -------- | ----------------- |
| Email    | `ghost@eshop.com` |
| Password | `Test1234!`       |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `ghost@eshop.com`
3. Nhập Password: `Test1234!`
4. Bấm nút **Sign In**

## Expected result

- Đăng nhập thất bại
- Hiển thị thông báo lỗi: "Đăng nhập thất bại. Vui lòng kiểm tra lại."
- Số lần đăng nhập sai của các tài khoản khác không thay đổi.

## Status / Related bugs

Pass / None
