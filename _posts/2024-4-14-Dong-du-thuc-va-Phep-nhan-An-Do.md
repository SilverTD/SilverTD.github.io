---

title: Đồng dư thức và phép nhân Ấn Độ

---

<b>Tác giả: </b> <i>Lương Thiện Phúc</i>, ĐH Sư phạm Kỹ thuật Thành phố Hồ Chí Minh.

## 1. Đồng dư thức

Chia dư hay chia lấy dư (modulo) kí hiệu là $\\%$ hoặc $mod$, là phép toán lấy phần dư của số nguyên $A$ khi chia với $N$.

<b>Ví dụ</b>:

$5 \ \\% \ 3 = 2$

$10 \ \\% \ 10 = 0$

$23 \ \\% \ 12 = 11$

Các phép toán chia dư cũng có thể thực hiện trên 1 số âm (nhưng mà tạm thời chúng ta chưa cần quan tâm đến nó).

Giả sử ta có $A \ \\% \ N = C$, và $B \ \\% \ N = C$, khi đó ta nói $A$ “đồng dư” (có cùng số dư) $B$ theo modulo $N$. Khi $A$ đồng dư $B$, sẽ có một số phép toán.

Với $K$ là 1 số nguyên bất kì, ta có:

- $(A + K) \ \\% \ N = (B + K) \ \\% \ N$

- $(A - K) \ \\% \ N = ( B - K ) \ \\% \ N$

- $(A * K) \ \\% \ N = ( B * K ) \ \\% \ N$

- $[ ( A \ \\% \ N ) + ( K \ \\% \ N ) ] \ \\% \ N = ( A + K ) \ \\% \ N$

- $[ ( A \ \\% \ N ) - ( K \ \\% \ N ) ] \ \\% \ N = ( A - K ) \ \\% \ N$

- $[ ( A \ \\% \ N ) * ( K \ \\% \ N ) ] \ \\% \ N = ( A * K ) \ \\% \ N$

<b>Lưu ý</b>: Các phép toán chỉ đúng với phép cộng, phép trừ và phép nhân. Muốn thực hiện phép chia phải áp dụng lí thuyết “Nghịch đảo modulo” (cái này chúng ta không cần quan tâm cũng được).

## 2. Khái niệm phép nhân Ấn Độ

Dễ dàng nhận thấy được, mọi số tự nhiên $N$ có thể viết dưới dạng 1 số $K$ nguyên dương nào đó:

$$
\begin{equation*}
N  = 
\begin{cases}
      2 * K & \text{nếu N chẵn} \\
      2 * K + 1 & \text{nếu N lẻ}
\end{cases}
\end{equation*}
$$

<b>Ví dụ:</b>

```
0 = 2 * 0
1 = 2 * 0 + 1
2 = 2 * 1
3 = 2 * 1 + 3
4 = 2 * 2
...
101 = 2 * 50 + 1
```

Và ta dễ dàng nhận thấy rằng, nếu số nguyên $K > 2$, có thể phân tích $K$ dưới dạng số nguyên dương $K'$:

$$
\begin{equation*}
K  = 
\begin{cases}
      2 * K' & \text{nếu K chẵn} \\
      2 * K' + 1 & \text{nếu K lẻ}
\end{cases}
\end{equation*}
$$

Vậy lúc này số tự nhiên $N$ sẽ có dạng:

$$
\begin{equation*}
N  = 
\begin{cases}
      2 * ( 2 * K' )  & \text{nếu N chẵn và K chẵn} \\
      2 * ( 2 * K' + 1 ) & \text{nếu N chẵn và K lẻ} \\
      2 * ( 2 * K' ) + 1 & \text{Nếu N lẻ và K chẵn} \\
      2 * ( 2 * K' + 1 ) + 1 & \text{N lẻ và K lẻ} 
\end{cases}
\end{equation*}
$$

<b>Ví dụ:</b>

```
6 = 2 * 3 = 2 * (2 * 1 + 1)
7 = 2 * 3 + 1 = 2 * (2 * 1 + 1) +1
8 = 2 * 4 = 2 * (2 * 2)
9 = 2 * 4 + 1 = 2 * (2 * 2) + 1
10 = 2 * 5 = 2 * (2 * 2 + 1)
11 = 2 * 5 + 1 = 2 * (2 * 2 + 1) + 1
...
```

Vậy nếu liên tục phân tích số tự nhiên $N$ thành số $K$, các số $K$ thành $K'$, $K''$,$...$ cho đến khi $K \leq 2$, ta sẽ được số tự nhiên $N$ có dạng là các tích của 2 và cộng thêm 1.

Giả sử ta có hai số tự nhiên $A$ và $B$, áp dụng cách phân tích ta có thể viết lại $A * B$ dưới dạng dạng biểu thức $(A * 2) * (B / 2) = A * B$ (luôn đúng). 

```
5 * 4 = ( 5 * 2 ) * ( 4 / 2 ) = 10 * 2 =20
3 * 7 = ( 3 * 2 ) * (  7 / 2 ) = 6 * 3.5 = 21
hay 3 * 7 = ( 3 * 2 ) * [ ( 2 * 3 + 1 ) / 2 ] = 6 * ( 2 * 3 / 2 ) + 6 * ( 1 / 2 ) = 21
```

<b>Và đây là nền tảng của phép nhân Ấn Độ!</b>

Vậy tổng quát lên, ta có $A * B$ sẽ bằng:

$$
\begin{equation*}
A * B  = 
\begin{cases}
      [(A * 2) * (B / 2)]  & \text{nếu B chẵn} \\
      [ ( A * 2 )  * [ ( B - 1 ) / 2 ] + A ] & \text{nếu B lẻ}
\end{cases}
\end{equation*}
$$

Vậy ta luôn có thể thực hiện phép toán trên với mọi $B > 1$:
- Ta sẽ kiểm tra $B$, nếu $B = 0$ thì kết quả của phép nhân là $0$.
- Sau đó, ở mỗi bước, ta sẽ kiểm tra tính chẵn lẻ của $B$, nếu $B$ lẻ ta sẽ lưu tổng cộng dồn của $A = T$, với $T$ ban đầu bằng $0$.
- Nhân $A$ lên $2$ lần, giảm $B$ đi $2$ lần.
- Thực hiện vòng lặp đến khi $B = 1$, khi đó $A + T$ sẽ là kết quả của phép nhân Ấn Độ $A * B$.

<b>Ví dụ</b> $A = 10$, $B = 5$:

<b>Lần 1:</b> $B = 5 \rightarrow B > 1$
- $B = 5$ (lẻ) $\rightarrow$ $T = T + A = 0 + 10 = 10$
- $A = A * 2 = 10 * 2 = 20$
- $B = B / 2 = 2$

<b>Lần 2:</b> $B = 2 > 1$
- $B$ (chẵn) $\rightarrow$ không cộng dồn $A$ vào $T$
- $A = A * 2 = 40$
- $B = B / 2 = 1$

<b>Lần 3:</b> $B = 1 \rightarrow$ kết thúc lặp, $A = 40$, $T = 10$, $A + T = 50$ là kết quả của thuật toán.

## 3. Thuật toán tính nhanh hàm mũ

Giả sử ta có hai số tự nhiên $A$ và $B$, ta dễ dàng tính được $A^B$ bằng cách:

$A ^ B = A * A * A * ... * A$ ($B$ lần).

Tuy nhiên ta có thể tính được hàm mũ nhanh hơn, phân tích số mũ $A ^ B$, có thể dễ dàng nhận ra :

$$
\begin{equation*}
A ^ B  = 
\begin{cases}
      {(A^{( B / 2 )})}^2  & \text{nếu B chẵn} \\
      {(A^{[ ( B - 1 ) / 2 ]})}^2 * A & \text{nếu B lẻ}
\end{cases}
\end{equation*}
$$

<b>Ví dụ:</b>
```
2 ^ 3 = 2 * 2 * 2 = ( 2 ^ 1 ) ^ 2 * 2
4 ^ 5 = 4 * 4 * 4 * 4 * 4 = ( 4 ^ 2 ) ^ 2 * 4
7 ^ 9 = ( 7 ^ 4 ) ^ 2 * 7
```

Vậy nếu ta liên tục tách số mũ $B$ thành $B / 2$ với mọi $B > 1$, sau đó ta sẽ tính ${(A ^ {( B / 2 )})} ^ 2$ thì sẽ nhanh hơn tính $A ^ B$ theo cách thông thường.

Ta sẽ kiểm tra $B$:
- Nếu $B = 0$ thì kết quả của hàm mũ là $1$.
- Nếu $B = 1$ thì kết quả của hàm mũ là $A$.

Sau đó, ở mỗi bước, ta sẽ kiểm tra tính chẵn lẻ của $B$, nếu $B$ lẻ ta sẽ lưu một tích nhân dồn của $A = T$, với $T$ ban đầu bằng $1$.

Nhân $A$ lên $A$ lần, giảm $B$ đi hai lần.

Kết thúc lặp đến khi $B$ giảm bằng $1$, khi đó $A * T$ là kết quả của hàm mũ $A ^ B$.

## 4. Phân tích bài toán

<b>Bài 1:</b> Cho 3 số nguyên dương $A, B, M \leq 10^{18}$. Tính $A * B \ \\% \ M$.

Ta có $M \leq 10^{18}$, $A \ \\% \ M \leq 10^{18}$, $B \ \\% \ M \leq 10^{18}$.

- Ta có $M \leq 10^{18}$: $A \ \\% \ M \leq 10^{18}$, $B \ \\% \ M \leq 10^{18}$

$(A \ \\% \ M) * (B \ \\% \ M) \ \\% \ M \leq 10^{36} \rightarrow $ Không thực hiện được.

Tuy nhiên nếu áp dụng phép nhân Ấn Độ cùng với đồng dư thức, ta có thể tính được:

- $(A \ \\% \ M) * 2 \ \\% \ M \leq 10^{18}$
- $B := B / 2$ luôn luôn giảm ngặt đến khi $B = 1$.

Vậy ý tưởng cho thuật toán là áp dụng phép nhân Ấn Độ, ở mỗi bước nhân, ta sẽ lấy đồng dư $A \ \\% \ M$, hoàn thành thuật toán.

<b>Bài 2:</b> Cho 3 số nguyên dương $A, B, M \leq 10^{18}$. Tính $A ^ B \ \\% \ M$.

Ta có $A \leq 10^{18} \rightarrow A * A \leq 10^{36} \rightarrow$ Không thực hiện được.

Tuy nhiên nếu áp dụng phép nhân Ấn Độ và đồng dư thức, ta có thể tính được:

- $(A * 2) \ \\% \ M \leq 10^{18}$
- $A / 2$ luôn giảm ngặt đến khi $A = 1$.

Ta có $B \leq 10^{18}$, giới hạn duyệt của vòng lặp là $\approx 10 ^ 7 \rightarrow$ Không thực hiện được.

Tuy nhiên nếu áp dụng thuật toán tính nhanh hàm mũ, ta có thể tính được với số lượng phép tính $\approx log_2(B) \approx 60 \rightarrow$ Rất nhanh.

Vậy ý tưởng của thuật toán là áp dụng thuật toán tính nhanh hàm mũ, ở mỗi bước nhân, ta sẽ áp dụng phép nhân Ấn Độ, đồng thời lấy đồng dư ở mỗi bước nhân, kết thúc thuật toán.
