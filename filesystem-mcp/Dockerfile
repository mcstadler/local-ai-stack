FROM node:24-alpine

RUN npm install -g \
    @modelcontextprotocol/server-filesystem \
    supergateway

WORKDIR /app

EXPOSE 8000

CMD ["supergateway", \
     "--stdio", "mcp-server-filesystem /workspace", \
     "--outputTransport", "streamableHttp", \
     "--port", "8000"]
