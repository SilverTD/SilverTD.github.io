---

title: Note về toán cho lượng tử - Shankar (5/11/2026)
description: Note về toán cho lượng tử - Shankar
---
# Bra và Ket
Vector được gọi là ket và được kí hiệu như sau: $\ket{V}$. Tất nhiên các vector này lập nên không gian vector và thỏa mãn 8 tiên đề.
Một dạng tuyến tính được kí hiệu là $\bra{W}$, vì nó nhận vào một vector và trả về một đại lượng vô hướng:

$$
\braket{W|V} \in \mathbb{F}
$$

Ta gọi $\braket{W|V}$ là tích vô hướng giữa 2 vector $\ket{W}, \ket{V}$. Ta có tính chất quan trọng sau của tích vô hướng (antilinear):

$$
\braket{W|V} = \braket{V|W}^*
$$

Trong đó $*$ là phép lấy liên hợp phức.

Giả sử ta có các vector sau đối với một cơ sở trực chuẩn nào đó $(\ket{1}, \ket{2}, \dots, \ket{n})$:

$$
\ket{V} = \sum_i v_i \ket{i}, \ \ \ket{W} = \sum_i w_i \ket{i}
$$

$$
\implies \braket{V|W} = \braket{V|\sum_i w_i \ket{i}} = \sum_i w_i \braket{V|i} = \sum_i w_i \braket{\sum_j v_j \ket{j}|i}
$$

Trong đó ta sử dụng tính chất trên:

$$
\braket{V|W} = \sum_i w_i \braket{i|\sum_j v_j \ket{j}}^* = \sum_i \sum_j w_i v_j^* \braket{i|j}^* = \sum_i \sum_j w_i v_j^* \braket{j|i}
$$

Dễ thấy $\braket{j|i} = \delta_{ji} \implies \braket{V|W} = \sum_i v_i^*w_i$

Ta nhân vô hướng $\bra{j}$ vào $\ket{V}$ và có được:

$$
\braket{j|V} = \braket{j|\sum_i v_i \ket{i}} = v_j
$$

Vậy ta có thể phân tích vector $\ket{V}$ lại như sau:

$$
\ket{V} = \sum_i \ket{i} \braket{i|V}
$$

Ta kí hiệu:

$$
\mathbf{I} = \sum_i \ket{i}\bra{i}
$$

được gọi là hệ đầy đủ.

# Các toán tử Hermitian, Anti-Hermitian, và Unitary
Toán tử là Hermitian nếu $\Omega^\dagger = \Omega$.
Toán tử là Anti-Hermitian nếu $\Omega^\dagger = -\Omega$
Có một sự tương tự giữa các toán tử với số phức. Các số phức luôn có thể được thành tích thành tổng của 2 phần thực và phần ảo như sau:

$$
a = \frac{a + a^*}{2} + \frac{a - a^*}{2}
$$

Thì tương tự, ta luôn có thể phân tích một toán tử thành tổng của 2 phần Hermitian và Anti-Hermitian như sau:

$$
\Omega = \frac{\Omega + \Omega^\dagger}{2} + \frac{\Omega - \Omega^\dagger}{2}
$$

Toán tử là Unitary nếu $U U^\dagger = U^\dagger U = I$

**Định lý 7:** Toán tử Unitary bảo toàn tích vô hướng giữa các vector
**Chứng minh:** Giả sử ta có $\ket{V_1'} = U\ket{V_1}, \ \ket{V_2'} = U\ket{V_2}$
Ta xét tích vô hướng sau:

$$
\braket{V_2'|V_1'} = \braket{UV_2|UV_1} = \braket{V_2|U^\dagger U|V_1} = \braket{V_2|V_1}
$$

**Bài tập 1.6.4:** Chứng minh định thức của một Unitary là một số phức có chuẩn bằng 1
Ta có $UU^\dagger = I \implies \det(UU^\dagger) = \det(U)\det(U^\dagger) = \det(I) = 1$. Mặt khác ta có $\det(U^\dagger) = \det(U)^* \implies \det(U)\det(U^\dagger) = \det(U)\det(U)^* = 1$. Vậy $\det(U)$ là một số phức có chuẩn bằng 1.

# Active và Passive transformations


# Eigenvalue và Eigenvector
**Định lý 9:** Giá trị riêng của một toán tử Hermitian là các giá trị thực
**Chứng minh:** Giả sử $\omega$ là giá trị riêng và $\ket{\omega}$ là vector riêng tương ứng.
Ta có:

$$
\Omega \ket{\omega} = \omega \ket{\omega}
$$

Tích vô hướng với $\bra{\omega}$ ta có được: $\braket{\omega|\Omega|\omega} = \omega\braket{\omega|\omega}$. Lấy liên hợp 2 vế:

$$
\braket{\omega|\Omega|\omega}^* = \omega^*\braket{\omega|\omega}^* \implies \braket{\omega|\Omega^\dagger|\omega} = \omega^*\braket{\omega|\omega}
$$

Mà ta biết rằng $\Omega^\dagger = \Omega$, vậy ta có được: $\braket{\omega|\Omega|\omega} = \omega^*\braket{\omega|\omega} = \omega\braket{\omega|\omega} \implies \omega = \omega^*$. Tức $\omega \in \mathbb{R}$

**Định lý 10:** Đối với mỗi toán tử Hermitian, tồn tại ít nhất một cơ sở gồm các vector riêng trực chuẩn. Ma trận đối với cơ sở này là ma trận chéo.

# Chéo hóa ma trận Hermitian
Giả sử toán tử Hermitian $\Omega$ trên $\mathbb{V}^n(\mathbb{C})$ được biểu diễn dưới dạng ma trận trong cơ sở trực chuẩn của các vector $\ket{1}, \ket{2}, \dots, \ket{n}$. Sau đó ta đổi từ cơ sở này sang cơ sở "riêng" gồm các vector riêng sau $\ket{\omega_1}, \ket{\omega_2}, \dots, \ket{\omega_n}$. Gọi toán tử $U$ là toán tử biến đổi các vector $\ket{i} \to \ket{\omega_i}$ tương ứng, tức:

$$
\ket{\omega_i} = U\ket{i}
$$

Thì $U$ là toán tử Unitary, ta chứng minh như sau. Vì toán tử $U$ chuyển các vector trực chuẩn sang các vector trực chuẩn khác do đó nó bảo toàn tích vô hướng giữa các vector cơ sở.

$$
\braket{i|j} = \braket{\omega_i|\omega_j} = \delta_{ij}
$$

$$
\braket{\omega_i|\omega_j} = \braket{Ui|Uj} = \braket{i|U^\dagger U|j} = \braket{i|j} = \delta_{ij} \implies U^\dagger U = I
$$

Do đó mỗi toán tử Hermitian $\mathbb{V}^n(\mathbb{C})$ đều "có thể" được chéo hóa bởi một toán tử Unitary đổi cơ sở $U$. Ta diễn đạt lại một cách chặt chẽ hơn như sau:
Nếu $\Omega$ là một ma trận Hermitian thì tồn tại một ma trận Unitary $U$ (được xây dựng dựa trên các vector riêng của $\Omega$) sao cho $U^\dagger \Omega U$ là ma trận chéo.

# Tổng quát hóa vô hạn chiều

$$
\braket{f|g} = \int_a^b f^*(x)g(x)dx
$$

Tại mọi điểm $x$ đều có tương ứng với một vector cơ sở là $\ket{x}$. Điều kiện các cơ sở trực giao nhau là:

$$
\braket{x|x'} = 0, \ x \neq x'
$$

Ta có tính chất sau:

$$
\int_a^b \ket{x'}\bra{x'}dx' = \mathbf{I}
$$

Nhân vô hướng 2 vế trên với một ket hàm tùy ý nào đó $\ket{f}$ bên phải và một cơ sở $\bra{x}$ vào bên trái, ta được:

$$
\int_a^b \braket{x|x'}\braket{x'|f}dx' = \bra{x}\mathbf{I}\ket{f} = \braket{x|f}
$$

Mà $\braket{x|f}$ là phép chiếu $f$ lên vector cơ sở $\ket{x}$, tức $\braket{x|f} = f(x)$ và cũng tương tự $\braket{x'|f} = f(x')$. Đặt $\braket{x|x'}$ là một hàm $\delta(x, x')$ nào đó chưa biết (Ta đang đi tìm hàm này). Vì $\delta(x, x')$ sẽ bị triệt tiêu khi $x \neq x'$ (Tính chất trực giao của 2 vector cơ sở), ta giới hạn tích phân trên trong một vùng lân cận vô cùng bé mà $x'$ gần $x$:

$$
\int_{x - \epsilon}^{x + \epsilon} \delta(x, x')f(x')dx' = f(x)
$$

Trong vùng vô cùng bé này, với mọi hàm liên tục $f$ đều có thể xấp xỉ $f(x') \approx f(x)$, do đó có thể đem $f(x)$ ra khỏi tích phân:

$$
f(x)\int_{x - \epsilon}^{x + \epsilon} \delta(x, x')dx' = f(x) \implies \int_{x - \epsilon}^{x + \epsilon} \delta(x, x')dx' = 1
$$

Chắc chắn $\delta(x, x')$ không thể có giá trị hữu hạn tại $x' = x$, vì nếu nó có giá trị hữu hạn sẽ dẫn đến tích phân trên là một vô cùng bé. Thực tế $\delta(x, x')$ tiến đến vô cùng khi $x' \to x$, mặt khác $\delta(x, x')$ chỉ phụ thuộc vào $x - x'$ nên ta viết lại thành $\delta(x - x')$. Hàm $\delta(x - x')$ có các tính chất:

$$
\begin{aligned}
& \delta(x - x') = 0, \ x \neq x', \\
& \int_a^b \delta(x - x')dx = 1, \ a < x < b
\end{aligned}
$$

được gọi là hàm Dirac delta và nó chuẩn hóa các vector cơ sở:

$$
\braket{x|x'} = \delta(x - x')
$$

Hàm Dirac delta là hàm chẵn:

$$
\delta(x - x') = \braket{x|x'} = \braket{x'|x}^* = \delta(x' - x)^* = \delta(x' - x) 
$$

(Vì hàm Dirac là hàm thực).
Ta có đạo hàm của hàm Dirac delta:

$$
\delta'(x - x') = \delta(x - x')\frac{d}{dx'}
$$

Tổng quát ta có đạo hàm cấp $n$:

$$
\frac{d^n\delta(x - x')}{dx^n} = \delta(x - x')\frac{d^n}{dx'^n}
$$

Ta cũng có thể xây dựng hàm Dirac delta dựa trên biến đổi Fourier, ta có một hàm $f(x)$ và biến đổi Fourier nó:

$$
f(k) = \frac{1}{(2\pi)^{1/2}}\int_{-\infty}^\infty e^{-ikx}f(x)dx
$$

và nghịch đảo của nó:

$$
f(x') = \frac{1}{(2\pi)^{1/2}}\int_{-\infty}^\infty e^{-ikx'}f(k)dk
$$

Thay $f(k)$ ở bên trên vào bên dưới:

$$
\begin{aligned}
f(x') & = \frac{1}{(2\pi)^{1/2}}\int_{-\infty}^\infty e^{-ikx'}\left(\frac{1}{(2\pi)^{1/2}}\int_{-\infty}^\infty e^{-ikx}f(x)dx\right)dk \\
 & = \int_{-\infty}^\infty \left(\frac{1}{2\pi}\int_{-\infty}^\infty dk \ e^{ik(x' - x)}\right)f(x)dx
\end{aligned}
$$

Từ đây thể suy ra được hàm Dirac delta:

$$
\frac{1}{2\pi}\int_{-\infty}^\infty dk \ e^{ik(x' - x)} = \delta(x' - x)
$$

# Toán tử trong không gian vô hạn chiều
Ta cũng có các toán tử tác dụng lên các vector hàm $\ket{f}$, ta xét phương trình sau:

$$
\Omega \ket{f} = \ket{\tilde{f}}
$$

Một toán tử mà ta thường gặp là toán tử đạo hàm, toán tử là một ánh xạ từ hàm này sang hàm khác.

$$
D\ket{f} = \ket{df/dx}
$$

trong đó $\ket{df/dx}$ là ket tương ứng với hàm số $df/dx$. Để tìm ma trận của $D$ trong cơ sở $\ket{x}$, ta nhân vô hướng bên trái với $\bra{x}$ phương trình trên:

$$
\braket{x|D|f} = \left\langle x \left| \frac{df}{dx} \right. \right\rangle = \frac{df(x)}{dx}
$$

Suy ra được:

$$
\int \braket{x|D|x'}\braket{x'|f}dx' = \int \braket{x|D|x'}f(x')dx' = \frac{df(x)}{dx}
$$

Từ đây ta suy ra được:

$$
\braket{x|D|x'} = D_{xx'} = \delta'(x - x') = \delta(x - x')\frac{d}{dx'}
$$

Lưu ý cần nhớ rằng $D_{xx'} = \delta(x - x')$ sẽ được tích phân theo biến số thứ 2 là $x'$ và được tính tại $x$. Tức là:

$$
\int \delta(x - x')\frac{d}{dx'}f(x')dx' = \frac{d}{dx'}f(x')\Big|_{x' = x} = \frac{d}{dx}f(x)
$$

Toán tử $K$ là Hermitian nếu:

$$
\braket{g|K|f} = \braket{g|Kf} = \braket{Kf|g}^* = \braket{f|K^\dagger|g}^* = \braket{f|K|g}^* = \braket{f|Kg}^*
$$

Ví dụ với $K = -iD$, trong đó $D$ là toán tử lấy đạo hàm mà ta đã nói ở trên.

$$
\begin{aligned}
\braket{g|Kf} & = \int_a^b g^*(x)\left(-i\frac{df(x)}{dx}\right)dx \stackrel{?}{=} \left(\int_a^b f^*(x)\left(-i\frac{dg(x)}{dx}\right)dx\right)^* \\
& = i\int_a^b f(x)\frac{dg^*(x)}{dx}dx = \braket{f|Kg}^*
\end{aligned}
$$

Ta có:

$$
\frac{d}{dx}(g^*f) = \frac{dg^*}{dx}f + g^* \frac{df}{dx}
$$

Ta tích phân từng phần:

$$
-i\int_a^b g^*(x)\frac{df(x)}{dx}dx = -ig^*(x)f(x)\Big|_a^b + i\int_a^b f(x)\frac{dg^*(x)}{dx}dx
$$

Vậy $\braket{g|Kf} = \braket{f|Kg}^*$ khi:

$$
-ig^*(x)f(x)\Big|_a^b = 0
$$

Giới hạn Cesàro là một sự mở rộng của khái niệm giới hạn thông thường. Ví dụ như giới hạn của các hàm sin, cos khi tiến đến vô cùng là bằng 0 theo giới hạn Cesàro.

Bây giờ ta sẽ đi tìm giá trị riêng của toán tử $K$ này.

$$
K\ket{k} = k\ket{k}
$$

Nhân vô hướng $\bra{x}$ vào bên trái 2 vế (chiếu lên vector cơ sở $\ket{x}$), đặt $\psi_k(x) = \braket{x|k}$:

$$
\begin{aligned}
& \braket{x|K|k} = k\braket{x|k} \\
\implies & \int \braket{x|K|x'}\braket{x'|k}dx' = k\braket{x|k} \\
\implies & -i\int \delta(x - x')\frac{d}{dx'} \psi_k(x')dx' = k\psi_k(x) \\
\implies & -i\frac{d}{dx}\psi_k(x) = k\psi_k(x)
\end{aligned}
$$

Nếu thay trực tiếp K vào phương trình ban đầu, tức:

$$
-i\frac{d}{dx}\ket{k} = k\ket{k}
$$

thì điều này không có ý nghĩa rõ ràng để suy ra được phương trình bên trên. Vậy ta có phương trình sau đây và cần tìm $\psi_k(x)$ thỏa mãn:

$$
-i\frac{d}{dx}\psi_k(x) = k\psi_k(x)\implies \frac{d\psi_k}{\psi_k} = ikdx \implies \psi_k(x) = Ae^{ikx}
$$

Mỗi một số thực $k$ là một giá trị riêng, tương ứng với nó là một vector riêng (hoặc eigenfunction) là $Ae^{ikx}$. Thông thường ta chọn $A = 1/(2\pi)^{1/2}$, tức:

$$
k \leftrightarrow \frac{1}{(2\pi)^{1/2}}e^{ikx}
$$

Ta xem thử tính trực giao giữa 2 vector riêng:

$$
\begin{aligned}
\braket{k|k'} & = \int_{-\infty}^\infty \braket{k|x}\braket{x|k'}dx = \int_{-\infty}^\infty \braket{x|k}^*\braket{x|k'}dx \\
& = \frac{1}{2\pi}\int_{-\infty}^\infty e^{-ikx}e^{ik'x}dx = \frac{1}{2\pi}\int_{-\infty}^\infty e^{-i(k - k')x}dx = \delta(k - k')
\end{aligned}
$$

Vì $\braket{k|k}$ là vô cùng, nên không tồn tại giá trị $A$ hữu hạn nào để chuẩn hóa $\braket{k|k}$. Cách tự nhiên nhất là dùng hàm Dirac delta để chuẩn hóa khi phổ giá trị riêng là liên tục.

Vì $K$ là một toán tử Hermitian, hàm số đã được khai triển trong cơ sở $X$ với các thành phần $f(x) = \braket{x|k}$ cũng được khai triển trong cơ sở $K$ (cơ sở các eigenfunctions). Để tìm các thành phần của nó trong cơ sở này, ta làm như sau:

$$
f(k) = \braket{k|f} = \int_{-\infty}^\infty \braket{k|x}\braket{x|f}dx = \frac{1}{(2\pi)^{1/2}}\int_{-\infty}^\infty e^{-ikx}f(x)dx
$$

Để chuyển ngược lại cơ sở $X$ ta cũng làm tương tự:

$$
f(x) = \braket{x|f} = \int_{-\infty}^\infty \braket{k|x}\braket{k|f}dk = \frac{1}{(2\pi)^{1/2}}\int_{-\infty}^\infty e^{ikx}f(k)dk
$$

Ta có thể thấy, biến đổi Fourier là phép đổi cơ sở qua lại giữa $\ket{x} \leftrightarrow \ket{k}$. Bây giờ ta đã biết nguồn gốc của cơ sở $K$, là xuất phát từ toán tử Hermitian $K$. Thế toán tử nào chịu trách nhiệm cho cơ sở $X$? Ta gọi toán tử này là $X$, các vector cơ sở $\ket{x}$ là vector riêng của nó tương ứng với giá trị riêng $x$:

$$
X\ket{x} = x\ket{x}
$$

Các yếu tố ma trận (Matrix elements) trong cơ sở $X$ là:

$$
\braket{x'|X|x} = x\braket{x'|x} = x\delta(x' - x)
$$

Toán tử này tác động lên một hàm sẽ như thế nào?

$$
X\ket{f} = \ket{\tilde{f}}
$$

Nhân vô hướng bên trái với $\bra{x}$ vào 2 vế:

$$
\braket{x|X|f} = \int\braket{x|X|x'}\braket{x'|f}dx' = \int x'\delta(x - x')f(x')dx' = xf(x) = \braket{x|\tilde{f}} = \tilde{f}(x)
$$

Vậy $\tilde{f}(x) = xf(x)$. Tức tác động của toán tử $X$ lên một hàm $f(x)$ là $x$ nhân với chính hàm $f(x)$ đó, có thể tổng quát tác động của $X$ trong không gian Hilbert như sau:

$$
X\ket{f(x)} = \ket{xf(x)}
$$

Có một mối quan hệ tương hỗ thú vị giữa các toán tử $X$ và $K$, điều này thể hiện rõ khi ta tính các yếu tố của ma trận $X$ trong cơ sở $K$:

$$
\begin{aligned}
\braket{k|X|k'} & = \int_{-\infty}^{\infty}\braket{k|X|x}\braket{x|k'}dx \\
& = \int_{-\infty}^{\infty}\braket{k|x}x\braket{x|k'}dx, \ \ \ \text{Since }X\ket{x} = x\ket{x} \\
& = \frac{1}{2\pi}\int_{-\infty}^\infty e^{-ikx}\ x \ e^{ik'x}dx = i\frac{d}{dk}\left(\frac{1}{2\pi}\int_{-\infty}^\infty e^{i(k' - k)x}dx\right) = i\delta'(k - k')
\end{aligned}
$$

Do đó nếu $\ket{g(k)}$ là một ket mà ảnh của nó trong cơ sở $K$ là $g(k)$ thì:

$$
X\ket{g(k)} = \left\langle i\frac{dg(k)}{dk} \right\rangle
$$

Tóm lại trong cơ sở $X$, toán tử $X$ tác động như là $x$ còn $K$ thì tác động như là $-id/dx$ (trên các hàm $f(x)$), trong khi ở cơ sở $K$ thì $X$ tác động như là $id/dk$ (trên các hàm $g(k)$). Các toán tử có mối quan hệ như vậy được gọi là **liên hợp** với nhau.

Các toán tử liên hợp $X$ và $K$ là không giao hoán với nhau. Giả sử cho các toán tử tác động lên một hàm $f(x)$ trong cơ sở $X$:

$$
\begin{aligned}
& X\ket{f} \to xf(x) \\
& K\ket{f} \to -i\frac{df(x)}{dx}
\end{aligned}
$$

Và do đó:

$$
\begin{aligned}
& KX\ket{f} \to -ix\frac{df(x)}{dx} \\
& XK\ket{f} \to -i\frac{d}{dx}xf(x)
\end{aligned}
$$

Dẫn đến:

$$
[X, K]\ket{f} = -ix\frac{df(x)}{dx} + ix\frac{df(x)}{dx} + if = if \to i\mathbf{I}\ket{f}
$$

vì $\ket{f}$ là vector tùy ý nên cuối cùng ta có được giao hoán tử giữa $X$ và $K$ là:

$$
[X, K] = i\mathbf{I}
$$
