# Escenario 03 - Agregar Descripciones

## Valor

Con un modelo de 50+ columnas, documentar manualmente toma horas.  
Con MCP + Sonnet: tablas y columnas documentadas en un solo prompt.

## Prompt

```
Add a business-friendly description to every table and every individual 
column in the model. For tables, describe their purpose in the data model. 
For each column, describe what that specific field represents for end users. 
Do not skip any table or column.
```

## Resultado esperado

Todas las tablas y columnas con descripciones visibles en Fabric.

## Tools ejecutadas

`table_operations` + `column_operations`

## ⚠️ Nota de modelo

Con **GPT-4.1 y Haiku**: solo aplica descripciones de tablas. Las columnas quedan sin descripción.  
Con **Sonnet**: aplica ambas correctamente. Tarda más pero cubre todo.

## Validación

Fabric → SalesModel → selecciona una columna → verifica campo **Description** en propiedades.

---
👉 [Escenario 04 - Medidas DAX](04_dax_measures.md)
