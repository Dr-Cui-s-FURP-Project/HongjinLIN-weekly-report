# 3.20-4.3

# Issac Sim Tutorial
I  've finished reading and trying the tutorial from the start to 2.4


# KF and EKF 
## Kalman Filter (KF) 
What is KF?
- Algorithm used for estimating the state of a linear dynamic system from a series of noisy measurements. (an optimal estimation algorithm)
What is a Filter and what does it do?
- Filter is a process or an algorithm that modifies or analyzes a set of data or signals
- Primary purpose: **extract useful information, reducuing unwanted data**
What is linear dynamic system?
- a mathematical model used to describe the behavior of a system whose change over time can be represented as a linear function of its current state and inputs.
	-  Characteristics of Linear Dynamic Systems
		1. **Linearity**
		2. **Dynamic**: The system's behavior changes over time in response to input signals.
What is noise
- "noise" refers to any unwanted or extraneous information that interferes with the ability to accurately discern or measure the desired information or signal.
### State Observation
- When sth cannot be measured directly, use other relevant data and a mathematic model estimate it
- KF is the mathematic model here, or so called Optimal State Estimator.
### Mathematic Equation


#### 1. Prediction

1. **Predict the state**:
    $\hat{x}_k^- = F_k \hat{x}_{k-1} + B_k u_k$
$\hat{x}_{k-1}$ is the priori estimate, 
$F_k$ is the state transition model applied to the previous state 
2. **Predict the estimation error covariance**:
    $$P_k^- = F_k P_{k-1} F_k^T + Q_k$$
$P_k^-$ is the variance of priori estimate
####  2. Update

1. **Compute the Kalman Gain**:
$$K_k = P_k^- H_k^T (H_k P_k^- H_k^T + R_k)^{-1}$$
2. **Update the estimate with the measurement**:
    $$\hat{x}_k = \hat{x}_k^- + K_k (z_k - H_k \hat{x}_k^-)$$
    Use the priori estimate and update them
    $\hat{x}_k$ is a posteriori estimate
    $K_k$ is a weight function
    $K_k (z_k - H_k \hat{x}_k^-)$ is the estimation value
    ==The priori estimate and the optimal estimation together gets the optimal estimation==
3. **Update the error covariance**:
    $$P_k = (I - K_k H_k) P_k^-$$       $P_k$ is the estimation error covariance matrix at time   

What is estimation error covariance matrix?
- This matrix provides a quantitative measure of the uncertainty or error in the estimate of the state of a syste
- The diagonal elements of P represent the variance (a measure of uncertainty) of the estimation error for each state variable. A larger variance indicates greater uncertainty in the estimate of that state variable.
- The off-diagonal elements represent the covariance between the estimation errors of pairs of state variables. These elements indicate how much the errors in estimating one state variable are linearly related to the errors in estimating another state variable.
What is convariance
- Covariance is a statistical measure that indicates the extent to which two variables change together.
-  Covariance vs. Correlation
	- While covariance indicates the direction of the linear relationship between variables, it does not provide information about the strength of this relationship. The reason is that the scale of covariance depends on the scales of the variables, making it difficult to compare across different pairs of variables.

