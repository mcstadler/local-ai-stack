FROM mcr.microsoft.com/dotnet/sdk:10.0

ENV DOTNET_ROOT=/usr/share/dotnet
ENV PATH="${DOTNET_ROOT}:${PATH}"
ENV DOTNET_SKIP_FIRST_TIME_EXPERIENCE=1
ENV DOTNET_NOLOGO=1
ENV DOTNET_CLI_TELEMETRY_OPTOUT=1
ENV DOTNET_CLI_HOME=/tmp/dotnet
ENV NUGET_PACKAGES=/root/.nuget/packages

# System dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    ca-certificates \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

# Node.js 24 (for Supergateway)
RUN curl -fsSL https://deb.nodesource.com/setup_24.x | bash - \
    && apt-get update \
    && apt-get install -y --no-install-recommends nodejs \
    && rm -rf /var/lib/apt/lists/*

# Install additional .NET SDKs side-by-side
RUN curl -fsSL https://dot.net/v1/dotnet-install.sh \
    -o /tmp/dotnet-install.sh \
    && bash /tmp/dotnet-install.sh --channel 8.0 --install-dir /usr/share/dotnet \
    && bash /tmp/dotnet-install.sh --channel 9.0 --install-dir /usr/share/dotnet \
    && rm /tmp/dotnet-install.sh

# Install the prebuilt .NET MCP server.
# Explicit net10.0 ensures the MCP server runs on the stable .NET 10 runtime.
RUN dotnet tool install \
    --tool-path /opt/dotnet-tools \
    --framework net10.0 \
    Community.Mcp.DotNet \
    --version 1.1.2

ENV PATH="/opt/dotnet-tools:${PATH}"

# Install Supergateway
RUN npm install --global supergateway

WORKDIR /workspace

EXPOSE 8000

# Expose the STDIO MCP server through Streamable HTTP
CMD ["supergateway", \
     "--stdio", "/opt/dotnet-tools/dotnet-mcp", \
     "--outputTransport", "streamableHttp", \
     "--port", "8000", \
     "--host", "0.0.0.0", \
     "--streamableHttpPath", "/mcp", \
     "--healthEndpoint", "/healthz", \
     "--healthCheck", "server"]
