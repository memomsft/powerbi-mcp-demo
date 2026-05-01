# Setup 02 - Claude Code (Recomendado)

## ¿Por qué Claude Code?

| | GitHub Copilot | Claude Code |
|--|---------------|-------------|
| Modelo | GPT-4.1 (Free) / Sonnet (Pro+) | Sonnet incluido |
| Guardar archivos en disco | ❌ Manual | ✅ Automático |
| Descripciones de columnas | ⚠️ Requiere modelo premium | ✅ |
| Best practices completo | ⚠️ Requiere modelo premium | ✅ |
| Configuración MCP | Automática (extensión) | Manual (una sola vez) |

---

## Requisitos

- [VS Code](https://code.visualstudio.com/download) instalado
- [Node.js LTS](https://nodejs.org) instalado, verifica con `node -v`
- Cuenta de [Claude](https://claude.ai) (cualquier plan)
- Extensión **Power BI Modeling MCP** instalada en VS Code (ver paso 1)

---

## Paso 1 - Instalar la extensión de VS Code

Esta extensión instala el ejecutable del MCP localmente en tu máquina.

1. Abre VS Code
2. Ve a Extensions (`Ctrl+Shift+X`)
3. Busca: `Power BI Modeling MCP`
4. Publisher: **analysis-services** (oficial de Microsoft)
5. Clic en **Install**

---

## Paso 2 - Instalar Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Verifica:

```bash
claude --version
```

---

## Paso 3 - Localizar el ejecutable del MCP

La extensión de VS Code instala el ejecutable localmente. Encuéntralo con:

```powershell
Get-ChildItem "$env:USERPROFILE\.vscode\extensions" | Where-Object {$_.Name -like "analysis-services*"}
```

Verás algo como:
```
analysis-services.powerbi-modeling-mcp-0.4.0-win32-x64
```

El ejecutable está en:
```
C:\Users\<YOUR_USERNAME>\.vscode\extensions\analysis-services.powerbi-modeling-mcp-<VERSION>-win32-x64\server\powerbi-modeling-mcp.exe
```

---

## Paso 4 - Configurar el MCP en Claude Code

El archivo de configuración de Claude Code es `~/.claude.json`. Ábrelo:

```powershell
code "$env:USERPROFILE\.claude.json"
```

Dentro del archivo, busca la sección `"projects"` y agrega `"mcpServers"` al proyecto donde trabajarás. Por ejemplo si trabajas desde `C:/Users/<YOUR_USERNAME>`:

```json
"projects": {
  "C:/Users/<YOUR_USERNAME>": {
    "mcpServers": {
      "powerbi-modeling-mcp": {
        "type": "stdio",
        "command": "C:\\Users\\<YOUR_USERNAME>\\.vscode\\extensions\\analysis-services.powerbi-modeling-mcp-<VERSION>-win32-x64\\server\\powerbi-modeling-mcp.exe",
        "args": ["--start"],
        "env": {}
      },
      "powerbi-remote": {
        "type": "http",
        "url": "https://api.fabric.microsoft.com/v1/mcp/powerbi"
      }
    }
  }
}
```

> ⚠️ Reemplaza `<YOUR_USERNAME>` y `<VERSION>` con tus valores reales.
> ⚠️ Usa doble backslash `\\` en los paths de Windows dentro de JSON.
> ⚠️ Si editaste `~/.claude.json` usando PowerShell `ConvertTo-Json`, 
> el archivo puede quedar con `\\\\` en lugar de `\\` en los paths. 
> Ambos funcionan correctamente — no es necesario corregirlo.
> Si editas el archivo manualmente en VS Code, usa `\\` simple.

---

## Paso 5 - Habilitar el Remote MCP en Fabric (admin)

El Remote MCP requiere habilitación por un admin del tenant:

1. Ve a [Fabric Admin Portal](https://admin.fabric.microsoft.com)
2. **Tenant settings** → busca: *"Users can use the Power BI Model Context Protocol server endpoint (preview)"*
3. Habilítalo → **Apply**

> ⏱️ Los cambios de tenant settings pueden tardar hasta 15 minutos en aplicar.

---

## Paso 6 - Verificar la conexión

1. Abre una terminal en VS Code (`Ctrl+` ` `)
2. Navega a tu carpeta de trabajo:
```bash
cd C:\Users\<YOUR_USERNAME>
```
3. Inicia Claude Code:
```bash
claude
```
4. Dentro de la sesión, escribe:
```
/mcp
```
5. Verifica que aparezcan bajo **Local MCPs**:
   - `powerbi-modeling-mcp · ✔ connected`
   - `powerbi-remote · ✔ connected`

---

## Siguiente paso

👉 [Escenario 01 — Conectar al modelo](../scenarios/01_connect.md)
