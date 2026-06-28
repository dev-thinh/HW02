# TC-MPROD-009: Xem chi tiết sản phẩm khi sản phẩm đang tải (loading)

## Requirement ID
FR-06 (Mobile)

## Module / Test type / Technique
Mobile-Product / Functional / State Transition Testing (COMBO-08)

## Preconditions
- Đang gửi yêu cầu tải thông tin chi tiết của một sản phẩm.

## Test steps
1. Mở màn hình chi tiết sản phẩm.
2. Ngay lập tức kiểm tra giao diện khi dữ liệu sản phẩm chưa được tải về hoàn tất (trạng thái `loading = true`).

## Expected result
- Màn hình hiển thị chỉ báo đang tải (loading indicator hoặc chữ "Đang tải...").
- Tránh tình trạng màn hình bị trống hoàn toàn hoặc lỗi crash.

## Status / Related bugs
Not Run / None
