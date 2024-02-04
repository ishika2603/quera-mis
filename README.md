# quera-mis


## Activities:

### Theory
*	Determine the parameters of a quantum algorithm for a neutral atom quantum computer to solve MIS with a unit-disk radius for connectivity larger than king’s.
    + 


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
We riffed off the idea that if two training examples are identical, we don’t need to train on both of them. This leads to redundant information. Therefore, we would benefit from having less training examples as long as the ones we remove are repetitive. This would result in only a mild decrease in accuracy but a massive decrease in computational cost. 

We chose the example of 10,000 images of skin lesions and their diagnoses. There are 5 possible diagnoses including melanoma and benign keratosis legion. We chose this dataset because of how easy it is to get embeddings for images, although with time we can get almost any type of embedding. 

With these embeddings, we do Principal Component Analysis (PCA) to map the embedding vectors onto a 2-dimensional space. Points that are similar to each other will be close in the space. Then, we perform a transformation that takes the scatter to a lattice grid format. This is possible with multiple methods with various degrees of information loss. The method we explored was snapping onto the coordinate grid in a predefined way, but this loses data. The other method we could not explore due to resource constraints is a machine learning model that approximates the best grid spacing, angle of coordinates, and displacement from the origin. This is similar to the images from the following thread: (https://stackoverflow.com/questions/62946604/fitting-an-orthogonal-grid-to-noisy-coordinates). 

Once we snap the points onto a lattice grid, we run MIS on the resulting graph using a neutral atom quantum computer. This gives us the maximum amount of clusters of data such that each cluster is sufficiently unique. The points selected from this algorithm are the training data that we will use on our algorithm, rather than the whole dataset. 

Lastly, we train the model classically using a neural net, showing promising results and a clear improvement even after controlling for training size (we did this by showing that selecting some subset of random points is far worse than selecting the specific subset of points from MIS).

The one flaw of this algorithm is that the upfront cost of running the MIS is high, although this can be reduced by only running MIS on a handful of training examples at a time (so that we are running MIS 1000 times on 1000 training examples rather than 1 time on 1000000 examples). Since MIS is NP-hard and likely takes exponential time, it is beneficial to split the run of MIS into multiple iterations which also makes it easier to run on a quantum computer. With improvements in neutral atom quantum computers, we can use a quantum computer instead of a classical computer to run MIS and therefore speed up the ML training process.
