# Eigen Change Impact Estimator

Herramienta cuantitativa para estimar el impacto estructural de cambios en el código **antes del merge**, orientada a revisiones técnicas y control de riesgo arquitectónico.

El motor interno está deliberadamente abstraído; la herramienta expone únicamente un **contrato verificable de entrada y salida**.

---

## ¿Qué hace?

A partir de parámetros simples del cambio, calcula:

- métricas normalizadas de impacto y estabilidad
- un score compuesto de riesgo
- una clasificación clara (Low / Medium / High)
- diagnósticos priorizados que indican **dónde es más probable que esté el problema**

No reemplaza una code review, la **enfoca**.

---

## Inputs

| Campo | Descripción |
|------|-------------|
| `files` | Cantidad de archivos modificados |
| `depth` | Profundidad estructural del cambio |
| `frequency` | Frecuencia reciente de cambios |
| `changeType` | `local` · `feature` · `core` |

---

## Output

```json
{
  "metrics": {
    "impact": 0-100,
    "volatility": 0-100,
    "stability": 0-100,
    "instability": 0-100,
    "composite": 0-100
  },
  "risk": "Low | Medium | High",
  "confidence": 0-100,
  "diagnostics": [
    "mensajes priorizados sobre la localización probable del error"
  ]
}