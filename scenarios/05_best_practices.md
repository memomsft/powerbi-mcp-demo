# Escenario 05 - Best Practices Analyzer

## Valor

Revisión manual de best practices toma horas.  
Con MCP + Sonnet: análisis completo + fixes automáticos en un solo prompt.

## Prompt

```
Analyze my semantic model and evaluate it against Power BI 
modeling best practices. List what needs to be improved 
and apply the fixes automatically.
```

## Resultado esperado con Sonnet

| Fix | Detalle |
|-----|---------|
| Ocultar keys técnicas | SalesKey, DateKey, ProductKey, CustomerKey → hidden |
| Corregir summarización | Year/Month/IsWeekend → None; campos de precio → Average |
| Formato de moneda | UnitPrice, Discount, TotalAmount, medidas → $#,0.00 |
| Marcar tabla de fechas | DimDate marcada para habilitar time intelligence (YTD, MTD) |
| Sort de MonthName | Ordenado por Month number |
| Categorías geográficas | Country y City categorizados para mapas |

## ⚠️ Nota de modelo

Con **modelos ligeros**: aplica fixes a nivel de tabla pero falla en columnas individuales.  
Con **Sonnet**: aplica todos los fixes correctamente incluyendo column-level.

## Validación

Fabric → SalesModel → verifica columnas con ícono de ojo tachado y DimDate marcada como Date Table.

---
👉 [Escenario 06 - Documentación](06_documentation.md)
