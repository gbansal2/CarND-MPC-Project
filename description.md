
# Description of the project

# The Model:

The state of the vehicle is defined by the vector - [x, y, psi, v, cte, epsi], where x and y are cartesian coordinates of the vehicle position, psi is orientation of the vehicle, v is the velocity of the vehicle, cte is the cross-track-error, and finally, epsi is the error in orientation with respect to reference trajectory.

The model to update x, y, psi, v, is essentially based on equations of motion, which are given by:
x = x0 + v*cos(psi)*dt

y = y0 + v*sin(psi)*dt

psi = psi0 + v/Lf*delta0*dt

v = v0 + a0*dt

The actuators consist of delta - steering angle, and a - throttle. 



