# Local AI development stack
The goal of this project is to get a local, containerized and open source AI development stack.

## Setup host (Windows)
- Install Docker Desktop
- Install NVIDIA CUDA driver (https://learn.microsoft.com/en-us/windows/ai/directml/gpu-cuda-in-wsl)

## Run local AI development stack
### PowerShell
- Open a powershell console in the repo root directory
- Set 'CODE_DIR' environment variable:
  ```powershell
  $env:CODE_DIR = 'C:\Users\<user>\source\repos\'
  ```
- Run docker compose
  ```powershell
  docker compose up --force-recreate
  ```
