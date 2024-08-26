============================================
Adding a New Architecture
============================================

.. code-block:: python

    class SimplePSLLoRAModel(SimplePSLModel):

        def __init__(self, n_obj, n_var, lr=1e-3):
            super().__init__(n_obj, n_var)
            #n_obj (int): Number of objectives.
            #n_var (int): Number of variables.
            #lr (float, optional): Learning rate. Default is `1e-3`.
            self.lr = lr
            self.model = nn.Sequential(
                nn.Linear(n_obj, 64),
                nn.ReLU(),
                nn.Linear(64, n_var)
            )

        def forward(self, prefs):
            # Input: prefs (Tensor): Preference matrix of shape `(n_prob, n_obj)`.
            # Output: solution (Tensor): Solution matrix of shape `(n_prob, n_var)`.
            return self.model(prefs)

        def optimize(self, problem, epoch):
            # problem (ProblemClass): The problem class instance to optimize.
            # epoch (int): Number of epochs for optimization.
            optimizer = torch.optim.Adam(self.model.parameters(), lr=self.lr)
            criterion = nn.MSELoss()
            for _ in range(epoch):
                optimizer.zero_grad()
                prefs = problem.evaluate(self.forward)
                loss = criterion(prefs, problem.prefs)
                loss.backward()
                optimizer.step()

        def evaluate(self, prefs):
            # Input: prefs (Tensor): Preference matrix of shape `(n_prob, n_obj)`.
            #Output: decision_variables (Tensor): Decision variables of shape `(n_prob, n_var)`.
            return self.forward(prefs)



