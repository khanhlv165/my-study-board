# Lec 4: Product rule, Quotient rule, Chain rule — Tổng hợp (Feynman notes)

## 1. Product Rule — quy tắc nhân

**(u·v)' = u'·v + u·v'**

Đọc thành lời: "đạo hàm cái trước nhân cái sau, cộng cái trước nhân đạo hàm
cái sau."

**Trực giác:** hình chữ nhật với hai cạnh u(x), v(x) cùng thay đổi. Diện tích
tăng thêm khi x tăng Δx = u·dv (phần xanh) + v·du (phần cam) + du·dv (góc rất
nhỏ, biến mất khi lấy giới hạn — giống O(Δx²) ở Lec 1).

VD: f(x) = x²·sin x → f'(x) = 2x·sin x + x²·cos x

## 2. Quotient Rule — quy tắc chia

**(u/v)' = (u'·v − u·v') / v²**

Lưu ý thứ tự trừ: "đạo hàm tử nhân mẫu, TRỪ tử nhân đạo hàm mẫu", chia cho
mẫu bình phương.

**Ý tưởng:** u/v = u·v⁻¹, áp dụng product rule + chain rule cho (v⁻¹)'.

VD: f(x) = sin x / x → f'(x) = (cos x · x − sin x) / x²

## 3. Chain Rule — quy tắc dây chuyền (quan trọng nhất)

**dy/dx = dy/du · du/dx**

Dùng khi có hàm lồng trong hàm khác (y = f(g(x))).

**Trực giác:** dây chuyền bánh răng — tốc độ nhân dồn qua từng tầng. Bánh A
nhanh gấp 3 lần B, B nhanh gấp 2 lần C → A nhanh gấp 6 lần C.

**Quy tắc thực hành:** đạo hàm tầng ngoài (giữ nguyên tầng trong) × đạo hàm
tầng trong.

VD: y = sin(x²), đặt u = x² → dy/dx = cos(x²) · 2x

**Ý tưởng chứng minh (tóm tắt):** Δy/Δx = (Δy/Δu)·(Δu/Δx); khi Δx→0 thì Δu→0
(do u liên tục), nên cả hai thừa số cùng tiến về đạo hàm tương ứng.

## 4. Liên hệ AI/ML — Backpropagation

Mạng nơ-ron = chuỗi hàm lồng nhau nhiều tầng, giống dây chuyền bánh răng
nhưng có hàng chục/hàng trăm tầng:

Loss = L(f₃(f₂(f₁(x))))

**Backpropagation = áp dụng chain rule liên tiếp**, nhân dồn tốc độ thay đổi
từ tầng cuối ngược về tầng đầu để tính gradient cho từng tham số.

**Vanishing gradient:** nếu mỗi tầng làm gradient giảm đi một nửa, qua n
tầng gradient còn lại (1/2)ⁿ. Với 3 tầng: 1/8. Với 50 tầng: gần như 0 — các
tầng đầu mạng gần như không học được.

→ Đây là lý do thực tế đằng sau ReLU (thay sigmoid), residual/skip
connections, batch normalization — đều sinh ra từ việc kiểm soát chain rule
nhân dồn gradient qua nhiều tầng như thế nào.

Product rule, quotient rule cũng dùng khi tính đạo hàm loss/activation phức
tạp (softmax, attention), nhưng tần suất ít hơn chain rule nhiều.
