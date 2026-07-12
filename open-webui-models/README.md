# Setup folder content
OpenWeb UI uses a model internally which has to be provided when running in offline mode.

Follow this guide to set up this folder correctly:

https://docs.openwebui.com/tutorials/maintenance/offline-mode/

Run the python commands inside a python container and install  'huggingface_hub':

```powershell
docker run -it -v .\open-webui-models\:/models python:3.11 bash
```

```bash
pip install huggingface_hub
```

```python
from huggingface_hub import snapshot_download

snapshot_download(repo_id="sentence-transformers/all-MiniLM-L6-v2", cache_dir="/models")
```
