<style>
.bjimg{
  position: fixed;
  top: 0;
  left: 0;
  width:100%;
height:100%;
min-width: 1000px;
z-index:-10;
zoom: 1;
  background-image: url();
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center 0;
  opacity: 0.3;
  }
</style>
<head>    
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
        tex2jax: {
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
        inlineMath: [['$','$']]
        }
});
</script>
</head>
<div class="bjimg"></div>

# 因为要写作业写论文所以没想出什么好topic但是可以水几句bootstrap method不然博客没有一篇分析方向文章太不像PDE废柴了

<font size="2">2024.3.8</font> <br/>
以下是广为人知当然也无处不在的**Grownwall不等式**(没有她可能会饿死很多PDE人罢233

> **定理.** 设连续函数$f:\mathbb{R}\to\mathbb{R}$，可积函数$g:\mathbb{R}\to\mathbb{R}$均恒正. 如果存在$A\geq 0$，对任意$t\in[0,T]$满足
>
$$
f(t)\leq A+\int_{0}^tf(s)g(s)ds,
$$
>
> 那么对对任意$t\in[0,T]$，
>
$$
f(t)\leq A\exp{\int\_0^tg(s)ds}
$$

当然可以直接用微分不等式的方法证明，这是经典的数分习题. 但这里我们采用更冗长——但也更符合Grownwall本性，更普适的**bootstrap method**，即自反馈机制对系统本身的控制. 证明基于一个拓扑事实.

> **引理.** 设拓扑空间$X$连通，则$X$中既开又闭的子集要么是空集，要么是$X$本身.

在定理中$X=[0,T]$. 子集的构造值得思考：对任意$\epsilon>0$，考虑以下条件(induction hypothesis)

$$
f(t)\leq (1+\epsilon)A\exp{((1+\epsilon)\int_0^tg(s)ds}.\tag{B}
$$

定义$O:=\{t\in[0,T]: \forall s\in[0,t], f(s)$满足$(B)\}$，我们希望$O=[0,T]$.<br/><br/>
$0\in O$，所以$O$非空.<br/><br/>
$f(t),\int_0^tg\,ds$连续，所以$O$是闭集.<br/><br/>
开性是证明的关键. 设$t\in O$，我们把$(B)$代入定理的条件：

$$
f(t)\leq A+A\int_{0}^t\exp{(1+\epsilon)\int_0^sg(y)dy}\cdot (1+\epsilon)g(s)ds=A(1+\exp{(1+\epsilon)\int_0^t g(s)ds}-1)
$$

$$
=A\exp{(1+\epsilon)\int_0^t g(s)\,ds}<(1+\epsilon)A\exp{((1+\epsilon)\int_0^tg(s)\,ds}.
$$

由$f$连续性可知存在$\delta>0$, $[0,t+\delta)\subset O$. 所以$O$是开集.<br/><br/>

综上可知$O=[0,T]$，令$\epsilon\to 0$即得到Grownwall不等式. &ensp;$\Box$
