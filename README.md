# Stiffness and Step Size Control Analysis in Numerical Integrators

## Motivation:

1. Runge-Kutta Integrator Overview: All Purpose Numerical Integration of Differential Equations by Dr. Steve Brunton (https://www.youtube.com/watch?v=HOWJp8NV5xU)
   
2. WKB-based scheme with adaptive step size control for the Schrödinger equation in the highly oscillatory regime (https://arxiv.org/pdf/2102.03107)

## Introduction

In the realm of numerical methods for solving ordinary differential equations (ODEs), the choice of integration scheme profoundly impacts the accuracy and efficiency of simulations, particularly in systems exhibiting chaotic behavior. This investigation delves into the comparison of two prominent numerical integration techniques, namely the 4th Order Runge Kutta (RK4) method and the Runge–Kutta–Fehlberg (RKF45) scheme, within the context of the Lorenz63 system—a canonical model renowned for its chaotic dynamics. The Lorenz63 system, introduced by meteorologist Edward Lorenz in 1963, serves as a paradigmatic example of deterministic chaos, where small variations in initial conditions lead to divergent trajectories. Motivated by the inherent challenges posed by chaotic systems, characterized by sensitivity to initial conditions and varying stiffness, this investigation seeks to evaluate the efficacy of RKF45's adaptive step size control in mitigating numerical errors and capturing the intricate dynamics of the Lorenz63 system. Through a combination of numerical simulations, graphical analysis, and statistical evaluation, this study aims to elucidate the advantages of adaptive integration techniques in accurately simulating chaotic systems, thereby advancing our understanding of their underlying dynamics and informing the design of robust numerical algorithms.

## Background and Inspiration

The Lorenz63 system, characterized by its three coupled nonlinear ordinary differential equations, exhibits chaotic behavior under certain parameter settings. While the RK4 method is widely used for numerical integration, its fixed step size can be inefficient for systems with varying stiffness. In contrast, the RKF45 scheme incorporates adaptive step size control, enabling it to dynamically adjust step sizes based on local error estimates. This adaptability promises to mitigate stiffness-related issues and enhance accuracy in capturing chaotic dynamics.

## Methodology

The investigation utilizes Python's scientific computing ecosystem, leveraging NumPy, SciPy, and Matplotlib for numerical computation, integration, and visualization, respectively. Two custom classes, RK4 and RKF45, are implemented to solve the Lorenz63 system numerically. The RK4 method employs a fixed step size, while the RKF45 scheme dynamically adjusts step sizes to maintain a prescribed error tolerance.
Results and Analysis

The numerical solutions obtained from RK4 and RKF45 are compared graphically using a 3D plot of the Lorenz attractor. Additionally, the deviation between the two solutions is quantitatively analyzed over time. Statistical measures such as maximum deviation, mean deviation, and standard deviation are computed to assess the consistency and accuracy of the RKF45 scheme relative to RK4.

## Code Explanation:
### 1. Lorenz63 Class:
- This class defines the Lorenz63 system with its parameters (rho, sigma, beta) and its derivative function.
- The derivative function computes the time derivatives of the three variables (x, y, z) according to the Lorenz63 equations.

### 2. RK4 Class:
- Implements the 4th Order Runge-Kutta method for numerical integration.
- The solve() method iteratively applies the RK4 scheme to approximate the solution of the ODE system.

### 3. RKF45 Class:
- Implements the Runge-Kutta-Fehlberg (RKF45) method for numerical integration with adaptive step size control.
- The solve() method iteratively applies the RKF45 scheme, dynamically adjusting the step size based on local error estimates.

### 4. Main code:
- Defines parameters for the Lorenz63 system (rho, sigma, beta, initial conditions, time span).
- Creates instances of Lorenz63, RK4, and RKF45 classes.
- Solves the system using both RK4 and RKF45 methods.
- Interpolates the RK4 solution to match the time steps of the RKF45 solution for comparison.
- Plots the solutions in a 3D space and calculates the deviation between RK4 and RKF45 solutions over time.
- Conducts statistical analysis on the deviation.

## Dealing with Stiffness:

Stiffness in ODE systems refers to a situation where there are widely varying time scales, making it challenging to select an appropriate fixed step size for numerical integration. The RK4 method uses a fixed step size throughout the integration process, which may lead to inaccuracies or inefficiencies when dealing with stiff systems.

To address stiffness, the RKF45 method employs adaptive step size control. It dynamically adjusts the step size based on the estimated local error, ensuring that the solution remains accurate while efficiently capturing rapid changes in the system's behavior. This adaptability allows RKF45 to handle stiff systems more effectively compared to fixed-step methods like RK4.

## Results and Insights:

### 1. Graphical Analysis:
- The 3D plot of the Lorenz attractor shows the trajectories obtained from RK4 (in green) and RKF45 (color-coded by time).
- RKF45's trajectories appear smoother and more accurately capture the intricate structure of the attractor compared to RK4, indicating its ability to handle stiffness and capture chaotic dynamics more effectively.
  
### 2. Deviation Analysis:
- The deviation plot illustrates the difference between RK4 and RKF45 solutions over time.
- Statistical measures such as maximum deviation, mean deviation, and standard deviation quantify the discrepancy between the two methods.
- RKF45 generally exhibits lower deviation compared to RK4, indicating its superior accuracy and ability to mitigate stiffness-related errors.
- The dispersion region highlights the variability in deviation, providing insights into the consistency and reliability of each method.

## Conclusion
The results suggest that the RKF45 method, with its adaptive step size control, outperforms the RK4 method in capturing the dynamics of the Lorenz63 system, particularly in chaotic regimes with stiffness. By dynamically adjusting step sizes based on local error estimates, RKF45 effectively compensates for stiffness-related issues, leading to more accurate and reliable solutions. This underscores the importance of adaptive step size methods in numerical integration, especially for systems exhibiting complex behavior like chaos.

## Future Drections
Future investigations may explore the applicability of adaptive step size methods to other chaotic systems or extend the analysis to higher-dimensional systems. Additionally, incorporating advanced techniques such as parallel computing or machine learning-driven adaptive methods could further enhance the efficiency and accuracy of numerical integration in chaotic dynamical systems.

By framing your work within this structured narrative, you effectively communicate your research objectives, methodology, findings, and implications to the scientific community. This approach enhances the clarity and impact of your work, facilitating comprehension and interpretation by readers and collaborators alike.
