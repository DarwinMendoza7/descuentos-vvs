# Auditoría estática del módulo de descuentos  

Acitvidad de la Unidad 1 de la materia Verificación y Validación de Software: evaluación estática de un módulo de JavaScript mediante revisión de requisitos, inspección por pares y análisis con ESLint  
**Autor:** Darwin Mendoza

## Estructura del repositorio  

|Ruta| Contenido |
|----|-----------|
| `src/descuentos.js` | Módulo "calcularDescuento (corregido tras la inspección)"|
| `docs/requisitos.md` | Matriz de revisión de requisitos, RF-01 a RF-04, supuestos y trazabilidad |
| `docs/checklist.md` | Checklist de revisión de requisitos |
| `docs/inspeccion.md` | Acta de inspección por pares con 10 hallazgos | 
| `evidencias/lint-inicial.txt` | Resultado de ESLint sobre el código original |
| `evidencias/lint-final.txt` | Resultado de ESLint tras las correcciones | 
| `eslint.config.mjs` | Configuración de ESLint |

## Cómo reproducir el análisis  

Requiere Node.js instalado.

    npm install
    npm run lint


## Reglas de ESLint utilizadas

- `no-var`: evita el alcance de función y las redeclaraciones de `var`.
- `eqeqeq`: evita conversiones de tipo implícitas con `==`.
- `no-unused-vars`: detecta código muerto o errores de nombre.
- `curly`: evita errores por `if` sin llaves.
- `no-console`: advierte sobre salidas por consola en lógica de negocio.

## Resultados

| Momento | Errores | Advertencias | 
|---------|---------|--------------|
| Lint inicial | 5 | 1 | 
| Lint final | 0 | 1 |

La advertencia restante (`no-console`) es intencional: depende de un supuesto de negocio pendiente de confirmar (comportamiento cuando el porcentaje es mayor que 100).

## Hallazgos pendientes 

Quedan hallazgos registrados en `docs/inspeccion.md` que requieren confirmación de negocio antes de corregirse, como el valor del beneficio VIP, el criterio de promoción y el manejo de porcentajes inválidos.