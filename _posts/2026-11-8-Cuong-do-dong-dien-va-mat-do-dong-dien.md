---
title: Cường độ dòng điện và mật độ dòng điện (8/11/2026)
description: Cường độ dòng điện và mật độ dòng điện
---
Xét tại một nút có $\vec{j}_1, \vec{j}_2$ đi vào nút và $\vec{j}_3$ đi ra khỏi nút. Thông thường theo định luật bảo toàn điện tích hay định luật Kirchhoff về nút ta có $I_1 + I_2 = I_3$, vì rằng cường độ dòng điện là đại lượng vô hướng dẫn đến phép cộng là phép cộng đại số. Thế nếu ta xét vector mật độ dòng điện thì sao? Tại nút thì $\vec{j}_1 + \vec{j}_2$ sẽ như nào? Nó có bằng với $\vec{j}_3$ không?

Rõ ràng $\vec{j}_1 + \vec{j}_2 \neq \vec{j}_3$, tại sao lại như thế? Theo mình nghĩ rằng thật ra không hề có sự chồng chập vector mật độ dòng điện ở đây, tức không hề có $\vec{j}_1 + \vec{j}_2$ được. Theo lối suy nghĩ của mình nếu xét mô hình vi mô $\vec{j}_1, \vec{j}_2, \vec{j}_3$ đều là chỉ cùng một đại lượng là $\vec{j}$ - mật độ dòng điện tổng quát trong mạch điện.

Chi tiết hơn ta biết rằng $\vec{j} = \sigma \vec{E}$, trong mạch điện sẽ xuất hiện một trường tĩnh điện $\vec{E}$ và ta có $\vec{j} \propto \vec{E}$. Do đó không hề có mật độ dòng điện khác nhau $\vec{j}_1, \vec{j}_2, \vec{j}_3$ nào cả, chúng đều là $\vec{j} = \sigma\vec{E}$. Nên nếu ta xét chồng chập 2 vector mật độ dòng $\vec{j}_1, \vec{j}_2$ thì không đúng lắm.

Thế còn $I_1 + I_2 = I_3$ thì sao? Vốn dĩ cường độ dòng điện $I$ là một hệ quả của $\vec{j}$. Ta có định luật bảo toàn điện tích cho hệ đạt trạng thái cân bằng là $\oint \vec{j} \cdot d\vec{S} = 0$, chọn mặt Gauss kín bất kì bao quanh nút và khai triển chi tiết ra:

$$
\begin{aligned}
& \vec{j}(\vec{r}_1)\cdot \vec{S}_1 + \vec{j}(\vec{r}_2)\cdot \vec{S}_2 + \vec{j}(\vec{r}_3)\cdot \vec{S}_3 = 0 \\
\implies & j_1 S_1 + j_2 S_2 - j_3 S_3 = 0 \\
\implies & j_1 S_1 + j_2 S_2 = j_3 S_3
\end{aligned}
$$

Đặt $I_1 = j_1S_1, \ I_2 = j_2S_2, \ I_3 = j_3S_3$ là các **cường độ dòng điện** (thông lượng của vector mật độ dòng điện) trong các nhánh, chúng là đại lượng vô hướng. Cuối cùng ta thu được định luật Kirchhoff cho nút:

$$
I_1 + I_2 = I_3
$$

Phép chồng chập mật độ dòng điện được thực hiện khi có nhiều thành phần mật độ dòng điện cùng đóng góp tại một điểm trong không gian. Các thành phần này được cộng vector để xác định mật độ dòng điện tổng tại điểm đó. Ngược lại, các vector mật độ dòng điện tại những vị trí khác nhau chỉ là những giá trị khác nhau của cùng một trường vector, không phải các thành phần cần chồng chập với nhau.

Ví dụ: Ta có một trường tĩnh điện $\vec{E} = \vec{E}_1 + \vec{E}_2$, thì vector mật độ dòng tổng quát lúc này là $\vec{j} = \sigma\vec{E}$, ta thấy rằng vector mật độ dòng tổng quát này là chồng chập của 2 thành phần khác nhau:

$$
\vec{j} = \sigma\vec{E} = \sigma(\vec{E}_1 + \vec{E}_2) = \sigma\vec{E}_1 + \sigma\vec{E}_2 = \vec{j}_1 + \vec{j}_2
$$

Còn nếu trong ví dụ 3 nhánh tại 1 nút:

$$
\begin{aligned}
\vec{j}_1 = \vec{j}(\vec{r}_1) \\
\vec{j}_2 = \vec{j}(\vec{r}_2) \\
\vec{j}_3 = \vec{j}(\vec{r}_3) \\
\end{aligned}
$$

Cả 3 vector này là giá trị của vector tổng, không phải là 1 thành phần nào đó của $\vec{j}$. Do đó không thể chồng chập.
