# Lec 13: Related Rates — Tổng hợp (Feynman notes)

## 1. Ý tưởng cốt lõi

Khi nhiều đại lượng cùng thay đổi theo thời gian và ràng buộc nhau bởi một
phương trình, biết tốc độ thay đổi của đại lượng này suy ra được tốc độ
của đại lượng kia. Chính là **implicit differentiation (Lec 5)**, chỉ khác:
biến độc lập luôn là thời gian t (ngầm hiểu), mọi đại lượng khác (x,y,V,r,
h...) đều là hàm của t.

## 2. Quy trình 4 bước

1. Vẽ hình, đặt tên các đại lượng đang thay đổi theo t
2. Viết phương trình liên hệ (Pythagore, thể tích, tam giác đồng dạng...)
3. Lấy đạo hàm hai vế theo t (chain rule — mỗi biến phụ thuộc t thì nhân
   thêm d(biến)/dt)
4. Thay số đã biết, giải ra đại lượng cần tìm

## 3. Ví dụ: cái thang trượt tường

Thang dài 5m, đầu dưới cách tường x, đầu trên cao y. Đầu dưới trượt ra với
dx/dt=1 m/s. Tìm dy/dt khi x=3.

**Bước 2:** x²+y²=25 (Pythagore, thang dài cố định)

**Bước 3:** 2x·(dx/dt) + 2y·(dy/dt) = 0

**Bước 4:** tại x=3 → y=4 (từ x²+y²=25). Thay vào:
2(3)(1) + 2(4)(dy/dt) = 0 → **dy/dt = −0.75 m/s** (âm = đang giảm)

**Ý nghĩa:** chỉ biết tốc độ MỘT đầu, nhờ ràng buộc hình học suy ra chính
xác tốc độ đầu kia.

### Tại sao |dy/dt| tăng vọt khi x→5 (thang gần nằm sát đất)

dy/dt = −(x/y)·(dx/dt). Khi x tăng → y=√(25−x²) giảm về 0 → tỉ số x/y tăng
vọt (tử tăng, mẫu→0) → |dy/dt|→∞ ngay trước khi thang chạm đất.

**Bài học:** kết quả "vận tốc vô hạn" cho thấy mô hình toán (giả định
dx/dt=1 không đổi mãi) đã vượt phạm vi hợp lý về vật lý thật (ma sát,
quán tính) — luôn cần tỉnh táo nhận ra giới hạn áp dụng của mô hình.

## 4. Ví dụ 2: bể nước hình nón (tóm tắt kỹ thuật)

Nước chảy vào bể nón với dV/dt biết trước. Bán kính mặt nước r tại độ cao
h bị ràng buộc bởi hình nón: r=(R/H)·h (R,H là bán kính/chiều cao bể, cố
định). Thay vào V=⅓πr²h để loại biến r, chỉ còn V theo h duy nhất — rồi
mới đạo hàm theo t. Kỹ thuật "dùng ràng buộc hình học để giảm số biến
xuống còn 1" giống hệt bài cái hộp ở Lec 12.

## 5. Liên hệ AI/ML

Related rates là phiên bản một-biến-thời-gian của **multivariable chain
rule** (18.02) — khi một đại lượng (loss) phụ thuộc nhiều biến qua một
"đồ thị tính toán" (computational graph). Trong backprop, khi một tham số
ảnh hưởng loss qua NHIỀU đường đi (weight sharing trong CNN, residual
connections), gradient tổng = cộng dồn đạo hàm theo từng đường — cùng tinh
thần "mọi đại lượng ràng buộc nhau qua biến chung, lấy đạo hàm rồi cộng
gộp" như bài thang và bài bể nước.
