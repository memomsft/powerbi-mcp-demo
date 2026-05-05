# Setup 03 - GitHub Copilot

## Requisitos

- [VS Code](https://code.visualstudio.com/download) instalado
- [Node.js LTS](https://nodejs.org) instalado
- Cuenta de GitHub con Copilot activo
- Plan recomendado: **Pro, Business o Enterprise** para acceso a Sonnet 4.5+

> 💡 Copilot Free funciona pero limita los modelos disponibles a GPT-4.1 y GPT-4o mini. Ver [tabla de resultados](../README.md#resultados-por-modelo) para entender el impacto.

---

## Paso 1 - Instalar extensiones en VS Code

1. Abre VS Code → Extensions (`Ctrl+Shift+X`)
2. Instala:
   - **GitHub Copilot** (publisher: GitHub)
   - **GitHub Copilot Chat** (publisher: GitHub)
3. Instala el MCP:
   - Busca: `Power BI Modeling MCP`
   - Publisher: **analysis-services** (oficial de Microsoft)
   - Clic en **Install**

---

## Paso 2 - Verificar el MCP en Copilot

1. Abre Copilot Chat (`Ctrl+Shift+I`)
2. Cambia a modo **Agent** (dropdown en el input)
3. Clic en el ícono de herramientas 🔧
4. Confirma que `powerbi-modeling-mcp` aparece en la lista

> ⚠️ Si no aparece: en GitHub.com → Settings → Copilot → verifica que **"MCP servers in Copilot"** esté habilitado. En cuentas Enterprise, un admin debe habilitarlo.

---

## Paso 3 - Seleccionar el modelo correcto

Para mejores resultados selecciona **Claude Sonnet 4.5** o superior:

1. En Copilot Chat → modo **Agent**
2. Clic en el selector de modelo (junto al input)
3. Selecciona: `claude-sonnet-4-5` o `GPT-5`

> ⚠️ Con GPT-4.1 o modelos ligeros, operaciones a nivel de columna (descripciones, hide, format) fallan. Ver [tabla de resultados](../README.md#resultados-por-modelo).

---

## Paso 4 - Configurar el Remote MCP

1. Abre la paleta de comandos (`Ctrl+Shift+P`)
2. Busca: `MCP: Open User Configuration`
3. Agrega:

```json
{
  "servers": {
    "powerbi-remote": {
      "type": "http",
      "url": "https://api.fabric.microsoft.com/v1/mcp/powerbi"
    }
  }
}
```

4. Guarda (`Ctrl+S`)

> ⚠️ Requiere que un admin del tenant habilite: **"Users can use the Power BI Model Context Protocol server endpoint (preview)"** en Fabric Admin Portal → Tenant settings.

---

## Diferencias vs Claude Code

| Característica | GitHub Copilot | Claude Code |
|----------------|:--------------:|:-----------:|
| Guardar .md en disco | ❌ Manual | ✅ Automático |
| Configuración MCP | ✅ Automática | Manual (una vez) |
| Modelo Sonnet incluido | ⚠️ Plan Pro+ | ✅ Siempre |
| RLS operations | ⚠️ Deshabilitado Free | ✅ |

---

## Siguiente paso

👉 [Escenario 01 - Conectar al modelo](../scenarios/01_connect.md)
