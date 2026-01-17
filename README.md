# Lý thuyết Mạng Tính Toán (Computational Network)

Assignment này tổng hợp cơ sở lý thuyết để xây dựng chương trình giải bài tập tự động dựa trên mô hình **Mạng tính toán**, bao gồm các định nghĩa, cấu trúc luật và phương pháp suy diễn lời giải.

## 1. Định nghĩa Mạng tính toán
Mạng tính toán là một mô hình biểu diễn tri thức được xác định bởi cặp (M, R).

### Các thành phần chính
* **Tập biến (M):** Là tập hợp các đại lượng hoặc biến số trong bài toán.
    `M = {x1, x2, ..., xn}`
* **Tập luật (R):** Là tập hợp các mối quan hệ dẫn xuất giữa các biến.
    `R = {r1, r2, ..., rm}`

### Cấu trúc của một Luật (r)
Mỗi luật r thuộc R bao gồm hai phần:
1.  **Đẳng thức:** Biểu diễn mối quan hệ toán học giữa các biến trong M.
2.  **Luật dẫn (Inference rule):** Xác định khả năng suy diễn của luật, có dạng:
    `u(r) -> v(r)`
    *Trong đó:*
    * `u(r)`: Tập các biến đầu vào cần biết.
    * `v(r)`: Tập các biến có thể tính được từ u(r).

---

## 2. Mô hình Bài toán
Một bài toán cụ thể trên mạng tính toán được biểu diễn bởi cặp (H, Goal).

* **Giả thiết (H):** Tập hợp các biến đã biết giá trị ban đầu.
* **Mục tiêu (Goal):** Yêu cầu của bài toán cần giải quyết.

### Cấu trúc Mục tiêu (Goal)
Goal được định nghĩa dưới dạng cấu trúc: `("KEYWORD", ListObj)`.

* **KEYWORD:** Nhận các giá trị hành động như "Tính", "Chứng Minh", "Giải", hoặc "Tìm".
* **ListObj:** Danh sách các biến trong M hoặc cấu trúc mở rộng.
    * *Ví dụ:* `Goal = ["Tinh", var_a, var_b]`
    * *Trường hợp "Tìm":* `ListObj = ["condition_key", x, y]` (Tìm x để y thỏa mãn điều kiện "condition_key").

---

## 3. Cơ chế Suy luận và Lời giải

### Quá trình suy diễn
Với một tập biến đã biết A thuộc M và một luật r thuộc R, tập hợp các sự kiện suy luận được từ A khi áp dụng luật r là:
`r(A) = A U M(r)`
*(Tập A hợp với các biến tính được từ luật r)*

### Định nghĩa Lời giải (S)
Cho danh sách các luật `S = [r1, r2, ..., rk]`. Khi đó tập biến suy diễn được là:
`S(A) = rk(rk-1(...r2(r1(A))...))`

* Danh sách S được gọi là **lời giải** của bài toán (H, Goal) nếu kết quả `S(H)` thỏa mãn Goal.
* **Lời giải tốt:** Là lời giải S mà không tồn tại tập con S' nào của S cũng là lời giải của bài toán (tức là không chứa các bước tính toán dư thừa).
* Bài toán được gọi là **giải được** nếu tồn tại ít nhất một lời giải.

---

## 4. Các miền tri thức áp dụng (Bài tập thực hành)

### Bài tập 1: Giải Tam giác
* **Mục tiêu:** Xác định các yếu tố tam giác còn thiếu từ dữ liệu cho trước.
* **Tập biến (M):**
    * Cạnh: a, b, c
    * Góc: A, B, C
    * Đường cao: ha, hb, hc
    * Khác: Diện tích (S), nửa chu vi (p)...
* **Tập luật (R):** Các công thức lượng giác, định lý Cosin, định lý Sin, công thức Heron...

### Bài tập 2: Hình học phẳng
Cài đặt tri thức và giải quyết bài toán cho:
1.  **Hình vuông & Hình thang vuông.**
2.  **Đa giác đều n cạnh:**
    * *Thuộc tính:* Số cạnh (n), chiều dài cạnh (a), góc ở tâm (beta), Diện tích (S), Chu vi (P), Bán kính ngoại tiếp (R).
    * *Luật:* Các công thức liên hệ toán học giữa các thuộc tính trên.

### Bài tập 3: Mạch điện một chiều
* **Phạm vi:** Mạch điện đơn giản chỉ gồm một điện trở.
* **Tập biến (M):**
    * Hiệu điện thế (U), Cường độ dòng điện (I), Điện trở (R).
    * Công suất (P), Tiết diện dây dẫn (S), Đường kính dây (d), Điện trở suất (rho).
* **Tập luật (R):**
    * Định luật Ohm: `U = I * R`
    * Công thức điện trở: `R = rho * (l / S)`
    * Công thức công suất: `P = U * I`
