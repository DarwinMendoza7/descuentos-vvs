# Análisis de requisitos - Módulo de descuentos

## 1. Matriz de revisión de requisitos

| ID | Requisito original | Problema | Impacto | Propuesta | Artefacto | Estado |
|----|--------------------|----------|---------|-----------|-----------|--------|
| R-01 | El descuento debe calcularse rápidamente | "Rápidamente" es subjetivo, no hay umbral medible  | No se puede verificar; discusiones entre equipo y cliente | RF-01: responder en menos de 50 ms para 1000 invocaciones (umbral por confirmar) | docs/requisitos.md (sección 2)| Pendiente de confirmar |
| R-02 | Los clientes importantes obtendrán un descuento especial | "Importantes" y "especial" no están definidos | Se implementa un criterio equivocado (en el código se sumó un 10 arbitrario) | RF-02: Si esVip es true, se aplica un descuento adicional de X puntos porcentuales | docs/requisitos.md (sección 2) | Pendiente de confirmar |
| R-03 | El descuento no puede superar el precio, excepto en promociones | No se define "promoción" ni cómo se identifica | Totales negativos o bloqueo de promociones legítimas | RF-03: el descuento no supera el precio salvo que esPromocion sea true | docs/requisitos.md (sección 2) | Propuesto |
| R-04 | Se debe mostrar el resultado correcto | "Correcto" no tiene criterio de aceptación | No se puede diseñar pruebas | RF-04: total con 2 decimales y nunca negativo fuera de promoción | docs/requisitos.md (sección 2) | Propuesto |

## 2. Requisitos funcionales verificables

- **RF-01:** La función "calcularDescuento" debe responder en menos de 50 ms para 1000 invocaciones consecutivas. *(umbral por confirmar)*  
- **RF-02:** Si "esVip" es "true", se aplica  un descuento adicional de x puntos porcentuales. *(X por confirmar)*  
- **RF-03:** El descuento aplicado no puede ser mayor que el precio, salvo que "esPromocion" sea "true".  
- **RF-04:** El total se devuelve con 2 decimales y, fuera de promoción, nunca es negativo.  

## 3. Supuestos de negocio pendientes de confirmación  

1. ¿El beneficio VIP son 10 unidades monetarias o 10 puntos porcentuales?  
2. ¿Quién es "cliente importante"? ¿Solo VIP o  hay otros niveles?  
3. ¿Cómo se identifica una promoción (parámetro, código, fecha)?  
4. ¿Qué debe pasar si el porcentaje es mayor que 100 o negativo?  
5. ¿Cuál es el tiempo máximo aceptable y en que entorno se mide?  

## 4. Trazabilidad  

|Requisito original | Requisito refinado | Estado |  
|-------------------|--------------------|--------|  
| R-01 | RF-01 | Pendiente de confirmar umbral |  
| R-02 | RF-02 | Pendiente de confirmar valor |  
| R-03 | RF-03 | Pendiente de confirmar criterio de promoción |  
| R-04 | RF-04 | Propuesto |