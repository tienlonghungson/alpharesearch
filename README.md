# Status
- Learning phase: working dir is [learn](.\learn), all other dirs are at zero state. 

# Environment setup
1. Create a virtual environment:
   ```
   python -m venv alpharesearch_env
   ```

2. Activate the virtual environment:
- On Windows (PowerShell):
  ```
  alpharesearch_env\Scripts\Activate.ps1
  ```
- On macOS/Linux:
  ```bash
  source alpharesearch_env/bin/activate
  ```

3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ``` 
   
4. Register the environment as a Jupyter Kernel:
    ```bash
    python -m ipykernel install --user --name=alpharesearch_env --display-name "Alpharesearch_env"
    ```