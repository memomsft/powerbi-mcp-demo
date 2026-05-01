# Escenario 02 - Crear Relaciones

## Valor

Normalmente: drag & drop en el editor de relaciones, tabla por tabla.  
Con MCP: descripción en lenguaje natural → relaciones creadas en segundos.

## Prompt

```
Create the following relationships in the model:
- FactSales[DateKey] → DimDate[DateKey] (Many to One, active)
- FactSales[ProductKey] → DimProduct[ProductKey] (Many to One, active)
- FactSales[CustomerKey] → DimCustomer[CustomerKey] (Many to One, active)
```

## Resultado esperado

3 relaciones visibles en el Model View de Fabric con cardinalidad Many-to-One.

## Tool ejecutada

`relationship_operations`

## Validación

Fabric → SalesModel → **Model view** → confirma las 3 relaciones.

---
👉 [Escenario 03 - Descripciones](03_descriptions.md)
