---

title: Chứng minh định lý Fermat nhỏ bằng lý thuyết nhóm (30/10/2026)
description: Chứng minh định lý Fermat nhỏ bằng lý thuyết nhóm.
---
**Định lý:** Cho $p$ là một số nguyên tố, $a$ là số nguyên bất kỳ thì $p \mid a^p - a$.

**Chứng minh:**

Ta có tập hợp các lớp tương đương modulo khác lớp $0$ $(\mathbb{Z}/p)\setminus\lbrace [0] \rbrace = \lbrace [1], [2], \dots, [p - 1] \rbrace$ được trang bị phép toán 2 ngôi như sau:

$$
[x][y] = [xy]
$$

Ta chứng minh tập hợp trên cùng với phép toán 2 ngôi lập thành một nhóm.

**Tính đóng:** Ta chứng minh nó có tính đóng: Xét $[x], [y] \in (\mathbb{Z}/p)\setminus\lbrace [0] \rbrace \Rightarrow p \nmid x, \ p \nmid y \Rightarrow p \nmid xy$ (Vì $p$ nguyên tố), vậy $[x][y] = [xy] \in (\mathbb{Z}/p)\setminus\lbrace [0]\rbrace$.

**Tính kết hợp:** Hiển nhiên.

**Phần tử đơn vị**: Phần tử đơn vị của nhóm là phần tử $[1]$, dễ thấy $[x][1] = [1][x] = [1x] = [x]$.

**Phần tử nghịch đảo:** Với $[x] \in (\mathbb{Z}/p)\setminus\lbrace [0] \rbrace$ vì $x$ và $p$ nguyên tố cùng nhau nên theo định lý Bezout luôn tồn tại 2 số nguyên $k, \ n \in \mathbb{Z}$ thỏa mãn $kx - np = 1 \Rightarrow kx - 1 = np \Rightarrow [kx] = [x][k] = [k][x] = [1] \Rightarrow [x]^{-1} = [k]$. Vậy với mọi phần tử trong tập hợp luôn tồn tại một phần tử nghịch đảo.

Do đó tập hợp $(\mathbb{Z}/p)\setminus\lbrace [0] \rbrace$ cùng với phép toán hai ngôi lập nên một nhóm.

- Nếu $p \nmid a$ thì $[a] \in (\mathbb{Z}/p)\setminus\lbrace [0] \rbrace$, theo hệ quả của định lý Lagrange thì cấp của nhóm $(\mathbb{Z}/p)\setminus\lbrace [0] \rbrace$ là $p - 1$ cũng là số mũ của $[a]$, tức $[a]^{p - 1} = [1] \Rightarrow p \mid a^{p - 1} - 1$. Mà $a^p - a = a(a^{p - 1} - 1) \Rightarrow p \mid a^p - a$.
- Nếu $p \mid a$ thì ta có ngay $p \mid a^p -a = a(a^{p-1} - 1)$.

Vậy với mọi số nguyên $a$ bất kỳ ta luôn có $p \mid a^p - a$. Ta có điều phải chứng minh.
