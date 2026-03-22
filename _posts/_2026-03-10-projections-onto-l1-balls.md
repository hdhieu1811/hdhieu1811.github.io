---
layout: distill
title: Phép chiếu lên khối cầu $\mathcal{L}_1$
date: 2026-03-13
description:
tags: math
categories:
giscus_comments: true

authors:
  - name: Dinh-Hieu Hoang
    affiliations:
      name:
toc:
  - name: Đặt vấn đề
  - name: Giải quyết
    subsections:
      - name: Phương pháp cổ điển
      - name: Phương pháp kỳ lạ
        subsections:
          - name: Dóng từ một điểm đường thẳng vuông góc với đường thẳng khác
          - name: Tìm trung điểm của đoạn thẳng
          - name: Lấy căn bậc hai độ dài của đoạn thẳng
  - name: Mở rộng
    subsections:
      - name: Tính căn bậc hai của một số phức
      - name: Chia ba một góc
---

## Đặt vấn đề

Ngắn gọn thì, trong không gian $\mathbb{R}^n$ ta có điểm $\bold{v}$ và ta cần tìm hình chiếu $\bold{w}$ của nó trên một khối cầu với độ đo khoảng cách $\mathcal{L_1}$. Viết dưới dạng một bài toán tối ưu hóa như sau:

$$
\text{minimize } f(w)=\frac{1}{2}||\bold{w}-\bold{v}||^2_2 \\
\text{ subject to  } ||\bold{w}||_1\leq c
$$

Tại sao ta nên giải quyết bài toán này? Mình có hai động lực thế này, cái đầu là từ đầu tư định lượng và cái sau thì từ học máy:

> **Động lực 1**: Giả sử bạn là một nhà đầu tư chứng khoán. Kết thúc mỗi ngày, bạn xác định xem hôm sau bạn muốn có vị thế thế nào. Tuy nhiên, bạn cũng cần giới hạn lượng cổ phiếu được giao dịch sao cho chi phí giao dịch không vượt quá một chặn trên $c$ cho trước.

> **Động lực 2**: Bạn huấn luyện một mô hình máy học, ví dụ hồi quy tuyến tính hoặc mạng thần kinh tích chập. Để tránh hiện tượng quá khớp (overfitting), ta thêm một biểu thức gọi là hàm điều chỉnh (regularization) vào bên trong hàm mục tiêu. Có hai sự lựa chọn thường thấy, $\mathcal{L}_1$ và $\mathcal{L}_2$. Ở đây ta tò mò $\mathcal{L}_1$ sẽ dẫn ta tới kết quả có tính chất gì.

## Giải quyết

Ta có một số nhận xét giúp bài toán đơn giản hơn:
- $w_i$ và $v_i$ có cùng dấu. Vì nếu trái dấu, ta đổi dấu $w_i$ lại thì sẽ được nghiệm mới tối ưu hơn $\rightarrow$ vô lý!
- Ta có thể giải bài toán với $\tilde{\bold{v}}=|\bold{v}|$ rồi bổ sung dấu tương ứng với mỗi chiều để ra kết quả với $\bold{v}$. Thật vậy, ta xét nghiệm tối ưu của bài toán gốc, lấy trị tuyệt đối của mỗi chiều, ta sẽ được một nghiệm cho bài toán với $\tilde{\bold{v}}$ với độ lớn hàm $f$ không đổi. Ngược lại cũng thế $\rightarrow$ độ lớn hàm $f$ với nghiệm tối ưu của hai bài toán là bằng nhau!

Vậy ta chỉ cần giải bài toán sau, tạm gọi là __bài toán 1__:

$$
\text{minimize } f(w)=\frac{1}{2}||\bold{w}-\bold{v}||^2_2
$$
$$
\begin{align*}

\text{ subject to  } & \sum_{i=1}^n w_i\leq c, \\
& w_i\geq 0, v_i\geq 0

\end{align*}
$$

Trên không gian hai chiều $Oxy$ nhìn nó sẽ như này:

**TODO**: Thêm hình minh họa cho bài toán trên 2D

## Nhắc lại kiến thức

Nhắc lại hàm Lagrangian và điều kiện Karush-Kuhn-Tucker (KKT):

Giả sử ta có bài toán tối ưu như sau:

$$
\text{minimize } f(x)
$$

$$
\begin{align*}
\text{subject to } & g_i(x)\leq 0,\\
& h_j(x)=0
\end{align*}
$$

với $x$ thuộc tập $X$ là một tập con lồi của $\mathbb{R}^n$

Khi đó ta có hàm Lagrangian:

$$\mathcal{L}(x,\mu,\lambda)=f(x)+\mu^T g(x)+\lambda^T h(x)$$

> **Định lý 1**. Nếu $(x^*, \mu^*)$ là một điểm yên ngựa của hàm Lagrangian với $x\in X$ và $\mu^*\geq 0$ thì $x^*$ là một nghiệm tối ưu của bài toán.

> **Định lý 2**. Giả sử $f(x)$ và $g_i(x)$ là hàm lồi và tồn tại một giá trị $x_0\in X$ sao cho $g(x_0)<0$ (điểm interior). Đặt $x^*$ là một nghiệm tối ưu của bài toán, thì khi đó tồn tại một giá trị $\mu^*\geq 0$ sao cho $(x^*, \mu^*)$ là một điểm yên ngựa của hàm $\mathcal{L}(x,\mu)$.

**TODO**: Nhắc lại kiến thức + vấn đề điều kiện cần và đủ.

## Bài toán 1

Bây giờ ta tìm cách giải quyết dựa trên điều kiện KKT. Ở đây ta có 2 cách giải, đầu tiên là bám theo hướng giải quyết của [Duchi et al.](https://ai.stanford.edu/~jduchi/projects/jd_ss_ys_l1.pdf)

## Bài toán 2

Tổng quát hóa bài toán 1 lên một tí, ta xét thêm rằng mỗi chiều lại có một trọng số riêng, chẳng hạn như trong động lực 2, chi phí giao dịch trên mỗi đơn vị khối lượng cổ phiếu của mỗi mã lại khác nhau tùy vào mức độ thanh khoản của các mã đó.

$$
\text{minimize } f(w)=\frac{1}{2}||\bold{w}-\bold{v}||^2_2
$$
$$
\begin{align*}

\text{ subject to  } & \sum_{i=1}^n w_i\leq c, \\
& w_i\geq 0, v_i\geq 0, a_i\geq 0

\end{align*}
$$

## Bài toán 3

Vì một lý do khá kì cục mà mình đã phải giải quyết bài toán này với một điều kiện phụ nữa, đó là $\mathcal{L}_1$-norm của $\bold{w}$ và $\bold{v}$ đều bằng nhau và bằng $z$.

**TODO**: viết nốt