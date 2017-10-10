We use our implementation of the Gibbs-Sampler algorithm and analyse its convergence. We try different sample sizes. 

First, we observe results with 100 simulations. Here are the results for the a posteriori parameter a. The different simulations are located around 7. Then we compute the bayesian estimator of the paraemeter a for each iteration, using all the available samples. This means for instance that at the k-st iteration, the bayesian estimator is computed using the k previous iterations with the method of moments. We see that the estimator converges.

We do the same for the lambda parameter. The different simulations are located around 0.27, when the actual value of the parameter is 0.25. 



Then, we observe results with 1000 iterations.  The estimator of a converges to the value 6.96. For lambda, it is 0.27. 

Secondly, we change the number of observations. Before, we just used 40 observations, now it is 500.
In this situation, the simulated values for a are closer to 7. In this case, the bayesian estimator of a converges around 7.00. 

The simulated values for lambda are of the same order of magnitude as before, with 40 observations. The bayesian estimator converges to 0.27. 


When we change the number of observations from 500 to 5000, the bayesian estimator of a converges to 6.99 and the one of lambda is 0.25, really close to the actual value of the parameter. 
