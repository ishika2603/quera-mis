# quera-mis


## Activities:

### Theory
*	Determine the parameters of a quantum algorithm for a neutral atom quantum computer to solve MIS with a unit-disk radius for connectivity larger than king’s.



*	Determine if the parameters above can fit a machine like [Aquila](https://www.quera.com/aquila). If so, generate problem instances on [Bloqade](https://queracomputing.github.io/Bloqade.jl/dev/) that could be run on it.
    +	Extra points for finding if Rb/a=3 is realizable experimentally on Aquila, or what would be the best performant largest value.

### Programming
* Perform simulations using [Bloqade](https://queracomputing.github.io/Bloqade.jl/dev/) on the largest possible system sizes you can. Optimize your protocol to maximize chance of measuring an MIS (optimization methods include [Nelder-Mead](https://queracomputing.github.io/Bloqade.jl/dev/tutorials/5.MIS/main/), [Bayesian methods](https://arxiv.org/pdf/2305.13365.pdf), counter-diabatic methods, or more)
    + Demonstrating higher probability of measuring MIS => more points!
    + Being able to simulate larger systems => more points!
*	Use [generic tensor networks](https://github.com/QuEraComputing/GenericTensorNetworks.jl), [Bloqade](https://queracomputing.github.io/Bloqade.jl/dev/), or your favorite method to estimate the (quantum and classical) annealing hardness parameters of the problem instances you found
    + Finding harder instances => more points!
*   Run jobs of comparative problem instances on Aquila with algorithm of choice and analyze data (no hybrid closed-loop optimization is allowed, so just use classically optimized controls)
    + Larger problems and better chance to solution => more points

### Business
*   Determine an application for MIS in the areas of energy (e.g., power grid networks), biology/health, logistics, or finance.
    + bonus points if your application requires graphs fitting exactly the constraint of the Rb/a=3 type
*   Estimate how many vertices would be necessary for real-life problems. 
    + Bonus points for finding applications that require order near-term numbers of qubits, order few hundreds.