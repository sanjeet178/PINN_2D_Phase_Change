# PINN 2D Phase Change  
This folder contains codes of physics-informed neural network and finite volume code for phase change problems. The details regarding the implementation of the code are presented in the paper.  

# PINN Architecture  
<img width="401" height="181" alt="image" src="https://github.com/user-attachments/assets/e0f20f3c-3b4f-472a-a45c-f5679ff76731" />


- Skip connections are incorporated in the network architecture.  
- The neural network takes **spatial and temporal coordinates** as input.  
- The network outputs the **temperature field** as the prediction.  
- The model is trained using **physics-informed loss functions** derived from governing equations.

# Loss Function
- The total loss function \( L \) is defined as a weighted sum of individual residual losses:
  \[
  L = K_r L_r + K_{ub} L_{ub} + K_{u0} L_{u0}
  \]
- \( L_r \) represents the **physics residual**, obtained by substituting the predicted solution into the governing partial differential equation (PDE).
- \( L_{ub} \) corresponds to the **boundary condition residual**, ensuring that the predicted solution satisfies all prescribed boundary constraints.
- \( L_{u0} \) denotes the **initial condition residual**, enforcing correct initialization of the solution field.
- \( K_r \), \( K_{ub} \), and \( K_{u0} \) are **weighting coefficients** that control the relative importance of each residual term during training.
- These coefficients allow **prioritization of specific physical constraints**, thereby improving convergence and solution accuracy.


