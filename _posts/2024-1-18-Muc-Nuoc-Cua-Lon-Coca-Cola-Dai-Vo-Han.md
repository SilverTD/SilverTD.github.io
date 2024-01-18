---

title: Mực nước của lon Coca Cola dài vô hạn
thumbnail: https://silvertd.github.io/assets/img/Water-1.png
description: Ở bài viết này, ta sẽ nghiên cứu một vấn đề vật lý trong thực tế. Đó là mực nước của lon Coca Cola hoặc trong một cốc nước sẽ thay đổi như nào khi thay đổi góc nghiêng giữa lon và mặt phẳng ngang,...

---

# Giả thuyết
- Giả sử lon coca có chiều dài vô hạn và không có khối lượng.
- Lon coca là một hình trụ bán kính $R$.
- Góc $\theta$ là góc hợp bởi lon coca với mặt phẳng ngang, $\theta$ càng nhỏ thì lon nghiêng càng nhiều.
- Mực nước ban đầu là $L$
- Sử dụng đơn vị radian thay vì là độ.

# Giải quyết bài toán mực nước trong lon Coca Cola
## Phát biểu bài toán
Cho rằng lon Coca Cola ban đầu ở góc $\theta = \pi/2$ và mực nước lúc đó là $L$, khi lon Coca Cola càng nghiêng dần thì mực nước của lon sẽ di chuyển có quy luật như nào ? Đi tìm quy luật đó (đồ thị, thực nghiệm).

## Mô hình đơn giản
Ở mô hình đơn giản này, ta sẽ giả sử lon Coca Cola là một hình hộp chữ nhật. Ta sẽ chia ra 2 trường hợp: $\theta \geq \theta_0$ và $\theta \leq \theta_0$.

Thế $\theta_0$ ở đây là gì ? $\theta_0$ ở đây là góc hợp giữa lon và mặt phẳng ngang mà khi đó là sự chuyển đổi hình dạng của nước từ "hình thang" sang "hình tam giác" (khi nhìn lon Coca Cola theo hướng 2 bên).

Ta dễ dàng tìm được $\theta_0 = arctan(\dfrac{L}{R})$, ta sẽ đi giải quyết trường hợp đầu tiên $\theta \geq \theta_0$ (hình dạng của nước lúc này là hình thang).

![](./assets/img/Water-1.png)

Như hình vẽ, ta dễ dàng thấy phần diện tích ở phía trên đã di chuyển xuống phần diện tích ở dưới. Ta đơn giản tìm được độ cao mực nước lúc này là:
$$
h(\theta) = Rcos(\theta) + Lsin(\theta)
$$

Tiếp đến là trường hợp $\theta \leq \theta_0$, hình dạng của nước lúc này là hình tam giác:

![](./assets/img/Water-2.png)

Lúc này ta sẽ giải quyết vấn đề khác với trường hợp đầu. Ta thấy rằng cho dù lon nghiêng với một góc như thế đi nữa thì thể tích của nước là không đổi. Ta có điều kiện $V_0 = V$ hay $A_0 = A$ với A là diện tích của nước (vì độ dày là bằng nhau).

Ta dễ dàng tìm được diện tích của nước như sau:

$$
A(\theta) =\dfrac{1}{2}\dfrac{h(\theta)}{sin(\theta)}\dfrac{h(\theta)}{cos(\theta)}
$$

Do thể tích nước là bảo toàn nên ta có (gọi bề dày là $a$):

$$
\displaylines{V(\theta) = V_0 \leftrightarrow aA(\theta) = aA_0 \\
\leftrightarrow \dfrac{1}{2}\dfrac{h(\theta)}{sin(\theta)}\dfrac{h(\theta)}{cos(\theta)} = 2LR \\
\leftrightarrow h(\theta) = \sqrt{4LRsin(\theta)cos(\theta)}}
$$

Tổng kết lại chúng ta có được hàm độ cao mực nước phụ thuộc vào góc $\theta$ như sau (đây là một hàm liên tục):

$$
\begin{equation*}
h(\theta) = 
\begin{cases}
    Rcos(\theta) + Lsin(\theta) & \theta \geq \theta_0 \\
    \sqrt{4LRsin(\theta)cos(\theta)} & \theta \leq \theta_0
\end{cases}
\end{equation*}
$$

## Mô hình phức tạp
Tuy mô hình trên khá đơn giản, nhưng trên thực tế các lon Coca Cola đều có dạng là hình trụ, do đó vấn đề sẽ phức tạp hơn rất nhiều. Tương tự, ta chia ra 2 trường hợp là $\theta \geq \theta_0$ và $\theta \leq \theta_0$.

![](./assets/img/Water-1.png)

Ở trường hợp $\theta \geq \theta_0$ đơn giản chỉ cần tính thể tích của hình phiến trụ. Từ đó ta cũng sẽ tìm được công thức tương tự như mô hình đầu tiên:

$$
h(\theta) = Rcos(\theta) + Lsin(\theta)
$$

Riêng trường hợp $\theta \leq \theta_0$ lại phức tạp hơn rất nhiều. Lúc này sẽ cần đến vi tích phân để tính phần thể tích nước.

![](./assets/img/Water-2.png)

Chọn trục tọa độ như hình vẽ với tâm $O$ là tâm của hình tròn bán kính $R$. Đầu tiên ta chia nhỏ thể tích nước thành các hình chữ nhật như sau:

![](./assets/img/Water-3.png)

Gọi $J, H$ lần lượt độ dài của phần nước ở đáy lon và độ dài cạnh góc vuông lúc này, ta tính được các đại lượng sau:

$$
\displaylines{\phi = \pi/2 - \theta \\
z(x) = \dfrac{H(x - R + J)}{J} \\
y(x) = \sqrt{R^2 - x^2}}
$$

Và diện tích phần hình chữ nhật lúc này là:

$$
A(x) = z(x) \times 2y(x)
$$

Từ đó ta lấy tổng tất cả các hình chữ nhật bằng cách tích phân cận từ $(R - J) \rightarrow R$, ta được:

$$
\begin{equation*}
\begin{aligned}
    V(\theta) & = \int_{R - J}^{R} A(x) dx \\
    &= 2\int_{R - J}^{R} \dfrac{H(x - R + J)}{J} \times \sqrt{R^2 - x^2} \ dx \\
    &= \dfrac{H\times R^2}{3}(\dfrac{3sin(\psi) - 3 \psi cos(\psi) - sin^3\psi}{1 - cos(\psi)})
\end{aligned}
\end{equation*}
$$

Với:

$$
\displaylines{\psi = \pi - arctan(\dfrac{J - R}{R})\\
H = \dfrac{h(\theta)}{sin(\theta)}, \ J = \dfrac{h(\theta)}{cos(\theta)}}
$$

Tương tự, do thể tích nước trong lon bảo toàn nên ta có:

$$
V(\theta) = V_0 = L\pi R^2
$$

Giải phương trình trên và ta sẽ tìm được $h(\theta)$.

## Biện luận và thử nghiệm
Từ các công thức trên, ta thấy rằng khi góc $\theta \rightarrow 0$ thì $H \rightarrow \infty$ và $J \rightarrow 0$

Để dễ hình dung mực nước di chuyển như nào, ta cần vẽ đồ thị $h(\theta)$.

Ở đây ta thử nghiệm với $L = R = 1.5$, Bên dưới là bảng dữ liệu mà tác giả đã tính toán được đối với trường hợp $\theta \leq \theta_0$:

![](./assets/img/Water-5.png)

Ta dễ thấy $y_2$ ban đầu giảm rất chậm, sau đấy thì lại giảm càng nhanh và dốc hơn rất nhiều. Tác giả dự đoán rằng đây là một hàm lũy thừa:

$$
f(x) \approx a \times x^b
$$

Thật vậy, từ việc dùng <b>Nonlinear Regression</b>, ta có được đồ thị của mực nước lúc đấy như sau:

$$
h(x) \approx 2.41978 \times x^{0.328745}
$$

Bên dưới là đồ thị kết hợp cả 2 trường hợp, và chắc chắn đây là một hàm liên tục.

![](./assets/img/Water-4.png)

Phần màu đỏ là trường hợp $\theta \geq \theta_0$ (hình phiến trụ) và phần màu xanh là trường hợp $\theta \leq \theta_0$ (hình trụ nêm). Ta thấy rằng đồ thị trông khá hợp lí và rất đẹp (khá gần với các giá trị tính toán từ bảng số liệu trên).

# Kết luận
Việc dự đoán mực nước trong lon Coca Cola dài vô hạn cứ ngỡ đơn giản, tuy nhiên việc tính toán lại rất phức tạp. Đặc biệt là tính toán thể tích của hình trụ nêm.

Tuy nhiên đây hoàn toàn là một nghiên cứu vấn đề thực tế rất hay, giúp học hỏi được các kĩ năng cần thiết trong việc nghiên cứu khoa học.

Đây chưa phải là vấn đề duy nhất mà tác giả sẽ giải quyết, ở bài viết sau ta sẽ giải quyết bài toán "Cần uống bao nhiêu % thể tích nước để lon Coca Cola cân bằng khi nghiêng một góc $\theta$".
