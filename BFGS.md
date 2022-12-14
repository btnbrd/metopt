# BFGS Description

The classic Newton method approximates the function to be optimised <img src="https://render.githubusercontent.com/render/math?math=f"> as a quadratic using the Taylor series expansion: 


  <img src="https://render.githubusercontent.com/render/math?math=f(x %2B \alpha p)=f %2B \nabla f^T p %2B 1/2 p^T \nabla ^2fp">

By minimising this function with respect to <img src="https://render.githubusercontent.com/render/math?math=p"> the optimal search direction <img src="https://render.githubusercontent.com/render/math?math=p"> can be found as: 

  <img src="https://render.githubusercontent.com/render/math?math=-\nabla ^2f^{-1}\nabla f">

The step length <img src="https://render.githubusercontent.com/render/math?math=a"> is then computed via a backtrack linesearch using Wolfe conditions that assure sufficient decrease.

The inverse of the Hessian <img src="https://render.githubusercontent.com/render/math?math=-\nabla ^2f^{-1}"> is computationally expensive to compute due to both finite difference limitations and the cost of inverting a particularly large matrix. For this reason an approximation to the inverse of the Hessian is used <img src="https://render.githubusercontent.com/render/math?math=H">.
This approximation is updated at each iteration based on the change in <img src="https://render.githubusercontent.com/render/math?math=x"> and the change in <img src="https://render.githubusercontent.com/render/math?math=\nabla f"> as follows: 

<img src="https://render.githubusercontent.com/render/math?math=H_{k+1} = (I-\frac{sy^T}{y^Ts})H(I-\frac{ys^T}{y^Ts}) %2B \frac{ss^T}{y^Ts}">



