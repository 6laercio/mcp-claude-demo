# MCP Demo

Conecte Claude Desktop com servidores MCP usando TypeScript e WSL.

## Integração com Claude Desktop

### Passos essenciais

1. **Obtenha caminhos necessários**:

   ```bash
   # Caminho do Node.js
   which node

   # Caminho do seu server.js (na pasta do projeto)
   realpath dist/server.js
   ```

2. **Configure o Claude Desktop (Windows)**:

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

4. **Teste**: Use o ícone de ferramentas e faça requisições como "add 5 8"

5. **Problemas?** Verifique logs: `type "%APPDATA%\Claude\logs\mcp*.log"`
