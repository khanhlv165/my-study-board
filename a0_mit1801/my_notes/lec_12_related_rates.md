# Lec 11: Critical Points và Max/Min — Tổng hợp (Feynman notes)

## 1. Critical point là gì

Điểm x mà **f'(x)=0** (tiếp tuyến nằm ngang) hoặc **f'(x) không xác định**
(góc nhọn, đứt đoạn).

**Lý do chỉ cần xét các điểm này:** nếu f'(x)≠0, hàm còn đang tăng/giảm →
chưa thể là đỉnh/đáy. Nên local max/min BẮT BUỘC xảy ra tại critical point.

**Lưu ý:** f'=0 là điều kiện CẦN, không phải ĐỦ. Có thể là saddle point
(VD x³ tại x=0: f'(0)=0 nhưng chỉ "khựng" rồi tiếp tục tăng, không phải
đỉnh/đáy).

## 2. Hai cách phân loại critical point

### First derivative test (xét đổi dấu f' hai bên)

- Dấu + → − (tăng rồi giảm) → local max
- Dấu − → + (giảm rồi tăng) → local min
- Dấu không đổi → không phải max/min (điểm khựng tạm)

### Second derivative test (nhanh hơn, không cần xét 2 bên)

- f''(x₀)>0 → concave up → **local min**
- f''(x₀)<0 → concave down → **local max**
- f''(x₀)=0 → không kết luận được, quay lại dùng first derivative test

## 3. Ví dụ: f(x) = x³ − 3x²

f'(x)=3x²−6x=3x(x−2) → critical points x=0, x=2

f''(x)=6x−6: f''(0)=−6<0 → x=0 local max (f(0)=0)
f''(2)=6>0 → x=2 local min (f(2)=−4)

## 4. Local max/min ≠ Global max/min — phải kiểm tra thêm 2 thứ

Trên khoảng [a,b], global max/min có thể nằm ở:
1. Critical points (như trên)
2. **Hai đầu mút a, b** (dễ bị bỏ sót!)
3. Điểm hàm không xác định/gián đoạn (nếu có)

### Ví dụ: f(x)=x³−3x² trên [−1,4]

| Điểm | Loại | f(x) |
|---|---|---|
| x=−1 | đầu mút | −4 |
| x=0 | local max | 0 |
| x=2 | local min | −4 |
| x=4 | đầu mút | 16 |

**Global max = 16 tại x=4 (đầu mút, không phải critical point!)**
**Global min = −4 (cả x=−1 và x=2)**

### Bài tập: h(x)=x² trên [1,3]

Critical point x=0 KHÔNG thuộc [1,3] → bỏ qua, không cần xét.
h'(x)=2x > 0 trên toàn đoạn [1,3] → hàm tăng đơn điệu suốt đoạn → global
min/max chỉ có thể ở 2 đầu mút: **global min tại x=1 (y=1), global max tại
x=3 (y=9)**.

## 5. Liên hệ AI/ML

Gradient descent dừng khi gradient≈0 → đã tìm được một critical point,
nhưng KHÔNG đảm bảo đó là điểm tối ưu tốt nhất — có thể là local min
(chấp nhận được) hoặc **saddle point** (cần kiểm tra thêm, với nhiều chiều
dùng ma trận Hessian thay cho f'').

Không gian tham số deep learning có hàng triệu chiều → kiểm tra "đầu mút"
và mọi critical point là bất khả thi → không kỳ vọng global min tuyệt đối.
Các kỹ thuật thực tế để tránh kẹt ở local min/saddle point xấu: random
restart, learning rate schedule, momentum.
