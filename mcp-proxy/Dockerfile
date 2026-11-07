FROM ghcr.io/tbxark/mcp-proxy:latest

USER root

# Node + npm installieren (abhängig vom Base Image)
#RUN apk add --no-cache nodejs npm

# MCP Server installieren
RUN npm install -g @modelcontextprotocol/server-filesystem

#COPY config.json /config.json

#CMD ["-config", "/config.json"]
