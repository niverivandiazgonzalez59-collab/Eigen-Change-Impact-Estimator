Eigen Change Impact Estimator

Herramienta cuantitativa para estimar el impacto estructural de cambios en el código antes del merge, orientada a procesos de pull request review, control de riesgo arquitectónico y priorización técnica.

El sistema implementa un motor de análisis compacto, verificable por cualquier desarrollador, que proyecta métricas de cambio a un espacio estructural sin exponer el núcleo matemático interno.


---

Objetivo

Proveer una estimación objetiva, reproducible y rápida del impacto de un cambio de código, antes de su integración, respondiendo a preguntas clave como:

¿Qué tan riesgoso es este cambio?

¿El impacto es local o sistémico?

¿Dónde conviene enfocar la revisión?

¿Qué tan confiable es la estimación?



---

Inputs

El estimador opera sobre parámetros simples, fácilmente obtenibles en cualquier PR:

Parámetro	Descripción

files	Cantidad de archivos modificados
depth	Profundidad estructural del cambio
frequency	Frecuencia reciente de cambios
changeType	Tipo de cambio: local, feature, core



---

Output

El motor devuelve un objeto estructurado:

{
  "metrics": {
    "impact": 0-100,
    "volatility": 0-100,
    "stability": 0-100,
    "instability": 0-100,
    "composite": 0-100
  },
  "risk": "Low | Medium | High | Critical",
  "confidence": 0-100,
  "diagnostics": [
    "Mensajes priorizados sobre el cambio"
  ]
}

Descripción de métricas

Impact: Magnitud estructural del cambio.

Volatility: Inestabilidad temporal inducida.

Stability: Coherencia estructural preservada.

Instability: Riesgo de propagación o ruptura.

Composite: Score global ponderado.

Risk: Clasificación final del riesgo.

Confidence: Nivel de confiabilidad de la estimación.

Diagnostics: Recomendaciones priorizadas para revisión.



---

Diseño

Núcleo matemático abstraído y protegido

Sin dependencias externas

Sin heurísticas arbitrarias

Basado en proyecciones geométricas y métricas normalizadas

Totalmente determinista y auditable
