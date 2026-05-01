# Power BI Modeling MCP - Demo Exploratorio

Repositorio de exploración de las capacidades del [Power BI Modeling MCP Server](https://github.com/microsoft/powerbi-modeling-mcp) de Microsoft, conectado a un Semantic Model en Microsoft Fabric usando lenguaje natural desde VS Code.

> ⚠️ **Public Preview** : Este MCP está en Public Preview. Las capacidades pueden cambiar antes del GA.

---

## ¿Qué es el Power BI Modeling MCP?

El Power BI Modeling MCP Server implementa el [Model Context Protocol](https://modelcontextprotocol.io) para crear una conexión entre agentes de AI y semantic models de Power BI. Permite a desarrolladores interactuar con modelos en lenguaje natural, desde crear relaciones y medidas DAX hasta configurar RLS y generar documentación completa del modelo.

> 💡 Este ejercicio usa **Microsoft Fabric** (cloud), pero el MCP también soporta **Power BI Desktop** y archivos **PBIP** locales.

---

## Arquitectura

```mermaid
flowchart LR
    A[👨‍💻 Developer\nLenguaje natural] --> B[AI Client\nVS Code]
    B --> C[Power BI Modeling MCP\nLocal · stdio]
    B -.->|Remote MCP| D[Power BI Remote MCP\nCloud · HTTP]
    C --> E[📊 Semantic Model\nFabric / Desktop / PBIP]
    D --> E

    style C fill:#0078D4,color:#fff
    style D fill:#0078D4,color:#fff
    style E fill:#F2C811,color:#000
```

### Dos MCP servers distintos

| | Modeling MCP | Remote MCP |
|--|-------------|------------|
| **Propósito** | Construir y modificar el modelo | Consultar datos en lenguaje natural |
| **Tipo** | Local (stdio) | Cloud (HTTP) |
| **Requiere admin** | No | Sí (Fabric tenant setting) |
| **Trabaja con** | Metadata del modelo | Datos reales |

---

## Herramientas requeridas

```mermaid
flowchart TD
    A[VS Code] --> B[Extensión\nPower BI Modeling MCP]
    A --> C[AI Client]
    C --> D[GitHub Copilot\nRecomendado: Sonnet 4.5+]
    C --> E[Claude Code\nSonnet incluido]
    B --> F[Modeling MCP Server\nLocal]
    D & E --> F
    D & E -.-> G[Remote MCP Server\nCloud]

    style F fill:#0078D4,color:#fff
    style G fill:#0078D4,color:#fff
```

---

## Flujo del demo

```mermaid
flowchart TD
    A[📄 4 CSVs sintéticos\nFactSales · DimProduct\nDimCustomer · DimDate] --> B[🏠 SalesLakehouse\nFabric Lakehouse]
    B --> C[📊 SalesModel\n4 tablas sin relaciones ni medidas]
    C --> D[MCP Modeling Server]
    D --> E1[01 · Conectar]
    E1 --> E2[02 · Crear relaciones]
    E2 --> E3[03 · Descripciones]
    E3 --> E4[04 · Medidas DAX]
    E4 --> E5[05 · Best practices]
    E5 --> E6[06 · Documentación .md]
    E6 --> F[MCP Remote Server]
    F --> E7[07 · DAX en lenguaje natural]
    E2 --> E8[08 · RLS + recomendaciones]

    style D fill:#0078D4,color:#fff
    style F fill:#0078D4,color:#fff
    style C fill:#F2C811,color:#000
```

---

## Estructura del repositorio

```
powerbi-mcp-demo/
├── README.md
├── setup/
│   ├── 01_fabric_setup.md        ← Crear Lakehouse y Semantic Model
│   ├── 02_claude_code.md         ← Configuración Claude Code (recomendado)
│   └── 03_github_copilot.md      ← Configuración GitHub Copilot
├── scenarios/
│   ├── 01_connect.md
│   ├── 02_relationships.md
│   ├── 03_descriptions.md
│   ├── 04_dax_measures.md
│   ├── 05_best_practices.md
│   ├── 06_documentation.md
│   ├── 07_remote_dax_query.md
│   └── 08_rls.md
├── prompts/
│   └── prompts.md                ← Todos los prompts validados
└── data/
    ├── FactSales.csv
    ├── DimProduct.csv
    ├── DimCustomer.csv
    └── DimDate.csv
```

---

## Resultados por modelo

| Escenario | GPT-4.1 | Claude Haiku | Claude Sonnet |
|-----------|:-------:|:------------:|:-------------:|
| Conectar al modelo | ✅ | ✅ | ✅ |
| Crear relaciones | ✅ | ✅ | ✅ |
| Descripciones de tablas | ✅ | ✅ | ✅ |
| Descripciones de columnas | ⚠️ | ⚠️ | ✅ |
| Crear medidas DAX | ⚠️ | ✅ | ✅ |
| Medidas en Display Folders | ❌ | ❌ | ✅ |
| Best practices completo | ⚠️ | ⚠️ | ✅ |
| Documentar + guardar .md | ⚠️ | ⚠️ | ✅ |
| RLS + recomendaciones | ❌ | — | ✅ |
| DAX query Remote MCP | ✅ | ✅ | ✅ |

✅ Funciona correctamente · ⚠️ Funciona parcialmente · ❌ No disponible · — No probado

> 💡 **Recomendación:** Usar **Claude Sonnet** o **GPT-5** para mejores resultados. Microsoft lo indica explícitamente en la documentación oficial.

---

## Requisitos generales

- Cuenta de Microsoft Fabric con permisos de admin en el workspace
- [VS Code](https://code.visualstudio.com/download)
- [Node.js](https://nodejs.org) (LTS)
- Extensión [Power BI Modeling MCP](https://aka.ms/powerbi-modeling-mcp-vscode) instalada en VS Code

---

## Comenzar

👉 **Paso 1:** [Setup de Fabric](setup/01_fabric_setup.md)

👉 **Paso 2 - Elige tu cliente:**
- [Claude Code](setup/02_claude_code.md) ← Recomendado
- [GitHub Copilot](setup/03_github_copilot.md)

👉 **Paso 3:** [Ejecuta los escenarios](scenarios/)
