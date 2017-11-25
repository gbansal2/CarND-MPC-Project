
# Description of the project

# The Model:

The state of the vehicle is defined by the vector - [x, y, psi, v, cte, epsi], where x and y are cartesian coordinates of the vehicle position, psi is orientation of the vehicle, v is the velocity of the vehicle, cte is the cross-track-error, and finally, epsi is the error in orientation with respect to reference trajectory.

The model to update x, y, psi, v, is essentially based on equations of motion, which are given by:

x = x0 + v * cos(psi) * dt

y = y0 + v * sin(psi) * dt

psi = psi0 + v/Lf * delta0 *dt

v = v0 + a0 * dt

The actuators consist of delta - steering angle, and a - throttle. 

The cte and epsi are defined as:

cte = f(x) - y

epsi = psi - psi_des

Here, f(x) is the reference trajectory which is a polynomial fit of order 3. psi_des is the desired orientation of the reference trajectory, which is given by f'(x).

The other key component of the model is the cost. I evaluated cost as the sum of the following:

1. cte^2
2. epsi^2
3. (v-v_ref)^2

## Choice of T, N, and dt

The parameters N and dt are tuned in the project. T is the horizon and is given by the product of N and dt. T is not directly set.

I set N = 250, and dt = 0.005

The effect of a large N is to increase the horizon, however, it comes at increased computational cost. I noticed that a large value of N resulted in significant lag in transmitting the actuations back to the simulator which degraded the control. 
I set N to be as high as possible without causing too much computational overhead. 

The value of dt was chosen small enough such that the effects of discretization error were reduced. A too small dt will reduce the horizon. A lower value of dt was needed at increased reference velocity.





