# Lec 10: Quadratic Approximation & Curve Sketching — Tổng hợp (Feynman notes)

## Phần A: Xấp xỉ bậc 2

Đường thẳng (Lec 9) không bắt được độ cong → thêm số hạng bậc 2 (parabol):

**f(x) ≈ f(x₀) + f'(x₀)·(x−x₀) + ½·f''(x₀)·(x−x₀)²**

f''(x₀) = đạo hàm của đạo hàm = đo độ cong tại x₀. Hệ số ½ là bắt buộc để
đạo hàm bậc 2 hai vế khớp nhau tại x₀ (không phải tùy chọn).

### Ví dụ: cos x gần x=0

cos(0)=1, (cos x)'(0)=0, (cos x)''(0)=−1

**cos x ≈ 1 − x²/2**

Bám sát giá trị thật tốt hơn nhiều so với xấp xỉ tuyến tính (chỉ =1, hằng
số, vì f'(0)=0).

## Phần B: Curve Sketching — đọc hình dạng đồ thị từ dấu f', f''

### Dấu f' — tăng/giảm

- f'(x)>0 → hàm đang TĂNG
- f'(x)<0 → hàm đang GIẢM
- f'(x)=0 → điểm dừng (có thể là max, min, hoặc điểm yên — Lec 11-12)

### Dấu f'' — concave up/down

- f''(x)>0 → **concave up** (lõm lên, hình chén ∪), độ dốc f' đang tăng dần
- f''(x)<0 → **concave down** (lồi xuống, hình mũ ∩), độ dốc f' đang giảm
- f'' đổi dấu → **điểm uốn (inflection point)**

### Ví dụ: f(x) = x³ − 3x

f'(x) = 3x²−3 = 3(x−1)(x+1) → f'=0 tại x=±1

| Khoảng | x<−1 | −1<x<1 | x>1 |
|---|---|---|---|
| f' | + | − | + |
| → | tăng | giảm | tăng |

x=−1: local max (tăng→giảm). x=1: local min (giảm→tăng).

f''(x)=6x → âm khi x<0, dương khi x>0 → điểm uốn tại x=0.

### Bài tập tự chứng minh: g(x)=x² tại x=0

f'=2x (âm khi x<0, dương khi x>0 → đổi dấu qua 0 → điểm dừng là min)
f''=2 (dương TẠI MỌI x, không chỉ x=0) → concave up toàn bộ, không có
hướng nào lật dấu → x=0 chắc chắn là cực tiểu, không thể là saddle point.

## Liên hệ AI/ML

- f'' (với nhiều biến: ma trận **Hessian**) là nền tảng của các phương pháp
  tối ưu bậc 2 (Newton's method, L-BFGS) — dùng độ cong của loss để chọn
  bước nhảy thông minh hơn gradient descent thường (chỉ dùng f').
- **Saddle point**: điểm có f'=0 nhưng f'' âm theo hướng này, dương theo
  hướng khác — trông giống đáy nhưng không phải điểm tối ưu. Bẫy phổ biến
  khi huấn luyện mạng nơ-ron sâu.
- Hàm loss MSE trong hồi quy tuyến tính có dạng giống x² (convex, chỉ 1
  đáy, không saddle point) → dễ huấn luyện. Loss của mạng nơ-ron sâu phức
  tạp hơn nhiều (f'' đổi dấu theo nhiều hướng) → khó huấn luyện hơn dù
  dùng chung gradient descent.
