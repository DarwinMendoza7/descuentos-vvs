# Acta de inspección por pares: src/descuentos.js

## 1. Datos de la inspección

- **Artefacto inspeccionado:** src/descuentos.js (versión inicial)  
- **Fecha:** 11/11/2026  
- **Modalidad:** Inspección individual
- **Origen del código:** código base entregado en el enunciado de la actividad (Unidad 1).

| Rol | Responsabilidad |  Quién |
|-----|-----------------|--------|
| Autor | Presenta el código base proporcionado por la actividad y explica su intención | Darwin Mendoza |
| Revisor | Lee el código buscando defectos sin ejecutarlo | Darwin Mendoza |
| Registrador | Anota cada hallazgo con severidad y evidencia | Darwin Mendoza |

## 2. Hallazgos 

| ID | Origen | Hallazgo | Severidad | Evidencia | Acción | Estado |
|----|--------|----------|-----------|-----------|--------|--------|
| H-01 | ESLint | Uso de "var" en lugar de "let"/"const" | Media | lint-inicial.txt, líneas 2:5 y 5:5 ("no-var") | Reemplazar por "let" y "const" | Corregido |
| H-02 | ESLint | Comparación con "==" en lugar de "===" | Media | lint.inicial.txt, línea 3:15 ("eqeqeq") | Usar "===" | Corregido |
| H-03 | ESLint | "if" sin llaves | Media | lint.inicial.txt, líneas 3:24 y 4:27 ("curly") | Añadir llaves | Corregido |
| H-04 | ESLint | "console.log" en lógica de negocio | Baja | lint.inicial.txt, línea 4:27 ("no-console")  | Mantener hasta definir el manejo de porcentaje inválido | Pendiente de confirmar |
| H-05 | Revisión humana | El valor de "10" es un número mágico y ambiguo (¿unidades o puntos porcentuales?) | Alta | Línea 3: "descuento + 10"; supuesto 1 de requisitos.md | Confirmar con negocio y usar una constante con nombre | Pendiente de confirmar |
| H-06 | Revisión humana | Con "porcentaje > 100" solo se escribe un mensaje y el cálculo continúa, por lo que el total puede ser negativo | Alta | Línea 4 y Línea 5; contradice RF-03 y RF-04 | Definir el comportamiento (error o tope) | Pendiente de confirmar |
| H-07 | Revisión humana | No existe el caso de promoción del R-03 (falta el parámetro "esPromocion") | Alta | La firma solo recibe 3 parámetros; supuesto 3 | Implementar RF-03 cuando se confirme el criterio | Pendiente de confirmar |
| H-08 | Revisión humana | No se valida "precio" negativo, "NaN" ni tipos incorrectos | Media | Ninguna validación en el código | Añadir validación de entradas | Abierto |
| H-09 | Revisión humana | El resultado no se redondea a 2 decimales (RF-04) | Media | Línea 5: "precio - descuento " | Redondear el total | Abierto |
| H-10 | Revisión humana | Falta documentación de la función (parámetros y retorno) | Baja | Sin comentarios ni JSDoc | Añadir JSDoc | Abierto |

## 3. Criterio de corrección 

Solo se corrigieron los hallazgos confirmados por una regla de ESLint y que no dependen de decisiones de negocio (H-01, H-02, H-03). Los demás quedan registrados porque requieren confirmación o un cambio de comportamiento. 

## 4. Conclusión  

Se registraron 10 hallazgos: 4 detectados por ESLint y 6 solo por revisión humana. El análisis automático no detectó los defectos de mayor severidad (H-05 a H-07), que son de lógica y de requisitos.