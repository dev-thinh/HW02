# TC-MPROD-BVA-001: Hiển thị giá sản phẩm = 0 VND trên Mobile (BVA – MIN boundary)

## Requirement ID
FR-06 (Mobile – Pool D)

## Module / Test type / Technique
Mobile-Product / Functional / Boundary Value Analysis (MIN boundary – Product price display)

## Preconditions
- Mobile app đã cài đặt
- Tồn tại sản phẩm có price = **0 VND** (free product / giá = 0)

## Test data
| Field | Value |
|-------|-------|
| Product price | `0 VND` (MIN boundary) |

## Test steps
1. Mở Mobile App
2. Tìm hoặc điều hướng đến sản phẩm có giá = 0 VND
3. Tap vào sản phẩm đó
4. Quan sát cách hiển thị giá

## Expected result
- Giá hiển thị đúng: `0 ₫` hoặc `Miễn phí` (tùy design)
- Không hiển thị giá âm, không hiển thị null/undefined
- Nút Add to Cart vẫn hoạt động

## BVA Note
| Boundary | Price | Expected Display |
|----------|-------|-----------------|
| MIN–1 | < 0 | Không hợp lệ – không nên có trong hệ thống |
| MIN | 0 VND | Hiển thị đúng |
| MIN+1 | 1 VND | Hiển thị đúng |
| Typical | 100,000–10,000,000 VND | Hiển thị đúng với format VND |
| MAX | Giá trị lớn nhất cho phép | Không bị overflow UI |

## Status / Related bugs
Not Run / None
