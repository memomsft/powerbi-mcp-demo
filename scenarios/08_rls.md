# Escenario 08 - Row Level Security (RLS)

## Pre-requisito

> ⚠️ Con **GitHub Copilot Free**, `security_role_operations` está deshabilitado.  
> Este escenario requiere **Claude Code** o **Copilot Pro/Business/Enterprise**.

## Valor

Configurar RLS normalmente requiere conocer DAX y la estructura del modelo.  
Con MCP: describes el requisito de seguridad → rol creado con DAX correcto + plan de implementación completo.

## Prompt

```
Create a Row Level Security role called 'RegionFilter' that filters 
the FactSales table so users only see rows where Region matches 
their username.
```

## Resultado esperado

El MCP crea el rol `RegionFilter` con el filtro DAX:
```dax
[Region] = USERPRINCIPALNAME()
```

Y provee un plan de implementación:
1. **Asignar miembros** : en Fabric workspace → semantic model settings → asignar usuarios o grupos al rol
2. **Mapear Region a UPNs** : los valores de Region deben coincidir con los emails de los usuarios, o crear una mapping table
3. **Probar el rol** : usar "View as role" en Fabric para validar antes de asignar a producción

## ⚠️ Consideración de datos

`USERPRINCIPALNAME()` devuelve el email del usuario (ej. `alice@contoso.com`).  
En este demo, Region tiene valores como `Norte`, `Centro`, `Sur` — no coinciden directamente.  
Para producción se requiere una **mapping table** `UserRegion`:

| UserPrincipal | Region |
|---------------|--------|
| alice@empresa.com | Norte |
| bob@empresa.com | Centro |

## Tool ejecutada

`security_role_operations`

---
---

## ✅ Tarea completada

Has ejecutado los 8 escenarios del ejercicio exploratorio. 

**Próximos pasos sugeridos:**
- Revisa la [tabla de resultados por modelo](../README.md#resultados-por-modelo) y compara con tu experiencia
- Explora los [prompts adicionales](../prompts/prompts.md#prompts-adicionales-para-explorar) para seguir experimentando
- ¿Encontraste algo diferente? Abre un [Issue](../../issues) o revisa cómo [contribuir](../CONTRIBUTING.md)
