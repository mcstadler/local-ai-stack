# Setup folder content
Download the required model using ollama

## First powershell
```powershell
docker run -it -rm --gpus all -v .\ollama-data:/root/.ollama ollama/ollama:latest
```
## Second powershell
```powershell
docker ps
```

    CONTAINER ID   IMAGE                  COMMAND               CREATED          STATUS         PORTS       NAMES
    2171372148da   ollama/ollama:latest   "/bin/ollama serve"   10 seconds ago   Up 9 seconds   11434/tcp   xenodochial_merkle

```powershell
docker exec -it 2171372148da /bin/sh
```

```bash
ollama pull qwen2.5-coder:7b
```

Make sure to set the 'GOOSE_MODEL' environment variable in 'docker-compose.yml' accordingly.
