---
Layout: post
mathjax: true
comments: true
title:  "Zeta regularisation black magic"
categories: [Mathematics, Physics]
date:  2019-08-04
---

**August 4, 2019.** *A quick technical post on zeta function regularisation.*

## Motivation

*Prerequisites: quantum field theory, path integrals.* 

The partition function of a quantum statistical system is 

## The maths

Define the *Hurwitz function* by

$$
\zeta(s, a) = \sum_{k \geq 0}\frac{1}{(k+a)^s}, \quad a > 0, \quad |\Re(s)| > 1.
$$
	
This is a generalisation of the
[Riemann zeta function](https://en.wikipedia.org/wiki/Riemann_zeta_function)
$\zeta_\text{R}$,
since $\zeta_\text{R}(s) = \zeta(s, 1)$.
Although the definition of the Hurwitz function above blows up at $s = 0$, we can analytically
continue so that it is defined at $s = 0$. From the [DLMF](https://dlmf.nist.gov/25.11) (or otherwise), it obeys

$$
\begin{align}
\zeta(0, a)= \frac{1}{2} - a, \quad \zeta'(0, a) = \ln
\left(\frac{\Gamma(a)}{\sqrt{2\pi}}\right),\label{zeta0}
\end{align}
$$

where $\Gamma$ is the [Gamma function](https://en.wikipedia.org/wiki/Gamma_function).
Consider an operator $\mathcal{X}^a_\xi$
with spectrum $\lambda_k = \xi(k+a)$, $k \in \mathbb{Z}_{\geq 0}$.
We can define the associated *spectral zeta function*

$$
  \begin{align}
    \zeta_\mathcal{X}(s) & = \sum_{k \geq 0} \lambda_k^{-s}\label{zeta1}\\
   & = \sum_{k \geq 0}\frac{1}{\xi^s(k+s)^s} =
      \xi^{-s}\zeta(s, a). \label{zeta2}
  \end{align}
$$
  
We can differentiate (\ref{zeta1}), (\ref{zeta2}) with respect to $s$, and equate them
to get

$$
  \begin{align}
    \zeta'_\mathcal{X}(s) & = -\sum_{k \geq 0}
                            \lambda_k^{-s}\log\lambda_k \label{zeta3}\\ 
   & = \xi^{-s}\zeta'(s,a) - \xi^{-s}\log \xi \cdot \zeta(s,
     a). \label{zeta4}
  \end{align}
$$
  
  From (\ref{zeta3}) and the elementary identity

$$
\det A = \prod_i a_i = e^{\sum_i \log a_i} =  e^{\mathrm{Tr} \log A},
$$

where $a_i$ are the eigenvalues of $A$, we also have

$$
\begin{equation}
    \zeta'_\mathcal{X}(0) = -\sum_{k \geq 0} \log \lambda_k = -\log
    \det \mathcal{X}. \label{zeta5} 
\end{equation}
$$
	
Setting $s = 0$ in (\ref{zeta4}), using (\ref{zeta0}), and equating with (\ref{zeta5}), we find

$$
\begin{align}
    \det \mathcal{X}^a_{\xi} & = \prod_{k=a}  \xi (k+a) \notag \\& = \exp \left[\zeta'(0, a) -
                                     \log \xi
                                \cdot \zeta(0,a)\right] \notag \\
  & = \exp \left[-\ln \left(\frac{\Gamma(a)}{\sqrt{2\pi}}\right) +\log
    \xi\left(\frac{1}{2} - a\right) \right] \notag \\
  & = \frac{\sqrt{2\pi}}{\Gamma(a) }\xi^{1/2-a}. \label{final}
  \end{align}
$$

This is our nice, simple final result!

## Applications

We can use (\ref{final}) to regularise the constants $\mathcal{N}$ in
part (b) and $\mathcal{M}$ bla bla

$$
\begin{align}
    \mathcal{N} & = \big[\det \mathcal{X}^1_{2\pi/\beta}\big]^4 =
    \left[\sqrt{2\pi}\cdot\sqrt{\beta/2\pi}\right]^4 = \beta^2 \label{N}\\
\mathcal{M} & = \big[\det \mathcal{X}^{1/2}_{2\pi/\beta}\big]^2 =
              \left(\frac{\sqrt{2\pi}}{\sqrt{\pi}}\right)^2 = 2.\label{M}
  \end{align}
$$

## References

- *Geometry, Topology and Physics* (2003), Mikio Nakahara.
- *An Introduction to Quantum Field Theory* (1995), Michael Peskin and
Daniel Schroeder.
- *Quantum Field Theory and the Standard Model* (2013), Matthew Schwartz.