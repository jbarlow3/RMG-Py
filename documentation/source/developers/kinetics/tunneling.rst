*********
Tunneling
*********

Wigner tunneling
================

An early formulation for incorporating the effect of tunneling is that of 
Wigner [1932Wigner]_:

.. math:: \kappa(T) = 1 + \frac{1}{24} \left( \frac{h \left| \nu_\mathrm{TS} \right|}{ k_\mathrm{B} T} \right)^2

where :math:`h` is the Planck constant, :math:`\nu_\mathrm{TS}` is the
negative frequency, :math:`k_\mathrm{B}` is the Boltzmann constant, and
:math:`T` is the absolute temperature. 

The Wigner formula represents the first correction term in a perturbative
expansion for a parabolic barrier [1959Bell]_, and is therefore only accurate
in the limit of a small tunneling correction. There are many cases for which
the tunneling correction is very large; for these cases the Wigner model is
inappropriate.

.. autoclass:: rmgpy.kinetics.Wigner
    :members:

    
.. [1932Wigner] E.\ Wigner. *Phys. Rev.* **40**, p. 749-759 (1932). `doi:10.1103/PhysRev.40.749 <http://dx.doi.org/10.1103/PhysRev.40.749>`_

.. [1959Bell] R.\  P.\  Bell. *Trans. Faraday Soc.* **55**, p. 1-4 (1959). `doi:10.1039/TF9595500001 <http://dx.doi.org/10.1039/TF9595500001>`_


Eckart tunneling
================

The Eckart tunneling model is based around a potential of the form

.. math:: V(x) = \frac{\hbar^2}{2m} \left[ \frac{A e^x}{1 + e^x} + \frac{B e^x}{\left( 1 + e^x \right)^2} \right]

where :math:`x` represents the reaction coordinate and :math:`A` and :math:`B` 
are parameters. The potential is symmetric if :math:`A = 0` and asymmetric if 
:math:`A \ne 0`. If we add the constraint 
:math:`\left| B \right| > \left| A \right|` then the potential has a maximum
at

.. math:: x_\mathrm{max} = \ln \left( \frac{B + A}{B - A} \right)

.. math:: V(x_\mathrm{max}) = \frac{\hbar^2}{2m} \frac{(A + B)^2}{4B}

The one-dimensional Schrodinger equation with the Eckart potential is
analytically solvable. The resulting microcanonical tunneling factor 
:math:`\kappa(E)` is a function of the total energy of the molecular system:

.. math:: \kappa(E) = 1 - \frac{\cosh (2 \pi a - 2 \pi b) + \cosh (2 \pi d)}{\cosh (2 \pi a + 2 \pi b) + \cosh (2 \pi d)}

where

.. math:: 2 \pi a = \frac{2 \sqrt{\alpha_1 \xi}}{\alpha_1^{-1/2} + \alpha_2^{-1/2}}

.. math:: 2 \pi b = \frac{2 \sqrt{\left| (\xi - 1) \alpha_1 + \alpha_2 \right|}}{\alpha_1^{-1/2} + \alpha_2^{-1/2}}

.. math:: 2 \pi d = 2 \sqrt{\left| \alpha_1 \alpha_2 - 4 \pi^2 / 16 \right|}

.. math:: \alpha_1 = 2 \pi \frac{\Delta V_1}{h \left| \nu_\mathrm{TS} \right|}

.. math:: \alpha_2 = 2 \pi \frac{\Delta V_2}{h \left| \nu_\mathrm{TS} \right|}

.. math:: \xi = \frac{E}{\Delta V_1}

:math:`\Delta V_1` and :math:`\Delta V_2` are the thermal energy 
difference between the transition state and the reactants and products,
respectively; :math:`\nu_\mathrm{TS}` is the negative frequency, 
:math:`h` is the Planck constant.

Applying a Laplace transform gives the canonical tunneling factor as a function
of temperature :math:`T` (expressed as :math:`\beta \equiv 1 / k_\mathrm{B} T`):

.. math:: \kappa(T) = e^{\beta \Delta V_1} \int_0^\infty \kappa(E) e^{- \beta E} \ dE

If product data is not available, then it is assumed that 
:math:`\alpha_2 \approx \alpha_1`.

The Eckart correction requires information about the reactants as well
as the transition state. For best results, information about the 
products should also be given. (The former is called the symmetric
Eckart correction, the latter the asymmetric Eckart correction.) This
extra information allows the Eckart correction to generally give a
better result than the Wigner correction.

.. autoclass:: rmgpy.kinetics.Eckart
    :members:
