# Escenario 06 - Documentar el Modelo

## Valor

Documentación del modelo generada automáticamente, siempre sincronizada con el estado real.

## Prompt

```
Generate a Markdown document that provides complete, professional 
documentation for this Power BI Semantic Model. Include:
- Model overview
- All tables and their purpose
- All columns with descriptions
- All measures with DAX code and business explanation
- Table relationships
- A Mermaid diagram showing the relationships
Save the document as SalesModel-documentation.md
```

## ⚠️ Diferencia por cliente

| | Claude Code | GitHub Copilot |
|--|:-----------:|:--------------:|
| Guarda el archivo | ✅ Automático | ❌ Manual |

Con GitHub Copilot: copia el contenido del chat y guarda como `SalesModel-documentation.md`.

## Visualización

- **VS Code**: extensión `Markdown Preview Enhanced` → `Ctrl+Shift+V`
- **GitHub**: el `.md` se renderiza automáticamente incluyendo el diagrama Mermaid

---
👉 [Escenario 07 - DAX Query Remote MCP](07_remote_dax_query.md)
