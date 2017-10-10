###############data#####################################    
set.seed(1000)
lambda.true = 0.25
a.true = 7
nobs = 40

x= a.true + rexp(n=nobs,rate=lambda.true)
# x = a sample of 40 observations from the translated exponential law

#We use this sample as if we didn't know the parameter of the law.
#The purpose is to find the parameters with the Gibbs sampler algorithm.

#######################################################
####         Algorithme de Gibbs-Sampler          #####
#######################################################

n=nobs
x.mean=mean(x)
x.min=min(x)


sample.a=function(n,lambda, x.min)
  {
  result=x.min - rexp(1, n*lambda)
  return(result)
  }


sample.lambda=function(n, x.mean, a)
  {
  result=rgamma(1,n,n*(x.mean-a))
  return(result)
  }

gibbs.exponentielle_decalee = function(N, n, x)
{
  x.mean=mean(x)
  x.min=min(x)

  a.gibbs = as.vector(rep(NA, N))
  lambda.gibbs = as.vector(rep(NA, N))  
  a.bayes = as.vector(rep(NA, N))
  lambda.bayes = as.vector(rep(NA, N))
  
#Initialisation
  lambda=0.9


  for (i in 1:N)
    {
    a = sample.a(n, lambda, x.min)
    lambda=sample.lambda(n, x.mean,a)
    
    a.gibbs[i]=a
    lambda.gibbs[i]=lambda
    a.bayes[i]=mean(a.gibbs[1:i])
    lambda.bayes[i]=mean(lambda.gibbs[1:i])
    }
  return(list(a.gibbs, lambda.gibbs, a.bayes, lambda.bayes))
}

#N = number of iterations
N=100
resutat.gibbs=gibbs.exponentielle_decalee(N ,n, x)

a.post=unlist(resutat.gibbs[1])[1:N]
lambda.post=unlist(resutat.gibbs[2])[1:N] 

a.bayes=unlist(resutat.gibbs[3])[1:N] 

lambda.bayes=unlist(resutat.gibbs[4])[1:N]
plot(a.post, type="l", col="blue",
ylab="a (a posteriori)", xlab="Iterations", main="Values of the Parameter a")

plot(lambda.post, type="l", col="blue",
ylab="Lambda (a posteriori)", xlab="Iterations", 
main="Values of the Parameter Lambda")

plot(a.bayes, type="l",col="blue", 
ylab="Bayesian Estimator", xlab="Iterations", 
main="Bayesian Estimator of the Parameter a")

plot(lambda.bayes, type="l", col="blue",
ylab="Bayesian Estimator", xlab="Iterations", 
main="Bayesian Estimator of the Parameter Lambda")
