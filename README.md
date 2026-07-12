# Run local AI stack
## PowerShell
- Open a powershell console
- Set 'CODE_DIR' environment varialbe
  ```powershell
  $env:CODE_DIR = 'C:\Users\<user>\source\repos\'
  ```
- Run docker compose
  ```powershell
  docker compose up --force-recreate
  ```