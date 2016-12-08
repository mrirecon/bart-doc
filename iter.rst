Iterative Algorithms
====================

Implementation of the operators is separated from the implementation of the iterative algorithm itself and passed as a function pointer. A similar stategy called supermarionation has been described in Murphy et al.


iter interfaces
-------------------

There are three iter interfaces that allow simplified access of the algorithms: iter, iter2, and iter3. The iter interfaces use the :ref:`linop` and :ref:`operatorp`.

The iter interface considers the problem :math:`\min_x \frac{1}{2} \| Ax - y \|_2^2 + g(x)`. It requires :math:`A^\top A`, :math:`A^\top y`, and :math:`\text{prox}_g` as inputs and outputs `x`. The iter interface supports cg, ist, fista and admm. :math:`\text{prox}_g` has to be NULL for cg.

The iter2 interface considers the problem :math:`\min_x \frac{1}{2} \| Ax - y \|_2^2 + \sum_i f_i (G_i x)`. It requires :math:`A^\top A`, :math:`A^\top y`, :math:`\text{prox}_{f_i}`, and :math:`G_i` linops as inputs and outputs `x`. The iter2 interface supports cg, ist, fista and admm. :math:`\text{prox}_{f_i}` has to be NULL for cg. For ist and fista, the number of :math:`\text{prox}_{f_i}` has to be one.

The iter3 interface contains the rest of the algorithms without a unifying interface.


cg
-------

cg implements the conjugate gradient method. It solves for:

.. math::

  \min_x \frac{1}{2} \| Ax - y \|_2^2 + \lambda \| x \|_2^2
  
* Parameters:
  
    Regularization :math:`\lambda` and number of iterations

* Input:
  
    :math:`A^\top A`, and :math:`A^\top y`

* Ouput:
  
    :math:`x`

* Iteration steps:

.. math::
   
   \alpha_k &= \frac{r_k^\top r_k}{p_k^\top (A^\top A + \lambda I) p_k} \\
   x_{k+1} &= x_k + \alpha_k p_k \\
   r_{k+1} &= r_k - \alpha_k (A^\top A + \lambda I) p_k \\
   \beta_k &= \frac{r_{k+1}^\top r_{k+1}}{p_k^\top p_k} \\
   p_{k+1} &= r_{k+1} + \beta_k p_k

ist
--------

ist implements the iterative soft threshold method, also known as the proximal gradient method.
It solves for:

.. math::

  \min_x \frac{1}{2} \| Ax - y \|_2^2 + g(x)

where :math:`g(x)` is simple, that is the proximal of `g(x)` can be computed easily.


* Parameters:
  
      Step-size :math:`\tau` and number of iterations

* Input:
  
      :math:`A^\top A`, :math:`A^\top y`, and :math:`\text{prox}_g`

* Ouput:
  
      :math:`x`

* Iteration steps:

.. math::

   x_{k+1} = \text{prox}_{\tau g} \left( x_k + \tau (A^\top y - A^\top A x_k) \right)



fista
----------

fista implements the fast iterative soft threshold method, also known as the accelerated proximal gradient method. It solves for:

.. math::

  \min_x \frac{1}{2} \| Ax - y \|_2^2 + g(x)

where :math:`g(x)` is simple, that is the proximal of `g(x)` can be computed easily.


* Parameters:
  
      Step-size :math:`\tau` and number of iterations

* Input:
  
      :math:`A^\top A`, :math:`A^\top y`, and :math:`\text{prox}_g`

* Ouput:
  
      :math:`x`

* Iteration steps:

.. math::

   x_{k} &= \text{prox}_{\tau g} \left( z_k + \tau (A^\top z_k - A^\top A z_k) \right) \\
   t_{k+1} &= \frac{1 + \sqrt{1 + 4 t_k^2}} {2} \\
   z_{k+1} &= x_k + \left( \frac{t_k - 1}{t_{k+1}} \right) (x_k - x_{k-1})

   
admm
--------

admm implements the alternating direction method of multipliers. It solves for:

.. math::

  \min_x \frac{1}{2} \| Ax - y \|_2^2 + \sum_i f_i (G_i x - b_i)

where :math:`f_i` s are simple, that is the proximal of each `f_i` can be computed easily.


* Parameters:
  
    Convergence parameter :math:`\rho`, and number of iterations

* Input:
  
     :math:`A^\top A`, :math:`A^\top y`, :math:`\text{prox}_{f_i}`, :math:`G_i`, :math:`G_i^\top`, :math:`G_i^\top G_i`, and :math:`b_i`

* Ouput:
  
      :math:`x`

* Iteration steps:

.. math::

   x   &= \left( A^\top A + \rho \sum_i G_i^\top G_i \right)^{-1} \left( A^\top y + \rho \sum_i G_i^\top (z_i - u_i + b_i) \right) \\
   z_i &= \text{prox}_{f_i / \rho} ( G_i x + u_i - b_i )\\
   u_i &= G_i x + u_i - z
