# Prompts Validados — Español

Versión en español de todos los prompts del ejercicio, listos para copiar.

> 💡 Validado con **Claude Sonnet**. Los prompts en español funcionan correctamente — mantén los nombres técnicos (tablas, columnas, workspace) tal como están en el modelo.

---

## 01 · Conectar

```
Conéctate al modelo semántico 'SalesModel' en el workspace de Fabric 'powerbi-mcp-demo'
```

---

## 02 · Crear relaciones

```
Crea las siguientes relaciones en el modelo:
- FactSales[DateKey] → DimDate[DateKey] (Muchos a Uno, activa)
- FactSales[ProductKey] → DimProduct[ProductKey] (Muchos a Uno, activa)
- FactSales[CustomerKey] → DimCustomer[CustomerKey] (Muchos a Uno, activa)
```

---

## 03 · Descripciones de tablas y columnas

```
Agrega una descripción clara y orientada al negocio a cada tabla y cada 
columna del modelo. Para las tablas, describe su propósito en el modelo 
de datos. Para cada columna, describe qué representa ese campo para los 
usuarios finales. No omitas ninguna tabla ni columna.
```

---

## 04 · Medidas DAX

```
Crea las siguientes medidas DAX en la tabla FactSales:
- Total Ventas: suma de TotalAmount
- Total Cantidad: suma de Quantity
- Descuento Promedio: promedio de Discount
- Total Transacciones: conteo de SalesKey
```

---

## 05 · Best practices

```
Analiza mi modelo semántico y evalúalo contra las mejores prácticas 
de modelado de Power BI. Lista los puntos a mejorar y aplica 
las correcciones automáticamente.
```

---

## 06 · Documentación

```
Genera un documento Markdown con documentación completa y profesional 
de este modelo semántico de Power BI. Incluye:
- Descripción general del modelo
- Todas las tablas y su propósito
- Todas las columnas con sus descripciones
- Todas las medidas con el código DAX y su explicación de negocio
- Las relaciones entre tablas
- Un diagrama Mermaid que muestre las relaciones
Guarda el documento como SalesModel-documentacion.md
```

---

## 07 · DAX query (Remote MCP)

Escribe `/` → selecciona `CreateDAXQuery`, luego:

```
¿Cuál es el total de ventas y cantidad vendida por categoría de producto?
```

O directo:

```
Muéstrame el total de ventas y cantidad vendida por categoría de producto del SalesModel
```

---

## 08 · RLS

```
Crea un rol de Seguridad a Nivel de Fila llamado 'FiltroRegion' que filtre 
la tabla FactSales para que cada usuario solo vea las filas donde la 
columna Region coincida con su nombre de usuario.
```

---

## Prompts adicionales para explorar

```
Crea una jerarquía de fechas en DimDate con los niveles: Año > Trimestre > Mes > Fecha
```

```
Crea una perspectiva llamada 'Análisis de Ventas' que incluya solo las 
medidas y columnas relevantes para reportes de ventas
```

```
Analiza el rendimiento de la medida Total Ventas y sugiere optimizaciones DAX
```
