# Lec 1: Rate of Change — Tổng hợp (Feynman notes)

## 1. Bài toán gốc

Cho đường cong y = f(x) và điểm P trên đó. Tìm **độ dốc của tiếp tuyến** tại P
bằng công thức (analytically), không ước lượng bằng mắt.

Nhắc lại từ cấp 3: muốn tính độ dốc cần **hai điểm**:
m = Δy / Δx. Tiếp tuyến chỉ chạm đường cong tại một điểm → bị kẹt.

## 2. Mẹo: cát tuyến → tiếp tuyến

1. Lấy thêm điểm Q cách P một khoảng Δx.
2. Nối P, Q thành cát tuyến (secant line), tính được độ dốc:
   Δf/Δx = [f(x₀+Δx) − f(x₀)] / Δx
3. Cho Q trượt về P (Δx → 0). Cát tuyến tiến dần thành tiếp tuyến.

**Tiếp tuyến = giới hạn của cát tuyến khi Q → P.**
(Không phải "đường chỉ cắt đồ thị một lần" — đường cong có thể wiggly.)

## 3. Định nghĩa chính thức

> f'(x₀) = lim (Δx → 0) của [f(x₀+Δx) − f(x₀)] / Δx

- Biểu thức trong lim gọi là **difference quotient**.
- Δx không bao giờ = 0 thật sự (nếu = 0 thì Q trùng P, ra 0/0 vô nghĩa).
- Đây chính là chỗ cần khái niệm **limit** (học kỹ ở Lec 2).

## 4. Quy trình tính đạo hàm bằng định nghĩa (áp dụng mọi hàm)

1. Viết Δf = f(x₀+Δx) − f(x₀)
2. Biến đổi đại số (quy đồng, khai triển...) sao cho Δx ở tử và mẫu **triệt tiêu**
   → thoát dạng 0/0
3. Lấy lim Δx → 0 (thay Δx = 0 vào biểu thức đã rút gọn)
4. **Luôn kiểm tra lại bằng trực giác** (dấu, giá trị tại điểm đặc biệt, xu hướng)

### Ví dụ 1: f(x) = 1/x

Δf/Δx = −1 / [(x₀+Δx)·x₀]  →  **f'(x₀) = −1/x₀²**

Kiểm tra: luôn âm (đồ thị 1/x luôn đi xuống) ✓; càng xa gốc càng gần 0 (đồ thị
càng bẹt) ✓

### Ví dụ 2: f(x) = x²

Δf/Δx = (2x₀Δx + Δx²)/Δx = 2x₀ + Δx  →  **f'(x₀) = 2x₀**

Kiểm tra: f'(0)=0 (đáy parabol, tiếp tuyến ngang) ✓; f'(1)=2>0 (đi lên) ✓;
f'(−1)=−2<0 (đi xuống) ✓

### Tổng quát: f(x) = xⁿ (dùng nhị thức Newton)

(x+Δx)ⁿ = xⁿ + n·xⁿ⁻¹·Δx + O(Δx²)

O(Δx²) gồm các số hạng bậc ≥2 của Δx — tiến về 0 **nhanh hơn** Δx nên biến mất
sau khi chia cho Δx và lấy giới hạn.

→ **(xⁿ)' = n·xⁿ⁻¹**

## 5. Ký hiệu đạo hàm

- Newton: f'(x)
- Leibniz: df/dx (tiện cho chain rule sau này)

## 6. Ứng dụng: diện tích tam giác (tiếp tuyến của 1/x)

Tiếp tuyến của y=1/x tại (x₀, 1/x₀) cắt hai trục tạo tam giác vuông với gốc O.
Phần calculus duy nhất cần dùng là độ dốc f'(x₀) = −1/x₀² để viết phương trình
tiếp tuyến; phần còn lại là đại số/hình học.

Kết quả thú vị: **diện tích tam giác luôn bằng 2**, bất kể chọn x₀ nào (vì
y₀ = 1/x₀ triệt tiêu x₀ trong công thức diện tích).

## 7. Liên hệ AI/ML

| 18.01 | ML |
|---|---|
| f(x), đạo hàm f'(x) | Loss L(w), gradient L'(w) |
| Độ dốc dương → hàm tăng | L'(w)>0 → tăng w làm loss tăng → phải giảm w |
| Độ dốc âm → hàm giảm | L'(w)<0 → tăng w làm loss giảm → nên tăng w |

→ Gradient descent: **w_mới = w_cũ − η·L'(w_cũ)**. Dấu trừ mã hóa đúng quy luật
"luôn đi ngược dấu đạo hàm" để loss giảm dần — không cần if/else cho từng
trường hợp dấu.

## 8. Chỗ cần sửa so với ghi chú gốc

- "Formal Derivative Definition": phải là **delta_f** = f(x₀+Δx) − f(x₀),
  không phải delta_x = ...
