FROM node:22-bookworm-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    python3 \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

# Python virtual environment
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:${PATH}"

# Official Git MCP server
RUN pip install --no-cache-dir mcp-server-git

# HTTP transport adapter
RUN npm install --global supergateway

WORKDIR /workspace

EXPOSE 8000

CMD ["supergateway", \
     "--stdio", "python -m mcp_server_git", \
     "--outputTransport", "streamableHttp", \
     "--port", "8000", \
     "--host", "0.0.0.0"]
