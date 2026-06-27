# TC-LOGIN-003: Đăng nhập thất bại với email sai định dạng

## Requirement ID

FR-02

## Module / Test type / Technique

Login / Functional / Domain Testing – EP (EP-EMAIL-03)

## Preconditions

- Đang ở trang `/login`

## Test data

| Field    | Value           |
| -------- | --------------- |
| Email    | `test_username` |
| Password | `Test1234!`     |

## Test steps

1. Mở trang `/login`
2. Nhập Email: `test_username`
3. Nhập Password: `Test1234!`
4. Bấm nút **Sign In**

## Expected result

- Trình duyệt hiển thị lỗi validate định dạng email (nếu input type="email").
- Nếu form submit được lên server, server trả về lỗi đăng nhập thất bại.
- _Lưu ý:_ Thực tế UI EShop đang dùng `type="text"` cho trường Username nên không ngăn cản submit ở phía client, dẫn đến việc submit lên server và báo lỗi chung "Đăng nhập thất bại. Vui lòng kiểm tra lại."

## Status / Related bugs

Pass / None
