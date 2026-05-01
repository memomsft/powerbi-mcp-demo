# Escenario 04 - Crear Medidas DAX

## Valor

El developer describe la lógica de negocio en lenguaje natural → el MCP genera el DAX correcto, lo registra en el modelo y con Sonnet organiza las medidas en Display Folders automáticamente.

## Prompt

```
Create the following DAX measures in the FactSales table:
- Total Sales: sum of TotalAmount
- Total Quantity: sum of Quantity
- Average Discount: average of Discount
- Total Transactions: count of SalesKey
```

## Resultado esperado

4 medidas creadas en FactSales, organizadas en un Display Folder (con Sonnet).

## Tool ejecutada

`measure_operations`

## ⚠️ Nota de modelo

Con **GPT-4.1**: usa `table_operations` → medidas no se crean.  
Con **Haiku y Sonnet**: selecciona `measure_operations` correctamente.  
Con **Sonnet**: además organiza las medidas en Display Folders automáticamente.

## Validación

Fabric → SalesModel → panel de datos → expande `factsales` → verifica las 4 medidas en su carpeta.

---
👉 [Escenario 05 - Best Practices](05_best_practices.md)
