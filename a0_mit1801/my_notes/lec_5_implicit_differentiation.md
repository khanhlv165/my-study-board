# Lec 5: Implicit Differentiation — Tổng hợp (Feynman notes)

## 1. Vấn đề

Không phải phương trình nào cũng giải được y = f(x) tường minh. VD đường
tròn: x² + y² = 25 (giải ra y = ±√(25−x²) vướng dấu ±, phức tạp hơn thì có
khi không giải được).

## 2. Kỹ thuật: lấy đạo hàm hai vế, coi y là hàm ẩn của x

Mỗi khi gặp y trong phương trình, áp dụng **chain rule** (vì y là hàm của x):

d/dx(y²) = 2y · dy/dx

### Ví dụ: đường tròn x² + y² = 25

2x + 2y·(dy/dx) = 0  →  **dy/dx = −x/y**

Không cần giải y tường minh vẫn tính được độ dốc tiếp tuyến tại điểm bất kỳ.
(Kiểm chứng hình học: tiếp tuyến luôn vuông góc bán kính OP.)

## 3. Ứng dụng chính: đạo hàm của hàm ngược (arctan, arcsin, arccos)

**Khuôn mẫu chung 3 bước:**
1. Viết lại dưới dạng phương trình ẩn (VD: y=arctan x ⟺ tan y = x)
2. Lấy đạo hàm hai vế bằng chain rule
3. Dùng đồng nhất thức lượng giác để thay biến trung gian y trở lại x

### (arctan x)'

Đặt y = arctan(x) ⟺ tan(y) = x. Đạo hàm 2 vế:

sec²(y)·dy/dx = 1 → dy/dx = 1/sec²(y)

sec(y) = 1/cos(y) (nghịch đảo cos). Đồng nhất thức: sec²(y) = 1+tan²(y) = 1+x²

**(arctan x)' = 1/(1+x²)**

### (arcsin x)'

Đặt y = arcsin(x) ⟺ sin(y) = x. Đạo hàm 2 vế: cos(y)·dy/dx = 1.
cos(y) = √(1−sin²y) = √(1−x²) (dương vì arcsin có range [−π/2, π/2], cos
luôn dương trên đoạn này)

**(arcsin x)' = 1/√(1−x²)**

### (arccos x)' — bài tập tự chứng minh

Đặt y = arccos(x) ⟺ cos(y) = x. Đạo hàm 2 vế:

−sin(y)·dy/dx = 1 → dy/dx = −1/sin(y)

Đồng nhất thức: sin²(y)+cos²(y)=1 → sin(y) = ±√(1−cos²y) = ±√(1−x²)

**Chọn dấu:** arccos(x) có range y∈[0,π] (nửa trên đường tròn lượng giác) →
sin(y) luôn **dương** trong khoảng này → chọn dấu +:

sin(y) = +√(1−x²)

**(arccos x)' = −1/√(1−x²)**

**Kiểm tra chéo:** arcsin(x) + arccos(x) = π/2 (hằng số) với mọi x → đạo hàm
hai vế phải triệt tiêu → (arcsin x)' = −(arccos x)'. Khớp với hai công thức
trên (chỉ khác đúng một dấu trừ) — cách kiểm tra nhanh không cần tính lại.

## 4. Liên hệ AI/ML

- Hàm **sigmoid** σ(x)=1/(1+e⁻ˣ) có hàm ngược là **logit** (log-odds):
  logit(p)=ln(p/(1−p)). Implicit differentiation là công cụ để tính đạo hàm
  của các hàm ngược kiểu này khi cần.
- Trong **constrained optimization** (bài toán có ràng buộc g(x,y)=0, như
  SVM, Lagrange multipliers), implicit differentiation là cách chuẩn để tính
  độ nhạy của nghiệm tối ưu khi ràng buộc thay đổi nhẹ.
