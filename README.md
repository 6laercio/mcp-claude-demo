# MCP Demo

Conecte Claude Desktop com servidores MCP usando TypeScript.

## Requisitos

- Claude Desktop (Windows ou macOS)
- Node.js instalado (versão 16 ou superior)
- TypeScript e dependências do projeto instaladas via `npm install`
- Para Windows com WSL: WSL configurado com Ubuntu ou distribuição similar

## Integração com Claude Desktop

### Windows (nativo)

1. **Configure o Claude Desktop**:

   - Edite: `%userprofile%\AppData\Roaming\Claude\claude_desktop_config.json`
   - Adicione:

   ```json
   {
     "mcpServers": {
       "demo-server": {
         "command": "node",
         "args": ["C:\\caminho\\para\\seu\\projeto\\dist\\server.js"]
       }
     }
   }
   ```

   - Substitua o caminho pelo local completo do arquivo server.js no seu sistema

2. **Reinicie o Claude Desktop**

3. **Problemas?** Verifique os logs:
   - Pressione `Win+R`, digite `%APPDATA%\Claude\logs` e procure pelos arquivos que começam com "mcp"

### Windows (com WSL)

1. **Obtenha caminhos necessários**:

   ```bash
   # Caminho do Node.js
   which node

   # Caminho do seu server.js (na pasta do projeto)
   realpath dist/server.js
   ```

2. **Configure o Claude Desktop**:

   - Edite: `%userprofile%\AppData\Roaming\Claude\claude_desktop_config.json`
   - Adicione:

   ```json
   {
     "mcpServers": {
       "demo-server": {
         "command": "wsl.exe",
         "args": ["bash", "-c", "CAMINHO_DO_NODE CAMINHO_DO_SERVER_JS"]
       }
     }
   }
   ```

   - Substitua CAMINHO_DO_NODE e CAMINHO_DO_SERVER_JS pelos valores obtidos

3. **Reinicie o Claude Desktop**

4. **Problemas?** Verifique os logs:
   - Pressione `Win+R`, digite `%APPDATA%\Claude\logs` e procure pelos arquivos que começam com "mcp"

### macOS

1. **Configure o Claude Desktop**:

   - Edite: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Adicione:

   ```json
   {
     "mcpServers": {
       "demo-server": {
         "command": "node",
         "args": ["/caminho/completo/para/seu/projeto/dist/server.js"]
       }
     }
   }
   ```

   - Substitua o caminho pelo local completo do arquivo server.js no seu sistema

2. **Reinicie o Claude Desktop**

3. **Problemas?** Verifique os logs:
   - Abra o Terminal e execute: `tail -n 50 ~/Library/Logs/Claude/mcp*.log`
   - Ou navegue até `~/Library/Logs/Claude/` no Finder

## Testando a Integração

Depois de configurar, teste usando o Claude Desktop:

1. Inicie uma nova conversa
2. Procure o ícone de ferramentas (martelo) na interface
3. Teste usando comandos como:
   - "Por favor, use a ferramenta 'add' para somar 42 e 58"
