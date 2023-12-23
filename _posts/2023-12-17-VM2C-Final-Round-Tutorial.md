---

title: VM2C Final Round Tutorial
thumbnail: https://github.com/SilverTD/SilverTD.github.io/assets/55396370/1379c360-d2f9-4e3f-8654-4a70c4624676
description: Ở bài toán VM2C vòng 2, chúng ta sẽ phải đi giải quyết vấn đề về sắp xếp lịch cho các nhân sự sao cho là công bằng và tối ưu nhất có thể...

---
# 1. Giới thiệu
## 1.1. Giới thiệu về kỳ thi
**Kỳ thi Mô hình hoá Toán học Việt Nam**  (Vietnam Mathematical Modelling Competition - viết tắt là VM2C) là kỳ thi mô hình hóa toán học lần đầu tiên được tổ chức ở Việt Nam, dựa theo mô hình tổ chức cuộc thi mô hình hóa uy tín trên thế giới.

Kỳ thi gồm 2 vòng. Ở mỗi vòng, thử thách của các đội là tìm ra giải pháp cho một vấn đề mở, thường thì không giống các bài tập về nhà hay dự án nhóm trên lớp học thông thường. Kỹ năng quản lý thời gian, làm việc nhóm, viết và trình bày báo cáo cũng quan trọng không kém khả năng tìm hiểu các kiến thức mới và tư duy ứng dụng vào thực tế.

Kỳ thi VM2C là một sân chơi bổ ích và thú vị, giúp các học sinh phát triển các kỹ năng cần thiết trong thực tế. Đội của mình rất vinh dự khi là một trong những đội đoạt huy chương đồng trong kỳ thi được tổ chức lần đầu tiên này.

## 1.2. Cảm nhận về kỳ thi
Kỳ thi này giúp mình có cảm giác như đang nhập vai thành một nhà khoa học thực thụ, phải tự tìm kiếm và nghiên cứu mọi thứ chứ không có sẵn công cụ nào cho mình.

Bên cạnh đó, do là toán mô hình nên không có một lời giải cụ thể nào, điều này cho phép chúng ta thỏa sức sáng tạo lời giải và tối ưu chúng.

Kỳ thi VM2C giúp mình cải thiện rất nhiều kỹ năng cần thiết trong thực tế, chẳng hạn như kỹ năng giải quyết vấn đề, quản lý thời gian, làm việc nhóm và thuyết trình. Mình tin rằng những kỹ năng này sẽ giúp ích rất nhiều trong tương lai.

# 2. Hướng giải quyết bài toán a vòng 2

> Do có giới hạn về thời gian, nên mình sẽ chỉ giải quyết bài toán a của vòng 2 (câu a trên dữ liệu 1 và dữ liệu 2).
 
> Đề vòng 2: [Đề thi](https://vm2c.viasm.edu.vn/images/VM2C%20-%20De%20thi%20Vong%20II.pdf "Đề thi")

## 2.1. Xử lý file lenh_san_xuat_Day_chuyen_?.txt
Đây là phần đã khiến mình không hoàn thành kịp phần thi của mình, mình đã quên mất file này khi làm bài thi. Về cơ bản là file cho bạn thời gian đóng và mở dây chuyền (dây chuyền không làm việc liên tục).

Đề bài cho ta biết trong một ngày có 3 ca:
+ Ca sáng: 6h - 14h.
+ Ca chiều: 14h - 22h.
+ Ca tối: 22h - 6h hôm sau.

```
Thoi_gian_bat_dau; Thoi_gian_ket_thuc
2023-06-01 08:00:00; 2023-06-02 04:00:00
2023-06-02 06:00:00; 2023-06-02 14:00:00
2023-06-02 22:00:00; 2023-06-03 06:00:00
2023-06-03 06:00:00; 2023-06-03 22:00:00
```

Với hướng làm của mình thì mình phải xử lý file đấy, và kiểm tra xem các ca nào sẽ hoạt động (hoạt động khi dây chuyền mở). Như với file dữ liệu ở trên thì dây chuyền mở cửa vào lúc ``2023-06-01 08:00:00`` và đóng cửa vào lúc ``2023-06-02 04:00:00``, từ dữ liệu đó thì ta biết được vào ngày ``2023-06-01`` sẽ có 3 ca là ca sáng, chiều và tối. Ta sẽ xử lý file ``lenh_san_xuat_Day_chuyen_1.txt`` như sau:

```
Ngày 1: có 3 ca sáng, chiều và tối 
Ngày 2: có 2 ca sáng và tối
Ngày 3: có 2 ca sáng và chiều
Ngày 4: có 3 ca sáng, chiều và tối
Ngày 5: có 1 ca chiều
```
Tuy nhiên để thuận tiện trong tính toán, ta sẽ biểu diễn lại dưới dạng ma trận $28 \times 3$ có biến nhị phân như sau:

$$
T_{28 \times 3} = \begin{pmatrix}
t_{1,1} & t_{1,2} & t_{1,3} \\
t_{2,1} & t_{2,2} & t_{2,3} \\
\vdots & \vdots & \vdots \\
t_{28,1} & t_{28,2} & t_{28,3}\\
\end{pmatrix}
$$

Tương ứng với 28 ngày và 3 ca mỗi ngày, ma trận có ý nghĩa:

$$
\begin{equation*}
t_{ij} = 
\begin{cases}
      1 & \text{nếu ca làm việc thứ j vào ngày i hoạt động} \\
      0 & \text{ngược lại}
\end{cases}
\ \ \ \ \ \ 1 \leq i \leq 28, \ 1 \leq j \leq 3
\end{equation*}
$$

Từ đó ta có thể thay thế dữ liệu đã xử lý thành một ma trận đơn giản và dễ hiểu hơn:

$$
T = \begin{pmatrix}
1 & 1 & 1\\  
1 & 0 & 1\\
1 & 1 & 0\\
1 & 1 & 1 \\
0 & 1 & 0 \\
 & \cdots & 
\end{pmatrix}
$$

Đến đây ta đã hoàn thành trong việc xử lý file ``lenh_san_xuat_Day_chuyen_1.txt`` thành một ma trận nhị phân giúp ta thuận lợi trong việc tính toán sau này. Việc xử lý file này khá quan trọng, vì nếu bất cẩn trong xử lý file thì những thuật toán của chúng ta cho dù hoạt động tốt nhưng vẫn sẽ cho ra kết quả không chính xác.

Ví dụ như trong ngày ``2023-06-01`` sẽ có 3 ca: sáng, chiều và tối nhưng bạn xử lý file chỉ còn mỗi 2 ca: sáng, chiều thì dẫn đến kết quả sẽ sai (vì thiếu mất ca tối).

Source code xử lý file này: [data_processing.py](https://github.com/SilverTD/PhysicsAndMath/blob/main/VM2C_Final/data_processing.py "data_processing.py")

File xử lý bằng tay để kiểm tra code hoạt động ổn: [processed_lenh_san_xuat_Day_chuyen_1.txt](https://github.com/SilverTD/PhysicsAndMath/blob/main/VM2C_Final/processed_lenh_san_xuat_Day_chuyen_1.txt "processed_lenh_san_xuat_Day_chuyen_1.txt")

## 2.2. Các biến số
Ta sẽ định nghĩa các biến số dùng trong tính toán như sau:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $X = \\{ x_{ijk} \\}$ là ma trận chứa các biến $x_{ijk}$ với ý nghĩa nhân sự $i$ được chọn làm ca thứ $j$ của dây chuyền $k$ hay không.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $B = \\{b_{ijk} \\}$ là ma trận chứa các biến $b_{ijk}$ với ý nghĩa nhân sự thứ $i$ có kĩ năng $j$ của dây chuyền $k$ hay không.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $D = \\{d_{i} \\}$ là ma trận chứa các biến $d_{i}$ với ý nghĩa tổng số ngày làm việc của nhân sự $i$ cho đến hiện tại.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $N = \\{n_{i} \\}$ là ma trận chứa các biến $n_{i}$ với ý nghĩa tổng số ca đêm làm việc của nhân sự $i$ cho đến hiện tại.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $W = \\{ w_{i} \\}$ là ma trận chứa các biến $w_{i}$ với ý nghĩa nhân sự thứ $i$ có được làm ca hiện tại hay không.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $R = \\{ r_{kj} \\}$ là ma trận chứa các biến $r_{kj}$ với ý nghĩa lượng nhân lực tối thiểu cần cho ca làm việc $j$ của dây chuyền $k$.
##  2.3. Các ràng buộc
Ta sẽ xét ngày thứ $z$ $\rightarrow$ ca làm việc thứ $j$ $\rightarrow$ dây chuyền thứ $k$:
1. Các nhân sự chỉ làm các ca có đúng kĩ năng của mình:

$$
\begin{aligned}
x_{ijk} \leq b_{ijk} \ \ \ \forall i, j, k \geq 0
\end{aligned} 
$$

2. Các nhân sự chỉ làm một kĩ năng duy nhất trong một ca trong ngày:

$$
\begin{aligned}
\sum\limits_{j}^{}x_{ijk} \leq 1 \ \ \ \forall i, k \geq 0
\end{aligned}
$$

3. Tổng nhân sự làm việc trong ca thứ $j$ (có kỹ năng $j$) tối thiểu là $r_{kj}$, ta có thêm biến $w_{i}$ nhằm đảm bảo các nhân sự chỉ làm một ca duy nhất trong ngày và các nhân sự làm ca đêm hôm trước sẽ không làm ca sáng hôm nay:

$$
\begin{aligned}
\sum\limits_{i}^{} \ (x_{ijk} * w_{i}) \geq r_{kj} \ \ \ \forall j, k \geq 0
\end{aligned} 
$$

4. Tổng số ngày làm việc của nhân sự không vượt quá 24 ngày:

$$
\begin{aligned}
\sum\limits_{i}^{} \ (x_{ijk} + d_{i}) \leq 24 \ \ \ \forall j, k \geq 0
\end{aligned} 
$$

##  2.4. Hàm mục tiêu
Mục tiêu mà chúng ta cần tối ưu đầu tiên là số lượng nhân sự tham gia làm việc luôn phải là nhỏ nhất:

$$
F_{1} = \sum\limits_{i, \ j}x_{ijk}
$$

Tiếp theo ta cần tối ưu độ công bằng giữa các nhân sự, điều này có nghĩa độ chênh lệch số ca làm việc giữa các nhân sự là nhỏ nhất có thể. Do ta đang xét từng ca trong từng ngày, nên mỗi lần xét ta sẽ luôn ưu tiên lựa chọn các nhân sự có số ca làm việc ít nhất:

$$
F_{2} = \sum\limits_{i, \ j} \ [x_{ijk} * d_{i} * C(i)]
$$

Tương tự với số ca đêm, ta cũng luôn lựa chọn các nhân sự có số ca đêm làm việc ít nhất:

$$
F_{3} = \sum\limits_{i, \ j} \ [x_{ijk} * n_{i} * C(i)]
$$

Với $C(i)$ ta định nghĩa như sau:

$$
\begin{equation*}
C(i) = 
\begin{cases}
      C & \text{nếu nhân sự i có nhiều hơn 1 kĩ năng} \\
      1 & \text{ngược lại}
\end{cases}
\end{equation*}
$$

Điều đó có nghĩa, ta sẽ ưu tiên lựa chọn các nhân sự có nhiều hơn một kĩ năng, như thế sẽ tránh trường hợp thiếu nhân sự của các xưởng khác.

Hàm mục tiêu của chúng ta lúc này sẽ là tổng các hàm cần tối ưu ở trên $F_1, F_2, F_3$:

$$
OP = F_1 + (1 - A) * F_2 + A * F_3
$$

Với $A$ được định nghĩa như sau:

$$
\begin{equation*}
A = 
\begin{cases}
      1 & \text{nếu ca hiện tại là ca đêm} \\
      0 & \text{ngược lại}
\end{cases}
\end{equation*}
$$

Hàm mục tiêu $OP$ càng nhỏ khi nhân sự được chọn có số ngày làm việc hoặc số ca đêm làm việc càng nhỏ.

## 2.5. Áp dụng mô hình
### 2.5.1 Dữ liệu 1
**Dữ liệu** 1 ý (a) với 17 nhân sự, tổng công là 330.

Sau khi áp dụng mô hình trên với bộ dữ liệu 1 thì ta thu được kết quả như đồ thị dưới đây. Về cơ bản đây là một kết quả khá tốt đối với một mô hình khá đơn giản như của chúng ta đã làm.

![image](https://github.com/SilverTD/SilverTD.github.io/assets/55396370/3cc719ec-0c96-40d4-a373-2e1b088a2924)
![image](https://github.com/SilverTD/SilverTD.github.io/assets/55396370/fd0dba9d-bad9-457d-a7c8-7f10ce10db54)

Ở đồ thị (1), ta thấy được $max = 23$ và $min = 16$:
- $max - min = 23 - 16 = 7$
- Trung bình: $\overline{x} \approx 19.41$
- Độ lệch chuẩn: $\sigma \approx 2.17$

Tương tự ở đồ thị (2), ta thấy được $max = 8$ và $min = 5$:
- $max - min = 8 - 5 = 3$
- Trung bình: $\overline{x} \approx 6.17$
- Độ lệch chuẩn: $\sigma \approx 0.98$

Từ các số liệu vừa tính toán ở trên, ta thấy được kết quả của chúng ta không hẳn là quá tệ. Các dữ liệu phân tán có thể xem là khá đồng đều.

Đặc biệt dễ thấy ở ca đêm, với độ lệch chuẩn chỉ $0.98$. Điều này cho thấy các ca đêm rất công bằng.

### 2.5.2 Dữ liệu 2
**Dữ liệu** 2 ý (a) với 55 nhân sự, tổng công là 1116.

Dưới đây là đồ thị của kết quả:

![image](https://github.com/SilverTD/SilverTD.github.io/assets/55396370/075e9dcd-952f-4914-9323-9076bd09f703)
![image](https://github.com/SilverTD/SilverTD.github.io/assets/55396370/0fa0289e-6dd0-4372-a77b-d1c82c85b30d)

Ở đồ thị (1), ta thấy được $max = 24$ và $min = 17$:
- $max - min = 24 - 17 = 7$
- Trung bình: $\overline{x} \approx 20.29$
- Độ lệch chuẩn: $\sigma \approx 2.22$

Tương tự ở đồ thị (2), ta thấy được $max = 9$ và $min = 1$:
- $max - min = 9 - 1 = 8$
- Trung bình: $\overline{x} \approx 6.49$
- Độ lệch chuẩn: $\sigma \approx 1.70$

Từ các số liệu chúng ta vừa tính toán, ta thấy được mô hình đơn giản của chúng ta đã cho ra kết quả rất tốt và tối ưu. Độ lệch chuẩn ở đồ thị (1) là $2.22$ và $max - min = 7$, tương tự ở đồ thị (2) độ lệch chuẩn là $1.70$ và $max - min = 8$. Kết quả này là rất tốt.

Tuy nhiên đó chưa phải là kết quả tốt nhất mà mô hình có thể đạt được. Từ đề bài "mỗi nhân sự được phép làm tối đa 24 ngày trong 4 tuần", điều đó có nghĩa mỗi nhân sự cũng có thể làm tối đa $22$ ngày và nó không vi phạm đề bài.

Do đó ta có thể giảm số ngày tối đa từ $24 \rightarrow 22$, điều này giúp sự chênh lệch các ca làm việc giữa các nhân sự giảm xuống rất nhiều. Sau khi áp dụng, bên dưới là đồ thị của kết quả:

![image](https://github.com/SilverTD/SilverTD.github.io/assets/55396370/61aefb29-9057-4547-bca9-a52bff886933)
![image](https://github.com/SilverTD/SilverTD.github.io/assets/55396370/01d680af-eb01-49f8-8468-0d90b5764433)

Độ lệch chuẩn lúc này là $1.49$ đối với các ca làm việc và $1.70$ đối với các ca đêm làm việc, $max - min = 5$ đối với các ca làm việc và $max - min = 8$ đối với các ca đêm làm việc. Ta thấy kết quả đã cải thiện và tốt hơn rõ rệt.

Toàn bộ source code của mình: [VM2C_Final](https://github.com/SilverTD/Stuffs/tree/main/VM2C_Final "VM2C Final")

Mọi ý tưởng và hướng đi mình vừa trình bày ở bên trên, đều là những ý tưởng, suy nghĩ của mình khi đang làm bài thi ở viện nghiên cứu <b>VIASM</b>: [VM2C_Vong2](https://github.com/SilverTD/Stuffs/tree/main/VM2C_Vong2 "VM2C Vong2")

## 2.6. Nhận xét
### 2.6.1. Ưu điểm
Đây vốn dĩ là một mô hình khá đơn sơ, đơn giản nên rất dễ hiểu, bên cạnh đó những thứ chúng ta làm không thực sự quá nặng toán. Cơ bản là chỉ làm theo những gì đề cho.

Code khi được triển khai cũng không quá dài, thời gian chạy cũng khá ngắn $7.46$ (s) đối với bộ dữ liệu (1) và $43.76$ (s) đối với bộ dữ liệu (2).

Kết quả mà chúng ta vừa tìm được trông khá ổn.

### 2.6.2. Nhược điểm
Mô hình còn đơn giản, do đó chưa tối ưu. Đồng thời mô hình đã bỏ qua những vấn đề thực tế khác.

Tuy nhìn mô hình trên đơn giản, nhưng việc triển khai nó bằng code thì hơi khó khăn. Đặc biệt là biến $w_i$, ta phải xét các trường hợp tổng quát để biến $w_i$ luôn cho ra các kết quả đúng và chính xác.

### 2.6.3. Cải thiện
Mô hình có thể cải thiện kết quả lên rất nhiều nếu ta giảm số ngày tối đa làm việc xuống (điều này không vi phạm đề bài).

Mô hình của chúng ta là đang xét từng ca, do đó mỗi lần xét ta sẽ ưu tiên lựa chọn các nhân sự có số ca làm ít. Chúng ta hoàn toàn có thể thử thay đổi hàm mục tiêu, như đội đến từ trường <b>chuyên Lê Hồng Phong</b> thì chọn tối ưu độ lệch chuẩn ($max - min$).

Hoặc như đội đến từ trường <b>chuyên Khoa Học Tự Nhiên</b> đã cho thêm vào "Độ bất mãn" để tối ưu kết quả, đây hoàn toàn là một ý tưởng khá hay và sáng tạo. Chúng ta có thể học hỏi theo cách làm ấy.

Hay như đội đến từ trường <b>chuyên Lương Văn Chánh</b> thì dùng thuật toán tham lam để giải quyết bài toán này.

**Lưu ý:** Trong quá trình làm việc, sau khi mô hình đã cho ra kết quả thì ta cần phải tạo một <b>Checker</b> để kiểm tra lại kết quả, xem kết quả đã thỏa mãn các ràng buộc hay chưa ? Vì cho dù kết quả có tối ưu, độ lệch chuẩn chỉ $0.1$ nhưng vi phạm điều kiện thì mọi thứ đều vô nghĩa.

# 3. Tổng kết
Do không có nhiều thời gian, nên tạm thời mình chỉ viết bài đăng giải quyết câu a. Nhưng nếu bạn đã đọc bài viết của mình, các bạn sẽ nắm được những gì bài toán yêu cầu và hướng đi, từ đó hình thành tư duy để giải quyết nốt các vấn đề còn lại của bài toán.

Như ta thấy, mỗi đội đều có một cách riêng để giải quyết bài toán này. Đó chính là cái hay của toán mô hình, "không có một lời giải cụ thể duy nhất", vì vậy các bạn có thể tự tạo ra nhiều mô hình khác nhau và từ đó so sánh kết quả của chúng để chọn ra mô hình tốt nhất.

Đây vốn dĩ là một cuộc thi khá hay phải không ? Nó hoàn toàn giúp chúng ta rèn luyện được khá nhiều kĩ năng có ích trong thực tế, và đây hoàn toàn là một cuộc thi xứng đáng để chúng ta trải nghiệm ít nhất một lần.

# 4. Một số hình ảnh
![prize](https://github.com/SilverTD/Stuffs/assets/55396370/e74d2ecb-465e-4467-b1b2-1a8f859407aa)
![prize2](https://github.com/SilverTD/Stuffs/assets/55396370/506fddfb-20cb-4f91-a4f3-52e1275d1f7a)
![vm2c](https://github.com/SilverTD/Stuffs/assets/55396370/910ab01c-cc78-47c1-a7a2-da9a1b308b2a)


# 5. Tài liệu tham khảo
```
- Bài làm của đội trường chuyên KHTN: https://github.com/hsgs-wtg/Final-Round
- Tài liệu của VM2C: https://vm2c.viasm.edu.vn/
```
