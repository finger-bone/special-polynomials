---
sidebar_position: 4
---

# Rodrigues 公式

## 复习

在物理中解方程时，我们一般只关注，

1. 解可以被多项式表示时，本征值的要求
2. 解的具体内容

如果要求本征解是可积函数，那么它一定可以被展开为多项式。而多项式空间总可以由幂函数张成。理论上可以将幂函数通过施密特正交化得到一组新的基作为本征解，且第 $n$ 个基地没有高于 $n$ 次的项。再利用完备性，展开 $x|n\rangle$ ，通过对比幂次得到递推公式。

不过其实但是并没有人要求我们只能展开 $x|n\rangle$ ，我们完全可以展开，

$$
\frac{\mathrm{d}}{\mathrm{d}x}|n+1\rangle
$$

因为它也是多项式，而且首一规定下，这个多项式最高次系数是 $n$ ，一定的一样可以找到一个递推式。积分积回去之后再待定一个常数就可以了。这也算是另一个推导方法了。

不论如何，我们一定能得到一个递推公式和本征值的可能取值。这样我们理论上完整地解出来了微分方程——但是递推公式总觉得不太好。

下面我们会给出一种更好的方法，即基于厄米算子的方法直接推出 Rodrigues 公式。

## Rodrigues 公式

我们先写一下公式，看一下我们要推的结论。

如果我们有，

$$
h D^2y + \frac{(hw)'}{w} Dy = \lambda y
$$

且其中，

$$
\frac{(hw)'}{w}
$$

是不超过一次的多项式，且，

$$
h
$$

是不超过二次的多项式，且，

$$
h(\sup)w(\sup) = h(\inf)w(\inf) = 0
$$

那么，那么它的多项式解是，

$$
y_n = \frac{1}{w} (\frac{\mathrm{d}}{\mathrm{d}x})^n(h^n w)
$$

对，就是如此简单……

下面我们介绍上面公式的证明，内容部分参考下面这位作者的文章。

https://zhuanlan.zhihu.com/p/438490439

## Rodrigues 形式

我们把，

$$
h D^2y + \frac{(hw)'}{w} Dy = \lambda y
$$

暂且叫做 Rodrigues 形式 （我自己瞎起的名）。这个形式的优势是右侧没有权函数，但是也正是因为右侧没有权函数，定义一个带权的内积空间就显得很突兀了。

前面我们的形式都是，

$$
py'' + qy' + ry = \lambda w y
$$

Rodrigues 形式除了次数要求外，唯一要求是 $r=0$ 。

:::tip

如果有 $r$ ，其实是可以做变换消去的。考虑，

$$
y = u\phi
$$

那么，

$$
pu\phi'' + (pu'+qu) \phi' + (pu'' + qu' + r) \phi = \lambda u w \phi
$$

取，

$$
pu'' + qu' + r = \lambda_r w u
$$

即我们找到一个特解即可消去。

:::

同时，注意，带权内积空间下，厄米条件保持不变，因为，

$$
p D^2y + q Dy = \lambda w y
$$

的厄米条件是，

$$
qw = (pw)'
$$

而对于，

$$
h D^2y + \frac{(hw)'}{w} Dy = \lambda y
$$

相当于是 $w=1$ ，此时要求，

$$
w \frac{(hw)'}{w} = (hw)'
$$

这个条件总是成立，因此左侧的算子依然是厄米的。

## Rodrigues 公式

现在我们有方程，

$$
h D^2y + \frac{(hw)'}{w} Dy = \lambda y
$$

这里最重要的观察是，如果我们对上面的公式两侧同时求导，如果将 $y'$ 作为求解函数，右侧依然是本征值的形式。但左侧算子会变化。

$$
h D^2y + \frac{(hw)'}{w} Dy = \lambda y
$$

两侧同时求导为，

$$
h D^2 y' + (Dh + \frac{(hw)'}{w}) Dy' + D(\frac{(hw)'}{w}) y' = \lambda y'
$$

此时如果有，

$$
\frac{(hw)'}{w}
$$

是一次的，或者说，

$$
D(\frac{(hw)'}{w}) = \mu
$$

那么方程的形式在求导后是不变的，即，

$$
h D^2 y' + (Dh + \frac{(hw)'}{w}) Dy' = (\lambda - \mu) y'
$$

同时注意，

$$
Dh + \frac{(hw)'}{w} \\
= \frac{(hw)' + h'w}{w} \\
= \frac{(h^2w)'}{hw}
$$

因此最后方程是，

$$
h D^2 y' + \frac{(h^2w)'}{hw} Dy' = (\lambda - \mu) y'
$$

这相当于对于方程，

$$
h D^2y + \frac{(hw)'}{w} Dy = \lambda y
$$

做了如下的代换，

$$
h_2 = h_1 \\
w_2 = h_1w_1 \\
\lambda_2 = \lambda_1 - \mu_1 \\
y \rightarrow y'
$$

注意，迭代后 $\mu$ 的值会发生变化，具体而言，

$$
\mu_2 = D(Dh + \frac{(hw)'}{w}) = D^2h + \mu_1
$$

因此如果方程形式要保持不变，即一阶的特征多项式保持一次，那么二阶的特征多项式必须是不高于二次的。

我们记，

$$
\eta = D^2 h
$$

因此再加一条代换规则，

$$
\mu_2 = \mu_1 + \eta
$$

此外注意到，上面的方程可以写成一个更方便的形式，即，

$$
\lambda w y = D(hwy')
$$

那么如果给定 $y'$ ，我们是可以很简单地得到 $y$ 的。

我们知道方程的收敛解一定是多项式，因此我们总可以执行上面的代换 $N$ 次（即多项式的次数），最后得到一个 $y$ 的 $nN$ 次导，这是的解是常数，然后将解逐次迭代上去。

:::tip

注意，下面的脚标表示迭代次数。

:::

下面我们将，

$$
h_2 = h_1 \\
w_2 = h_1w_1 \\
\mu_2 = \mu_1 + \eta \\
\lambda_2 = \lambda_1 - \mu_1 \\
y \rightarrow y'
$$

迭代 $n$ 次，有，

$$
h_n = h_1 \\
w_n = h_1^n w_1 \\
\mu_n = \mu_1 + n \eta \\
\lambda_n = \lambda_1 - \sum_{i=1}^{i=n}\mu_i = \lambda_1 - n\mu_1 - \frac{n(n-1)}{2}\eta \\
y_n \rightarrow D^n y
$$

因此，此时的方程为，

$$
\lambda_n h^n w D^n y = D(h^{n+1} wD^{n+1} y)
$$

或者，更好地，

$$
h^n w D^n y = \frac{1}{\lambda_n} D(h^{n+1} wD^{n+1} y)
$$

这个式子可以从高次迭代回低次，因为考察，

$$
h^{n-1} w D^{n-1}y = \frac{1}{\lambda_{n-1}} D(h^{n} wD^{n} y)
$$

注意到低一次的右侧导数算子里的内容和高一次左侧是完全一致的，因此，

$$
wy = (\prod_{i=0}^{i=n} \frac{1}{\lambda_i}) D^{n+1}(h^{n+1} wD^{n+1} y)
$$

如果我们要求第 $N$ 次第多项式，显然我们使用，

$$
wy = (\prod_{i=0}^{i=N-1} \frac{1}{\lambda_i}) D^N(h^{N} wD^{N} y)
$$

此时，对应的方程是，

$$
\lambda_N h^N w (D^N y) = D^N(h^{N+1} wD(D^{N} y))
$$

因为 $y$ 是 $N$ 次多项式，因此记，

$$
D^N y = C_N \neq 0
$$

此时有，

$$
\lambda_N C_N h^Nw = 0
$$

因此，

$$
\lambda_N = 0
$$

:::tip

注意，这一项零没有出现在分母上，分母上至多只用到 $\lambda_{N-1}$ 。

:::

而，

$$
C_N
$$

的选取是任意的。后面我们会看到，它会影响我们的归一系数。

如果使用首一约定，即，

$$
C_N = n!
$$

那么，

$$
wy = n! (\prod_{i=0}^{i=N-1} \frac{1}{\lambda_i}) D^N(h^{N} w)
$$

但是这样不太好看，我们通常是使用，

$$
C_N (\prod_{i=0}^{i=N-1} \frac{1}{\lambda_i}) = 1
$$

此时，

$$
wy = D^N(h^N w)
$$

或者说，

$$
y = \frac{1}{w} D^N(h^N w)
$$

这就是 Rodrigues 公式。

:::tip

下面的脚标代表第 $n$ 个本征值。

:::

此时，最高次系数为，

$$
\frac{C_N}{n!} = \frac{1}{n!} (\prod_{i=0}^{i=N-1} \lambda_i)
$$

其中，

$$
\lambda_i
$$

是迭代中的本征值，

$$
\lambda_m = \lambda_N - m \mu_1 - \frac{m(m-1)}{2} \eta
$$

函数的本征值是，

$$
\lambda_N = N\mu_1 + \frac{N(N-1)}{2} \eta
$$

这就是 Rodrigues 公式对于二阶二次厄米算子本征值问题的收敛解——非收敛解可以由收敛解构造出来。

因为 Rodrigues 形式和原本的算子形式是完全等价的，因此正交性是一定保持的。不过下面我们算一下归一系数。

## 归一性

:::tip

下面的脚标代表第 $n$ 次迭代。

:::

$$
wy = D^n(h^n w)
$$

开算就行，

$$
\int_{\inf}^{\sup} wyy \mathrm{d}x \\
= \int_{\inf}^{\sup} y D^n(h^nw) \mathrm{d}x \\
= B - \int_{\inf}^{\sup} DyD^{n-1}(h^nw) \mathrm{d}x
$$

边界项，

$$
B = (yD^{n-1}(h^nw))|^{\sup}_{\inf}
$$

注意，前面我们限定了， 

$$
h
$$ 

不超过二阶。

$$
\frac{(hw)'}{w}
$$ 

不超过一阶，如此迭代出的， 

$$
\frac{D^{n-1}(h^{n}w)}{h^{n-1}w}
$$ 

也不超过一阶，即，

$$
\frac{D^{n-1}(h^{n}w)}{h^{n-1}w} = ax + b
$$ 

因此，

$$
B = (y(ax+b)(h^{n-1}w))|^{\sup}_{\inf}
$$

前面我们要求了，

$$
p(\sup)w(\sup) = p(\inf)w(\inf) = 0
$$

因此，

$$
B = 0
$$

$$
\int_{\inf}^{\sup} wyy \mathrm{d}x \\
= \int_{\inf}^{\sup} y D^n(h^nw) \mathrm{d}x \\
= - \int_{\inf}^{\sup} DyD^{n-1}(h^nw) \mathrm{d}x
$$

我们可以继续迭代，直到，

$$
\int_{\inf}^{\sup} wyy \mathrm{d}x \\
= (-1)^n \int_{\inf}^{\sup} D^ny(h^nw) \mathrm{d}x \\
= (-1)^n C_N \int_{\inf}^{\sup} h^nw \mathrm{d}x
$$

因此归一系数的分母是，

$$
\sqrt{(-1)^n C_N \int_{\inf}^{\sup} h^nw \mathrm{d}x}
$$

:::tip

这里根号下保证是恒正的，因为 $w$ 是正定的。这里的结果形式上出现了 $(-1)^n$ 其实反而保证了正定性。

:::

## 生成函数

现在我们可以给出一个通用的生成函数了。

Rodrigues 公式告诉我们，

$$
y_n = \frac{1}{w} D^n(h^n w)
$$

逆用柯西积分公式，可以得到，

$$
y_n = \frac{n!}{2\pi i}\frac{1}{w(x)} \oint_{C(x)} \frac{h^n w}{(t-x)^{n+1}} \mathrm{d} t
$$


:::tip

分子上的 $w$ 是关于 $t$ 的，而分母上的 $w$ 是关于 $x$ 的。下文没写自变量默认是关于 $t$ 的。

:::

显然，做变换，

$$
u = \frac{t-x}{h(t)}
$$

得到，

$$
y_n = \frac{n!}{2\pi i} \oint_{C(x)} \frac{w \frac{\mathrm{d}t}{\mathrm{d}u}}{w(x)h} \frac{1}{u^{n+1}}  \mathrm{d} u
$$

根据生成函数的定理，生成函数就是，

$$
G(x; u) = \frac{w \frac{\mathrm{d}t}{\mathrm{d}u}}{w(x)h}
$$

因为 $u$ 和 $t$ 是隐函数关系，这里的生成函数不方便写开。不过，一般直接代入是很好求的，比如对于厄米多项式，

$$
h(t) = 1 \\
w(x) = \exp(-x^2 / 2)
$$

那么，

$$
u = t - x
$$

$$
\frac{\mathrm{d}t}{\mathrm{d}u} = 1
$$

$$
w(t) = \exp(-(u+x)^2/2)
$$

因此，

$$
G(x; u) = \exp(-xu-u^2/2)
$$

## 总结

我们推导了二阶二次厄米算子的带权本征方程 Rodrigues 公式与相关结果。下一章我们随便捉几个物理问题，来看下我们建立的体系为什么比靠猜测和展开的方法要容易多
