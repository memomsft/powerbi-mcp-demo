# Prompts Validados

Referencia rápida de todos los prompts del ejercicio, listos para copiar.

> 💡 Usa inglés — el MCP fue diseñado en inglés y los resultados son más precisos.

---

## 01 · Conectar

```
Connect to semantic model 'SalesModel' in Fabric Workspace 'powerbi-mcp-demo'
```

---

## 02 · Crear relaciones

```
Create the following relationships in the model:
- FactSales[DateKey] → DimDate[DateKey] (Many to One, active)
- FactSales[ProductKey] → DimProduct[ProductKey] (Many to One, active)
- FactSales[CustomerKey] → DimCustomer[CustomerKey] (Many to One, active)
```

---

## 03 · Descripciones de tablas y columnas

```
Add a business-friendly description to every table and every individual 
column in the model. For tables, describe their purpose in the data model. 
For each column, describe what that specific field represents for end users. 
Do not skip any table or column.
```

---

## 04 · Medidas DAX

```
Create the following DAX measures in the FactSales table:
- Total Sales: sum of TotalAmount
- Total Quantity: sum of Quantity
- Average Discount: average of Discount
- Total Transactions: count of SalesKey
```

---

## 05 · Best practices

```
Analyze my semantic model and evaluate it against Power BI 
modeling best practices. List what needs to be improved 
and apply the fixes automatically.
```

---

## 06 · Documentación

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

---

## 07 · DAX query (Remote MCP)

Escribe `/` → selecciona `CreateDAXQuery`, luego:

```
What is the total sales amount and quantity by product category?
```

O directo:

```
Show me total sales and quantity sold by product category for the SalesModel
```

---

## 08 · RLS

```
Create a Row Level Security role called 'RegionFilter' that filters 
the FactSales table so users only see rows where Region matches 
their username.
```

---

## Prompts adicionales para explorar

```
Create a date hierarchy in DimDate with levels: Year > Quarter > Month > Date
```

```
Create a perspective called 'Sales Analysis' that includes only the 
measures and columns relevant for sales reporting
```

```
Analyze the DAX performance of the Total Sales measure and suggest optimizations
```
