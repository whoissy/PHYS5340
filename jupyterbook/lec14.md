# lec14

:::{note}
This is **NOT** the official course PHYS5340 website yet!

* If you are student in this course, **always** take the lecture notes as the correct one if you find any differences between lecture notes and website contents
* If you are just passerby, use the materials below at your own risk. Since the website is still the first version (even alpha version), there could be some typos, incorrect/inaccurate/improper statements.
:::

:::{note}
**All** materials in this website are based on the course offered at HKUST
:::

:::{note}
As a "casual course", we provide only general references but not specific ones to the materials introduced
:::

:::{note}
**All** materials' copyright in this website are reserved for the course lecturer

* If you want to use the material somewhere, you might need to contact the lecturer first
:::

:::{note}
Contribution is always **welcome**. if you find any typo, incorrect/inaccurate/improper statements or necessary references, do not hesitate to

* raise an issue on github repo
* make an pull request on github repo
* contact me directly
:::

20220323

Topics

1. Recap of what we have learnt
2. Adiabatic turning on, Gell-Mann-Low theorem
3. Primer into interacting electrons

Goals

1. Introducing many-body perturbation theory
2. Setting up methods for treating interacting electrons

## Recap: what have we learnt so far?

Today happens to be the mid-way point of our course: let's quickly recap what we've covered

![lec14-fig00](data/fig/lec14-fig00.png)

## Adiabatic turning on & Gell-Mann-Low Theorem

Suppose we have a Hamiltonian

$$ \hat{H}=\hat{H}_0+\hat{V}$$

where we view $\hat{V}$ as a perturbation and $\hat{H}_0$ defines the "unperturbed" problem. As the name suggests, we consider the scenario in which the unperturbed problem is solvable, such that we can attempt to systematically add the corrections from $\hat{V}$ to our physical observables. The typical setup is that $\hat{H}_0$ is a free theory (with Gaussian ground states), and $\hat{V}$ is an interaction. We will refer to $\hat{V}$ as the "interaction" as such.

One clever trick for developing such a perturbation theory is to imagine turning on the perturbation $\hat{V}$ "slowly". Imagine modifying our Hamiltonian into (in Schrodinger picture)

$$ \hat{H}\left( t \right) =\hat{H}_0+e^{-\left| t \right|/\tau}\hat{V}$$

such that it interpolates from $\hat{H}_0$ to $\hat{H}=\hat{H}_0+\hat{V}$ as go from $t=-\infty$ to $t=0$, and interpolates back to $\hat{H}_0$ as we further send $t\to +\infty$

![lec14-fig01](data/fig/lec14-fig01.png)

Now, let us suppose we start with the ground state $|\Omega_0\rangle$ of $\hat{H}_0$ at $t\to -\infty$. In the Schrodinger's picture, the state evolve according to

$$ i\partial _t|\Omega \left( t \right) \rangle =\hat{H}\left( t \right) |\Omega \left( t \right) \rangle $$

with the initial value

$$ |\Omega \left( -\infty \right) \rangle =|\Omega _0\rangle $$

We (probably) don't know how to solve the time-evolution of the state exactly. If we knew, we could have solved $\hat{H}$ directly! Instead, let us imagine plotting the many-body eigen-energies as a function of $t$:

![lec14-fig02](data/fig/lec14-fig02.png)

**Suppose** the excitation gap remains finite for all values of $t$. This sets a timescale

$$ \tau _A\sim \frac{1}{\min \left( \Delta E\left( t \right) \right)}$$

The adiabatic theorem then states that, so long as the dynamics in $\hat{H}(t)$ is slow compared to $\tau_A$, i.e., $\tau\gg \tau_A$, then our "black dot" stays in the lowest branch to good approximation.

Heuristically, this could be understood from energy considerations: to transit from the ground state to the excited state, we need to supply energy, In our setup, the only possible energy source is the dynamics in $\hat{H}(t)$, with scale set by $1/\tau$. If we keep that arbitrarily slow, i.e., take $\tau\to \inf\infty$, then we are not giving energy to the system to make a transition to the excited states. In other words, we stay in the instantaneous ground state.

We caution that the adiabatic limit is tricky for two reasons

1. For a many-body system in the thermodynamic limit, there may be gapless excitations directly above the ground state. As such there is no reason to expect the adiabatic theorem to hold at all. However, one might imagine circumventing the difficulty by considering a finite system and taking the adiabatic limit first, before taking the thermodynamic limit. In practice, of course, these are subtle problems, and we will not address them carefully here.
2. More importantly, the interaction may be strong enough that a quantum phase transition occurs as we crank the interaction strength up to its full value. Such quantum phase transitions are characterized by a crossing of the energy levels as a function of the interpolation time $t$. In that case, the adiabatic theorem also fails. And, indeed, one should not hope to get a satisfactory perturbation theory starting from a "wrong" $\hat{H}_0$!

Setting the subtleties aside, let us now consider taking expectation values (with a goal of finally computing some physical observables). We can choose to work in the Heisenberg picture of $\hat{H}(t)$, and consider the time-ordered Green's functions, i.e., quantities of the form

$$ \langle \Omega _H\left( -\infty \right) |\mathcal{T} \left[ \hat{O}_{H}^{\left( 1 \right)}\left( t_1 \right) \hat{O}_{H}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{H}^{\left( n \right)}\left( t_n \right) \right] |\Omega _H\left( -\infty \right) \rangle $$

The motivation for specializing to time-ordered operators will be clear in a moment, and we consider times $t_i$ which remain finite even as $\tau\to\infty$, i.e., we stay near $t=0$ in the adiabatic limit.

In the above, we take advantage of the fact that, in the Heisenberg picture, the state is stationary and all the time-dependence is assigned to the operators. One may for a moment revert back to the Schrodinger picture, supposing for simplicity that $t_1>t_2>\cdots>t_n$ such that the time-ordering does nothing. The quantity we wrote down can be understood as

$$ \langle \Omega _S\left( t_1 \right) |\mathcal{T} \left[ \hat{O}_{S}^{\left( 1 \right)}\left( t_1 \right) \hat{U}_S\left( t_1,t_2 \right) \hat{O}_{S}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{U}_S\left( t_{n-1},t_n \right) \hat{O}_{S}^{\left( n \right)}\left( t_n \right) \right] |\Omega _S\left( t_n \right) \rangle $$

where $\hat{U}_S$ is the time-evolution operator in the Schrodinger picture

$$ \hat{U}_S\left( t_i,t_j \right) =\mathcal{T} \left[ \exp \left( -i\int_{t_i}^{t_j}{dt'\hat{H}_S\left( t' \right)} \right) \right] $$

In the adiabatic limit, for finite times $t_i$, we have

$$ \hat{H}_S\left( t_i \right) \rightarrow \hat{H}$$

$$ |\Omega _S\left( t_i \right) \rangle \rightarrow |\Omega \rangle $$

where $|\Omega\rangle$ denotes the many-body ground state of full Hamiltonian $\hat{H}=\hat{H}_0+\hat{V}$. As such, we see that, in the adiabatic limit, we are simply computing some sort of correlation functions for the interacting ground state.

At the same time, we know that the "initial state"

$$ |\Omega _H\left( -\infty \right) \rangle =|\Omega _S\left( -\infty \right) \rangle =|\Omega _0\rangle $$

is simply the ground state of the unperturbed Hamiltonian $\hat{H}_0$. This connects the "hard problems" of interest (concerning the interacting system) to those in our "simple starting point".

To show this more explicitly, we recall the interaction picture introduced in the last lecture. For our problem, it is natural to use $\hat{H}_0$ to define the dynamics of the operators, such that the interaction-picture operators (for the full problem with adiabatic turning on) evolve in time according to the Heisenberg picture defined with respect to $\hat{H}_0$. Starting from the reference time of $t\to -\infty$, the quantum states evolve in the interaction picture according

$$ |\Omega _I\left( t \right) \rangle =\hat{S}\left( t,-\infty \right) |\Omega _0\rangle $$

$$ \hat{S}\left( t,-\infty \right) =\mathcal{T} \left[ \exp \left( -i\int_{-\infty}^t{dt'\hat{V}_I\left( t' \right)} \right) \right] $$

where $\hat{V}_I(t)$ is the interaction Hamiltonian (perturbation) in the interaction picture. The "S-matrix" is unitary and could be related to backward time evolution

$$ \hat{S}^{\dagger}\left( t_1,t_2 \right) \hat{S}\left( t_1,t_2 \right) =I$$

$$ \hat{S}^{\dagger}\left( t_1,t_2 \right) =\hat{S}\left( t_2,t_1 \right) $$

Now, in computing observables we know that

$$ \langle \Omega _0|\hat{O}_H\left( t \right) |\Omega _0\rangle =\langle \Omega _I\left( t \right) |\hat{S}\left( t,-\infty \right) \hat{O}_H\left( t \right) \hat{S}^{\dagger}\left( t,-\infty \right) |\Omega _I\left( t \right) \rangle $$

$$ \hat{O}_I\left( t \right) =\hat{S}\left( t,-\infty \right) \hat{O}_H\left( t \right) \hat{S}^{\dagger}\left( t,-\infty \right) $$

where the state $|\Omega_0\rangle$ doesn't evolve in the Heisenberg picture. i.e., we have

$$ \hat{O}_H\left( t \right) =\hat{S}^{\dagger}\left( t,-\infty \right) \hat{O}_I\left( t \right) \hat{S}\left( t,-\infty \right) =\hat{S}\left( -\infty ,t \right) \hat{O}_I\left( t \right) \hat{S}\left( t,-\infty \right) $$

Supposing for the moment that $t_1>t_2>\cdots >t_n$, in the interaction picture we have

$$
\begin{align*}
    &\langle \Omega _0|\mathcal{T} \left[ \hat{O}_{H}^{\left( 1 \right)}\left( t_1 \right) \hat{O}_{H}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{H}^{\left( n \right)}\left( t_n \right) \right] |\Omega _0\rangle \\
    =&\langle \Omega _0|\hat{O}_{H}^{\left( 1 \right)}\left( t_1 \right) \hat{O}_{H}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{H}^{\left( n \right)}\left( t_n \right) |\Omega _0\rangle \\
    =&\langle \Omega _0|\hat{S}\left( -\infty ,t_1 \right) \hat{O}_{I}^{\left( 1 \right)}\left( t_1 \right) \hat{S}\left( t_1,-\infty \right) \hat{S}\left( -\infty ,t_2 \right) \hat{O}_{I}^{\left( 2 \right)}\left( t_2 \right) \hat{S}\left( t_2,-\infty \right) \\
    &\quad \cdots \hat{S}\left( t_{n-1},-\infty \right) \hat{S}\left( -\infty ,t_n \right) \hat{O}_{I}^{\left( n \right)}\left( t_n \right) \hat{S}\left( t_n,-\infty \right) |\Omega _0\rangle \\
    =&\langle \Omega _0|\hat{S}\left( -\infty ,t_1 \right) \hat{O}_{I}^{\left( 1 \right)}\left( t_1 \right) \hat{S}\left( t_1,t_2 \right) \hat{O}_{I}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{I}^{\left( n \right)}\left( t_n \right) \hat{S}\left( t_n,-\infty \right) |\Omega _0\rangle \\
    =&\langle \Omega _0|\hat{S}\left( -\infty ,+\infty \right) \mathcal{T} \left[ \hat{S}\left( +\infty ,t_1 \right) \hat{O}_{I}^{\left( 1 \right)}\left( t_1 \right) \hat{S}\left( t_1,t_2 \right) \hat{O}_{I}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{I}^{\left( n \right)}\left( t_n \right) \hat{S}\left( t_n,-\infty \right) \right] |\Omega _0\rangle \\
    =&\langle \Omega _I\left( +\infty \right) |\mathcal{T} \left[ \hat{S}\left( +\infty ,-\infty \right) \hat{O}_{I}^{\left( 1 \right)}\left( t_1 \right) \hat{O}_{I}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{I}^{\left( n \right)}\left( t_n \right) \right] |\Omega _I\left( -\infty \right) \rangle
\end{align*}
$$

when the dust settles, we see that the final expression is independent on the initial time-ordering. In other words, even if the times were ordered differently in the beginning, we still get the same expression at the end. Importantly, all the insertion of the S-matrix can be lumped into a single one going $-\infty$ to $+\infty$. The time-ordering ensures that we break it down into pieces in the actual expression.

The only problem left is that what we have is not an "expectation value" with respect to a given state. This can be fixed by noticing that, in the adiabatic limit, the state $|\Omega_0\rangle$ is both the initial and final state. Yet, in the interaction picture the states have to evolve, and so we can only reconcile the initial and final states up to a phase in the interaction picture:

$$ |\Omega _I\left( -\infty \right) \rangle =|\Omega _0\rangle $$

$$ |\Omega _I\left( +\infty \right) \rangle =\hat{S}\left( +\infty ,-\infty \right) |\Omega _I\left( -\infty \right) \rangle =e^{2i\delta}|\Omega _0\rangle $$

In particular, the phase can be understood as the overlap

$$ \langle \Omega _0|\Omega _I\left( +\infty \right) \rangle =\langle \Omega _0|\hat{S}\left( +\infty ,-\infty \right) |\Omega _0\rangle =e^{2i\delta}$$

$$ \langle \Omega _I\left( +\infty \right) |=e^{-2i\delta}\langle \Omega _0|=\frac{\langle \Omega _0|}{\langle \Omega _0|\hat{S}\left( +\infty ,-\infty \right) |\Omega _0\rangle}$$

Altogether, we conclude

$$
\begin{align*}
    &\langle \Omega _H\left( -\infty \right) |\mathcal{T} \left[ \hat{O}_{H}^{\left( 1 \right)}\left( t_1 \right) \hat{O}_{H}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{H}^{\left( n \right)}\left( t_n \right) \right] |\Omega _H\left( -\infty \right) \rangle \\
    =&\frac{\langle \Omega _0|\mathcal{T} \left[ \hat{O}_{I}^{\left( 1 \right)}\left( t_1 \right) \hat{O}_{I}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{I}^{\left( n \right)}\left( t_n \right) \hat{S}\left( +\infty ,-\infty \right) \right] |\Omega _0\rangle}{\langle \Omega _0|\hat{S}\left( +\infty ,-\infty \right) |\Omega _0\rangle}
\end{align*}
$$

where

$$ \hat{S}\left( +\infty ,-\infty \right) =\mathcal{T} \left[ \exp \left( -i\int_{-\infty}^{+\infty}{dt'\hat{V}_I\left( t' \right)} \right) \right] $$

and the interaction-picture operators evolve according to the Heisenberg picture with respect to $\hat{H}_0$. Furthermore, we end up with an expression involving only the ground-state expectation value of the unperturbed problem. This fulfills our promise of relating the interacting problem to the unperturbed one. The remaining task is "simply" to expand in powers $\hat{V}_I$ and we would get a perturbation series!

Remark: the final expression obtained above is highly reminiscent of what we have learnt in statistics mechanics. Recall, for instance, that the average energy

$$ \left< \hat{H} \right> =\frac{\mathrm{Tr}\left( \hat{H}e^{-\beta \hat{H}} \right)}{\mathcal{Z} \left( \beta \right)}=-\partial _{\beta}\ln \mathcal{Z} \left( \beta \right) $$

This suggests that we can define

$$ \mathcal{Z} \left[ J^{\alpha}\left( t \right) \right] =\langle \Omega _0|\mathcal{T} \left[ \exp \left( -i\int_{-\infty}^{+\infty}{dt'\left( \hat{V}_I\left( t' \right) +J^{\alpha}\left( t \right) \hat{O}^{\alpha}\left( t \right) \right)} \right) \right] |\Omega _0\rangle $$

such that our expression can be simplified further into something like

$$ \frac{\langle \Omega _0|\mathcal{T} \left[ \hat{O}_{I}^{\left( 1 \right)}\left( t_1 \right) \hat{O}_{I}^{\left( 2 \right)}\left( t_2 \right) \cdots \hat{O}_{I}^{\left( n \right)}\left( t_n \right) \hat{S}\left( +\infty ,-\infty \right) \right] |\Omega _0\rangle}{\langle \Omega _0|\hat{S}\left( +\infty ,-\infty \right) |\Omega _0\rangle}\sim \left. \partial _{J_1}\partial _{J_2}\cdots \partial _{J_n}\ln \mathcal{Z} \left[ J^{\alpha}\left( t \right) \right] \right|_{J=0}$$

this is the spirit of a generating functional (c.f. PS3). In any case, we see that a close parallel with statistics mechanics emerges.

## Interacting electrons

Let us be brave and go straight now to a problem of interacting electrons. Consider a fermionic problem with the full Hamiltonian

$$ \hat{H}=\hat{H}_0+\hat{V}$$

$$ \hat{H}_0=\sum_{x,y,\sigma ,\sigma '}{\hat{c}_{x\sigma}^{\dagger}h_{xy}^{\sigma \sigma '}\hat{c}_{y\sigma '}}$$

$$ \hat{V}=\sum_{x,y}{V\left( \left| x-y \right| \right) :\hat{n}_x\hat{n}_y:}$$

where $\hat{n}_x=\sum_{\sigma}{\hat{c}_{x\sigma}^{\dagger}\hat{c}_{x\sigma}}$ denotes the on-site density of the electrons. Notice that the interaction term is normal-ordered, such that

$$
\begin{align*}
    :\hat{n}_x\hat{n}_y:&=\sum_{\sigma \sigma '}{:\hat{c}_{x\sigma}^{\dagger}\hat{c}_{x\sigma}\hat{c}_{y\sigma '}^{\dagger}\hat{c}_{y\sigma '}:}\\
    &=\sum_{\sigma \sigma '}{\hat{c}_{x\sigma}^{\dagger}\hat{c}_{y\sigma '}^{\dagger}\hat{c}_{y\sigma '}\hat{c}_{x\sigma}}
\end{align*}
$$

and the last line holds even if $x=y\;\&\;\sigma=\sigma'$, in which case the term vanishes. This ensures

$$ \hat{V}|0\rangle =0$$

$$ \hat{V}\left( \hat{c}_{x\sigma}^{\dagger}|0\rangle \right) =0$$

i.e., there is no interaction when we have zero or one electron.

Of course, it's quite meaningless if we just state the Hamiltonian and leave it there. Let us attempt to evaluate some physical quantities, say the dielectric function. (The full problem is more complicated, with distinctions between longitudinal vs transverse response and DC versus AC etc. In the following, we only sketch a simplified version of the key points.)

Recall, in a medium the EM scalar potential is modified into

$$ \phi _0\left( r \right) =\frac{\rho _{\mathrm{ext}}}{4\pi \varepsilon _0r}\quad \rightarrow \quad \phi \left( r \right) =\frac{\rho _{\mathrm{ext}}}{4\pi \varepsilon r}$$

In momentum space, we have

$$ \phi \left( q \right) \sim \frac{\rho _{\mathrm{ext}}\left( q \right)}{q^2\varepsilon \left( q \right)}$$

The modification to the dielectric "constant" ( which is $q$ dependent here) can also be understood as a modification of the "true" charge density in the medium, due to the screening from the system. I.e., we can consider

$$ \phi \left( q \right) \sim \frac{\rho _{\mathrm{tot}}\left( q \right)}{q^2\varepsilon _0}$$

$$ \rho _{\mathrm{tot}}\left( q \right) =\rho _{\mathrm{ext}}\left( q \right) +\rho _{\mathrm{sc}}\left( q \right) $$

Comparing the two, we find

$$ \frac{\rho _{\mathrm{ext}}\left( q \right) +\rho _{\mathrm{sc}}\left( q \right)}{\varepsilon _0}=\frac{\rho _{\mathrm{tot}}\left( q \right)}{\varepsilon _0}$$

$$ \Rightarrow \quad \frac{\varepsilon _0}{\varepsilon \left( q \right)}=1+\frac{\rho _{\mathrm{sc}}\left( q \right)}{\rho _{\mathrm{ext}}\left( q \right)}$$

Now, within linear response, the screening charges appear as a response to the external potential

$$ \rho _{\mathrm{sc}}\left( q \right) \sim -\chi \left( q,\omega =0 \right) \frac{\rho _{\mathrm{ext}}\left( q \right)}{4\pi \varepsilon _0q^2}$$

where

$$ \chi \left( q,\omega \right) =i\int_{-\infty}^{\infty}{dt\Theta \left( t \right) \left< \left[ \hat{\rho}\left( q,t \right) ,\hat{\rho}\left( -q,0 \right) \right] \right> e^{i\omega t}}$$

is the density-density response function (maybe up to the sign). This gives

$$ \frac{\varepsilon _0}{\varepsilon \left( q \right)}=1-\frac{\chi \left( q \right)}{4\pi \varepsilon _0q^2}$$

So we could determine the dielectric function by evaluating the density-density response function! But, how do we relate that to the Gell-Mann-Low formula (and hence perturbation theory)?
