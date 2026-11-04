# Lec 3: Derivatives of sin x and cos x — Tổng hợp (Feynman notes)

## Kết quả cần nhớ

> **(sin x)' = cos x**
> **(cos x)' = −sin x**

## Cách nhớ dấu

Lấy đạo hàm 4 lần liên tiếp sẽ quay vòng về chính nó:

sin → cos → −sin → −cos → sin → ...

- Đạo hàm của sin "giữ nguyên dấu" (ra cos dương)
- Đạo hàm của cos thì "đổi dấu" (ra −sin)

## Trực giác (không cần chứng minh để thấy hợp lý)

Nhìn đồ thị sin x và cos x di chuyển song song:

- Chỗ nào sin x đạt đỉnh/đáy (độ dốc = 0) → cos x = 0 tại đó ✓
- Chỗ nào sin x cắt trục 0 và đang dốc lên nhanh nhất → cos x đạt giá trị +1 tại đó ✓
- Tại x=0: (sin x)' = cos(0) = 1 — tiếp tuyến của sin x tại gốc có độ dốc 1
  (đây là lý do có xấp xỉ quen thuộc sin x ≈ x khi x nhỏ)
- Tại x=0: (cos x)' = −sin(0) = 0 — cos x đang ở đỉnh (cos 0 = 1 là max) nên
  tiếp tuyến nằm ngang, hợp lý

## Ý tưởng chứng minh (tóm tắt, không đi sâu đại số)

1. Khai triển Δf/Δx bằng công thức cộng góc → quy về hai giới hạn đặc biệt:
   lim(θ→0) sinθ/θ và lim(θ→0) [cosθ−1]/θ
2. Dùng **squeeze theorem** (kẹp diện tích tam giác nhỏ < quạt < tam giác lớn
   trên đường tròn đơn vị) để chứng minh lim(θ→0) sinθ/θ = 1
3. Từ đó suy ra lim(θ→0) [cosθ−1]/θ = 0
4. Ráp lại hai giới hạn này vào Δf/Δx → ra kết quả (sin x)' = cos x

## Liên hệ AI/ML

sin và cos xuất hiện trong **positional encoding** của kiến trúc Transformer
(mã hóa vị trí token bằng sóng sin/cos tần số khác nhau). Khi backprop lan
truyền gradient qua lớp này, công thức (sin x)'=cos x và (cos x)'=−sin x
được áp dụng tự động — không cần tự tay tính lại.
