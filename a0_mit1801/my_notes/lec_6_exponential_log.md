# Lec 6: Exponential and Logarithm Functions — Tổng hợp (Feynman notes)

## 1. Vì sao cần một hàm "tự tái tạo"

Nhiều hiện tượng (lãi kép có nhập gốc, tăng trưởng dân số, phân rã phóng xạ)
có chung tính chất: **tốc độ thay đổi tỉ lệ thuận với giá trị hiện tại**.

Viết bằng đạo hàm: **dy/dx = k·y**. Câu hỏi: hàm nào có (f)' = f (trường hợp
k=1)?

### Vì sao cần giải "f'=f" (chưa rõ hoàn toàn — cần ôn lại)

Ví dụ: video lan truyền, 10 người xem lúc 0h, mỗi giờ số người xem mới tăng
thêm = đúng số người đang xem (quy luật tức thời, liên tục — không phải
nhảy cóc từng giờ). Muốn biết chính xác số người xem tại MỘT THỜI ĐIỂM BẤT
KỲ (vd 2h30) mà không phải lặp hàng trăm bước tính tay theo từng phút, cần
một "công thức tắt" f(x): nhập x (giờ) vào là ra ngay kết quả.

Công thức đó phải tôn trọng đúng quy luật gốc: tại MỌI thời điểm x, tốc độ
tăng tức thời f'(x) phải luôn bằng đúng số lượng hiện có f(x) → điều kiện
**f'(x) = f(x)**.

Giải ra f(x) = C·eˣ (C = giá trị ban đầu) cho một "máy tính bỏ túi" dùng
được ngay, không cần lặp bước tính tay nào.

Nếu tốc độ tăng chỉ bằng k lần số hiện có (k≠1, vd lan truyền chậm hơn với
k=0.5): công thức tổng quát là f(x) = C·e^(kx) — suy ra từ "f'=f" bằng cách
co giãn trục x (không cần giải lại từ đầu cho từng k).

*(Ghi chú cá nhân: phần này vẫn còn hơi trừu tượng, cần ôn lại kỹ hơn sau.)*

## 2. Định nghĩa số e

**e ≈ 2.71828...** là cơ số duy nhất sao cho **(eˣ)' = eˣ** — đồ thị có độ
dốc tiếp tuyến tại mỗi điểm luôn bằng đúng chiều cao tại điểm đó.

## 3. Nguồn gốc: lãi kép liên tục (trong 1 năm)

Gửi tiền lãi suất 100%/năm, nhập gốc n lần TRONG CÙNG 1 NĂM (mỗi lần lãi
suất 1/n): số tiền cuối năm = (1+1/n)ⁿ lần số gốc.

**lim(n→∞) (1+1/n)ⁿ = e**

Hai lực kéo co: nhập gốc nhiều lần hơn → có lợi; nhưng mỗi lần lãi suất
nhỏ hơn → bất lợi. Lợi ích thêm vào càng nhỏ dần khi n tăng → giá trị
"bão hòa" ở e thay vì tăng vô hạn.

Lưu ý: n là số lần chia lãi TRONG 1 năm, không phải số năm gửi. Nếu gửi t
năm với lãi liên tục: số tiền cuối = (gốc)×e^t — tăng không giới hạn theo t.
Mốc e chỉ riêng cho t=1.

## 4. Vì sao chính e, không phải số khác

Từ định nghĩa đạo hàm cho hàm aˣ bất kỳ:

(aˣ)' = aˣ · lim(h→0) (aʰ−1)/h = aˣ · C(a)

**C(a) = ln(a)** với mọi a (một định nghĩa khác của logarit tự nhiên — kiểm
chứng bằng số: a=2 → C(2)≈0.693=ln2; a=3 → C(3)≈1.099=ln3).

Vì **ln(e)=1 theo đúng định nghĩa e là hàm ngược của ln**, nên a=e là
trường hợp duy nhất C(a)=1 → **(eˣ)' = eˣ**.

(aˣ)' tăng dần theo a: a=2 → C(a)<1 (đạo hàm nhỏ hơn chính hàm); a=3 →
C(a)>1 (đạo hàm lớn hơn chính hàm); e là điểm cân bằng chính xác ở giữa.

## 5. (ln x)' = 1/x — dùng implicit differentiation (Lec 5)

Đặt y=ln(x) ⟺ eʸ=x. Đạo hàm 2 vế: eʸ·dy/dx=1 → dy/dx=1/eʸ=**1/x**

## 6. Hàm mũ cơ số bất kỳ

aˣ = e^(x·ln a) (chain rule) → **(aˣ)' = aˣ·ln(a)**

Khi a=e: ln(e)=1 → rút gọn về (eˣ)'=eˣ, khớp định nghĩa ban đầu.

## 7. Liên hệ AI/ML

- **Sigmoid** σ(x)=1/(1+e⁻ˣ): σ'(x) = σ(x)·(1−σ(x)) — tự tái tạo, không cần
  tính lại từ đầu khi backprop vì σ(x) đã có sẵn từ forward pass.
- **Softmax**: softmax(xᵢ) = e^xᵢ / Σⱼe^xⱼ — dùng eˣ để chuyển dãy số thành
  phân phối xác suất.
- **Cross-entropy loss**: L = −Σy·ln(ŷ) — dùng (ln x)'=1/x khi backprop.
- **Log-likelihood**: dùng ln để biến phép nhân xác suất (dễ underflow)
  thành phép cộng log-xác suất, ổn định hơn về số học.
