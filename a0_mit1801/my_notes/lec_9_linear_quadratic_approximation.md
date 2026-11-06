# Lec 9: Linear Approximation — Tổng hợp (Feynman notes)

## 1. Ý tưởng cốt lõi

Phóng to đủ gần, đường cong trông như đường thẳng. Nếu biết tiếp tuyến tại
x₀, dùng nó để "đoán" f(x) tại điểm x gần x₀, không cần tính hàm gốc.

## 2. Công thức

**f(x) ≈ f(x₀) + f'(x₀)·(x − x₀)**, chỉ đúng khi x gần x₀ (Δx nhỏ)

Chính là phương trình tiếp tuyến (Lec 1), dùng để ước lượng thay vì chỉ
tính độ dốc.

## 3. Ví dụ: tính √4.5 không cần máy tính

x₀=4 (vì √4=2 đẹp). f'(x)=1/(2√x) → f'(4)=0.25

√4.5 ≈ 2 + 0.25×0.5 = **2.125** (giá trị thật ≈2.1213, sai số ~0.004)

## 4. Vì sao sai số tăng khi xa x₀

Phần "bỏ qua" là độ cong của đồ thị — đường thẳng không bắt được độ cong.
Càng xa x₀, phần cong tích lũy càng nhiều → sai số càng lớn. (Lec 10: xấp
xỉ bậc 2, thêm đường cong parabol để chính xác hơn.)

## 5. Chứng minh chặt chẽ: sai số tiến về 0 nhanh hơn Δx

Đặt E(Δx) = f(x₀+Δx) − [f(x₀)+f'(x₀)·Δx]. Từ định nghĩa đạo hàm:

lim(Δx→0) [f(x₀+Δx)−f(x₀)]/Δx = f'(x₀)
→ lim(Δx→0) E(Δx)/Δx = 0

Suy ra trực tiếp từ định nghĩa đạo hàm, không cần giả định thêm. Nghĩa là
sai số không chỉ →0 mà còn →0 NHANH HƠN Δx (giống O(Δx²) ở Lec 1).

## 6. Liên hệ AI/ML — nền tảng gradient descent

L(w) ≈ L(w₀) + L'(w₀)·(w−w₀) — chính là xấp xỉ tuyến tính, đổi tên biến.

Công thức cập nhật w_mới = w_cũ − η·L'(w_cũ) chỉ đúng khi bước nhảy
η·L'(w) đủ nhỏ (Δx nhỏ, theo mục 5).

**Chứng minh learning rate lớn gây phân kỳ** (ví dụ L(w)=w², L'(w)=2w):

w_mới = w_cũ·(1−2η) = w_cũ·r, với r=1−2η → sau n bước: wₙ = w₀·rⁿ

| η | r | │r│ | Kết quả |
|---|---|---|---|
| 0.1 | 0.8 | <1 | hội tụ về 0 |
| 0.5 | 0 | 0 | hội tụ tức thì |
| 0.8 | −0.6 | <1 | hội tụ, dao động quanh 0 |
| 1.2 | −1.4 | >1 | **phân kỳ, wₙ→±∞** |

Khi │r│>1 (η quá lớn), bước nhảy Δw=η·L'(w) không còn nhỏ → vi phạm điều
kiện ở mục 5 → giả định xấp xỉ tuyến tính sai → cập nhật đẩy w ra xa đáy
thay vì tiến gần, loss tăng thay vì giảm.

## Kết luận

1. f(x)≈f(x₀)+f'(x₀)(x−x₀), chỉ đúng khi x gần x₀
2. Sai số →0 nhanh hơn Δx — chứng minh chặt từ định nghĩa đạo hàm, không
   phải cảm tính
3. Gradient descent dựa trên giả định này ở mỗi bước → learning rate phải
   đủ nhỏ, nếu không mô hình phân kỳ (đã chứng minh bằng số cụ thể)
