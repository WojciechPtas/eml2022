---
geometry: margin=2.5cm
header-includes: |
        \usepackage{amsmath}
---

**Authors: Wojciech Ptaś (7042843), Mhd Jawad Al Rahwanji (703890)**



# Problem 2


## 1.

The probability of $j$th observation being the first bootstrap observation is equal to $\frac{1}{n}$ because of the uniform distribution. The probability of a complementary event is then equal to $1-\frac{1}{n}$

## 2.

The probability of $j$th observation being in the bootstrap sample $k$ times can be obtained with binomial distribution:

$P=\binom{n}{k}p^k(1-p)^{n-k}$

In this case $k=0$ and $p=\frac{1}{n}$ (as we use uniform distribution), so the probability of the given event can be expressed as:

$P=\frac{n!}{0!*n!}(\frac{1}{n})^0(1-\frac{1}{n})^n=$  
$=(1-\frac{1}{n})^n$ 

Which was to be demonstrated.

## 3.

As the value of $n$ increases, the probability from 2.1 converges to 1:
$\lim_{n \to \inf}1-\frac{1}{n}=1$
Whereas the probability obtained in 2.2 converges to $e^{-1}\approx0.368$
$\lim_{n \to \inf}(1-\frac{1}{n})^n=e^{-1}$