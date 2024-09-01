# <b>Gradient Descent for Optimization </b>
## <b><u>Introduction
### Gradient descent is an algorithm used to the find local minima of any differentiable function. More formally, given a differentiable function $f(x),$ the gradient descent algorithms helps us compute $x^*$ such that $f'(x^*) = 0$ and $x^*$ is a minimum of $f(x).$ A function can have many local minima $x_{1}^{*}, x_{2}^{*}, \ldots, x_{k}^{*},$ the gradient descent algorithm will converge to one of them depending on the its starting position and learning rate (discussed below). 

### The name "Gradient Descent" hints at how this algorithm works. The algorithms requires 1) knowing the $\textbf{gradient}$ (partial derivatives) of the function and 2) using the gradient to determine the direction of steepest $\textbf{descent}.$ The idea is that we will begin somewhere on the function, for example $f(x_{1})$, and then climb down the function as quickly as possible towards the first valley (local minimum) where $f'(x^*) = 0.$ The gradient descent algorithm essentially describes the sequence of steps to take to go from $x_{1}$ to a local minimum $x^*.$

### Gradient descent (or a variation) is very commonly used to train machine learning models by minimizing some objective function. Many of the objective functions in machine learning are hard to minimize analytically, but we can approximate the minimum using gradient descent. <br>

## <b><u>Algorithm intuition </u></b>

### Suppose we have a single variable function $f(x)$ that has a single global minimum (for example a parabola that opens upwards) at $x^*.$ Our goal is to approximate $x^*$ through an iterative algorithm. The first step is to pick a starting point (initial value) for the algorithm, $x_{1}.$ We will randomly guess $x_{1}$ and note that either $x_{1} < x^*$, or $x_{1} > x^*$ (we can get really lucky and have $x_{1} = x^*,$ but this is very unlikely). Since $x^*$ is the global minimum, we know that $f(x^*) < f(x_{1}),$ that is our starting point is above the minimum. Starting at $x_{1}$ we want to take a sequence of steps to get down to $x^*.$ The gradient descent algorithm characterizes the set of steps to take to get from $x_{1}$ down to $x^*.$

### Without loss of generality assume our starting position $x_{1} < x^*,$ and let us discuss how to get down towards $x^*.$ Recall that we can compute the gradient of $f(x)$ since we assume the function is differentiable. Suppose we find $f'(x_{1}) < 0,$ that indicates that if we take a step right to $x_{2} > x_{1}$ then we will move down the function since $f(x_{2}) < f(x_{1}).$ This is exactly what we want (moving down the function), so we want to take a step to the right of $x_{1}.$ But how large of a step should we take? Well it makes sense to say the step size will depend on the steepness of the descent. The steeper the descent at $x_{1}$, the larger the step size should be as it indicates we have a long way to go before getting to the minimum. More formally the step size will be proportional to the gradient at $x_{1}.$

### Once we get from $x_{1}$ to $x_{2}$, we repeat the same logic as above. Suppose $f'(x_2) < 0$ again, so we need to take a step towards $x_{3} > x_{2}$ to further go down the function. Again our step size will be proportional to $f'(x_2).$ Repeating this process will result in a sequence of steps $x_{1}, x_{2}, \ldots, x_{T}.$ For large values of $T$ we expect $x_{T} \approx x^*.$ The diagram below more formally describes the intuition behind gradient descent.<br>

![image](https://github.com/user-attachments/assets/83444749-b527-445e-9f62-306b68825542)

### The diagram above formally shows a single step of the gradient descent algorithm from $x_{1}$ to $x_{2}$ To determine $x_{2}$ we take a step to the right of $x_{1}$ that is proportional to $f'(x_{1}).$ Mathematically speaking, the sign of $f'(x_{1})$ indicates the direction of the steepest ascent at $x_{1}$ (magnitude of $f'(x_{1})$ is measure of steepness), but since we want to descend (its called gradient $\textbf{descent}$) we use $-f'(x_{1}).$ Gradient descent relies on a parameter $\lambda$ called the learning rate<br>

### <b>Learning rate </b>

### The learning rate $\lambda$ and the steepest descent $-f'(x_{1})$ together determine the step size towards the minimum. Hence the learning rate determines the size of the steps. If $\lambda$ is large then we will take large steps down towards to the minimum. Similarly if $\lambda$ is small it will take longer to converge towards the minimum as the step size is smaller. Does this mean we should pick a really large $\lambda$ to coverge fast towards $x^*?$ No, this is not a good idea. $\lambda$ too large or too small can cause covergence problems as illustrated by the diagram below.<br>
![image](https://github.com/user-attachments/assets/b7beb0c5-8034-4ebd-8833-ad0911a0b6a3)
