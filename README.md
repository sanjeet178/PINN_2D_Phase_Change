# PINN 2D Phase Change  
This folder contains codes of physics-informed neural network and finite volume code for phase change problems. The details regarding the implementation of the code are presented in the paper.  

# PINN Architecture  
<img width="401" height="181" alt="image" src="https://github.com/user-attachments/assets/e0f20f3c-3b4f-472a-a45c-f5679ff76731" />


- Skip connections are incorporated in the network architecture.  
- The neural network takes **spatial and temporal coordinates** as input.  
- The network outputs the **temperature field** as the prediction.  
- The model is trained using **physics-informed loss functions** derived from governing equations.
- The Gaussian activation function was scaled to both **maintain output values within the desired physical range** (e.g., [0, 1] or [0, 0.3]) and **effectively capture the steep temperature gradients across the mushy–liquid interface** by selecting an appropriate variance in the range [1, 5].

# Loss Function

- The total loss function L is defined as a weighted sum of individual residual losses: L = Kr * Lr + Kub * Lub + Ku0 * Lu0
- Lr represents the physics residual, obtained by substituting the predicted values into the governing partial differential equation (PDE).
- Lub corresponds to the boundary condition residual, ensuring that the predicted solution satisfies all prescribed boundary constraints.
- Lu0 denotes the initial condition residual, enforcing correct initialization of the solution field.
- Kr, Kub, and Ku0 are the weighting coefficients of the residual terms.
- These weighting coefficients allow prioritization of specific residuals over others during training.

# Few Results
<img width="536" height="545" alt="image" src="https://github.com/user-attachments/assets/860128a8-a28e-4c39-8499-5d3c6a53092f" />

- Comparison of PINN temperature contours are made with temperature contours generated from finite volume (CFD) simulations. It can be noticed that results are in good agreement with each other.

# Actual Paper
- Patra, S., Agrawal, M., Rath, P., & Bhattacharya, A. (2025). Physics informed neural network-based framework for two-dimensional phase change problems. Computer Physics Communications, 317, 109854. https://doi.org/10.1016/j.cpc.2025.109854




