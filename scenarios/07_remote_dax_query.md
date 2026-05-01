# Escenario 07 - DAX Query en Lenguaje Natural (Remote MCP)

## Pre-requisito

Remote MCP conectado y tenant setting habilitado : ver [Setup 02](../setup/02_claude_code.md) o [Setup 03](../setup/03_github_copilot.md).

## Valor

Consultar datos del modelo sin escribir DAX, el Remote MCP genera y ejecuta la query automáticamente y explica los resultados.

## Opción A — Prompt built-in (recomendado)

Escribe `/` en el chat → selecciona **CreateDAXQuery**, luego:

```
What is the total sales amount and quantity by product category?
```

## Opción B — Prompt directo

```
Show me total sales and quantity sold by product category for the SalesModel
```

## Resultado esperado

Tabla con datos reales + análisis explicativo del agente.

## Tools ejecutadas

`GetSemanticModelSchema` → `GenerateDAXQuery` → `ExecuteDAXQuery`

---
👉 [Escenario 08 - RLS](08_rls.md)
