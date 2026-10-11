---

title: Note về nhiệt động lực học (11/10/2026)
description: Một vài note về nhiệt động lực học, các phương trình trạng thái.
---
Nguyên lý 1 nhiệt động lực học là:

$$
\delta Q = dU + p_{ext}dV
$$

trong đó $p_{ext}$ là áp suất mà môi trường tác dụng lên hệ, nếu quá trình là thuận nghịch thì ta có:

$$
\delta W = - \delta W_{ext} \implies p_{ext} = p
$$

Và ta có được:

$$
\delta Q = dU + pdV
$$

trong đó $p$ là áp suất khí của hệ khí, tất nhiên đẳng thức trên chỉ đúng nếu như đó là quá trình thuận nghịch.
Theo nguyên lý 2 nhiệt động lực học, ta có:

$$
TdS \geq \delta Q = dU + p_{ext}dV \implies dU \leq TdS - p_{ext}dV
$$

Còn đẳng thức mà ta hay thấy:

$$
dU = TdS - pdV
$$

đây là vi phân của hàm trạng thái $U = U(S, V)$ trong đó:

$$
T = \left(\frac{\partial U}{\partial S}\right)_V, \ \ \ p = -\left(\frac{\partial U}{\partial V}\right)_S
$$

tức nó không phải nguyên lý 1 nhiệt động lực học, và đẳng thức trên luôn đúng. Chỉ cần ta xác định được một đường đi trong đó $T, p$ là xác định trên đường đi đó thì ta tích phân được.

Từ đó, ví dụ với hàm Hemholtz là $F = U - TS$, với quá trình đẳng nhiệt ta có:

$$
d(U - TS) = dF \leq -p_{ext}dV = \delta W_{ext}
$$

còn nếu ta lấy vi phân $F$ là $dF = dU - TdS - SdT = -SdT - pdV$ ($F$ là hàm trạng thái), với quá trình đẳng nhiệt ta có:

$$
dF = -pdV = \delta W
$$

Nếu quá trình là bất thuận nghịch thì $\delta W \neq \delta W_{ext}$ và dấu bằng không xảy ra.
