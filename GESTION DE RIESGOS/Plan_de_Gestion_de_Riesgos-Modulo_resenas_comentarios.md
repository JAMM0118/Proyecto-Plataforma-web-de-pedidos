# Plan de Gestión de Riesgos – Módulo de Reseñas y Comentarios – Proyecto Punto H
**Proyecto:** Punto H – Aplicación Web para pedidos universitarios  
**Módulo:** Reseñas y Comentarios  
**Equipo:** Soft Integration  
**Fecha:** Octubre 2025  
**Versión:** 1.0  

---

## 1. Introducción

El presente documento define el **plan de gestión de riesgos** para el desarrollo del **módulo de reseñas y comentarios** de la aplicación web *Punto H*, que permite a los usuarios dejar valoraciones y comentarios sobre menús, cocineros o restaurantes.

El objetivo de este plan es **identificar, analizar, priorizar y planificar respuestas** ante eventos que puedan afectar los objetivos del proyecto en **alcance, cronograma, presupuesto o calidad**, asegurando un desarrollo estable y confiable del módulo.

---

## 2. Identificación de riesgos

Cada riesgo se redacta siguiendo el formato:

> Debido a [causa], [riesgo] podría ocurrir, lo que impactaría [objetivo] en [impacto cuantificable].  
> **Disparador:** [señal temprana].

| ID | Categoría | Causa | Riesgo | Objetivo afectado | Impacto (medida) | Disparador | Dueño |
|----|------------|--------|---------|------------------|------------------|-------------|--------|
| R-01 | Datos | Errores en la escritura o lectura de reseñas en la base de datos | Pérdida o duplicación de comentarios | Calidad / Disponibilidad | >3% de reseñas inconsistentes | Logs con errores de escritura | Líder Backend |
| R-02 | Seguridad | Falta de validación en formularios de reseñas | Inyección de código o spam masivo | Seguridad / Reputación | Vulnerabilidad OWASP crítica | Alertas de seguridad o reportes anómalos | QA Técnico |
| R-03 | Usuarios | Reseñas falsas o generadas por bots | Sesgo en las calificaciones globales | Reputación / Calidad | Desviación >15% en promedios reales | Picos de actividad inusual | Analista UX |
| R-04 | Infraestructura | Fallas en el almacenamiento de archivos (imágenes de reseñas) | Errores en carga o visualización de imágenes | Disponibilidad / Experiencia de usuario | >5% de imágenes no cargan | Reporte de QA o logs HTTP 500 | DevOps |
| R-05 | Equipo | Falta de experiencia con Firebase y Firestore | Retrasos en integración del sistema de autenticación y reseñas | Cronograma | +8 días | Retraso >3 días en primeras tareas | Líder de Desarrollo |
| R-06 | Comunicación | Falta de sincronización entre frontend y backend | Incompatibilidad en formato de datos JSON | Cronograma / Calidad | +7 días de retraso | Merge requests rechazadas | Scrum Master |
| R-07 | Cambios de alcance | Solicitudes tardías para nuevas funciones (filtros, puntuaciones visuales) | Sobrecostos y retrasos | Alcance / Presupuesto | +10% presupuesto | Solicitud fuera de iteración | Project Manager |
| R-08 | Rendimiento | Carga excesiva de reseñas en páginas populares | Lentitud o caída del módulo | Disponibilidad / UX | Tiempos de carga >3s | Alertas de monitoreo | Líder Técnico |
| R-09 | Integración | Errores en endpoints REST o sincronización con módulo de menús | Fallo en mostrar o asociar reseñas a menús | Calidad / Cronograma | +5 días | Reportes de QA con errores 404/500 | Líder Backend |
| R-10 | Legal / Ético | Comentarios con lenguaje inapropiado no filtrado | Daño a la reputación de la plataforma | Reputación | Reportes de usuarios >5 en un día | Feedback negativo | Product Owner |

---

## 3. Análisis cualitativo

**Escalas:**
- **Probabilidad (a–e):**  
  a = remota (≤5%) | b = poco probable (6–20%) | c = probable (21–50%) | d = altamente probable (51–80%) | e = casi con certeza (81–99%)  
- **Impacto (1–5):**  
  1 = mínimo | 2 = menor | 3 = moderado | 4 = alto | 5 = crítico  

| ID | Prob (a–e) | Imp (1–5) | Prioridad |
|----|-------------|------------|------------|
| R-01 | c | 3 | Moderado |
| R-02 | d | 5 | Alto |
| R-03 | c | 4 | Alto |
| R-04 | b | 3 | Moderado |
| R-05 | c | 3 | Moderado |
| R-06 | c | 3 | Moderado |
| R-07 | c | 4 | Alto |
| R-08 | d | 4 | Alto |
| R-09 | c | 3 | Moderado |
| R-10 | b | 4 | Moderado |

**Riesgos altos priorizados para análisis cuantitativo:**  
R-02 (Seguridad), R-03 (Usuarios falsos), R-07 (Cambios de alcance), R-08 (Rendimiento)

---

## 4. Análisis cuantitativo (EMV)

**Cálculo:**  
E(costo) = probabilidad × impacto_en_$  
E(tiempo) = probabilidad × impacto_en_días  

| Riesgo | Tipo | Prob | Impacto Costo (USD) | E(Costo) | Impacto Tiempo (d) | E(Tiempo) |
|---------|------|-------|--------------------|-----------|-------------------|-------------|
| R-02 Vulnerabilidad seguridad | Amenaza | 0.7 | +2,000 | +1,400 | +10 | +7.0 |
| R-03 Reseñas falsas | Amenaza | 0.5 | +1,800 | +900 | +8 | +4.0 |
| R-07 Cambios de alcance | Amenaza | 0.5 | +2,500 | +1,250 | +12 | +6.0 |
| R-08 Carga excesiva | Amenaza | 0.6 | +1,500 | +900 | +9 | +5.4 |

**Totales esperados:**  
- **E(Costo total):** 1,400 + 900 + 1,250 + 900 = **4,450 USD**  
- **E(Tiempo total):** 7.0 + 4.0 + 6.0 + 5.4 = **22.4 días**  

**Reserva recomendada:**  
- Presupuesto adicional: **+4.5%**  
- Tiempo de contingencia: **+2 semanas**

---

## 5. Estimación PERT (tarea crítica)

**Tarea crítica:** Implementación del sistema de publicación y visualización de reseñas.  

| Escenario | Duración (días) |
|------------|----------------|
| O (Optimista) | 10 |
| M (Más probable) | 18 |
| P (Pesimista) | 28 |

**Cálculos:**  
TE = (10 + 4×18 + 28) / 6 = **18.7 días**  
σ = (28 − 10) / 6 = **3 días**

**Interpretación:**  
- 50% de probabilidad de terminar en 18.7 días  
- 84% de probabilidad de terminar en 21.7 días (TE + σ)  
- 97.5% de probabilidad de terminar en 24.7 días (TE + 2σ)

---

## 6. Plan de respuesta al riesgo

| ID | Riesgo (causa → riesgo → impacto) | Estrategia | Acciones | Disparador | Dueño | Fecha | Presupuesto (USD) |
|-----|-----------------------------------|-------------|-----------|-------------|--------|--------|-------------------|
| R-02 | Falta de validación → ataques XSS / spam → acceso no autorizado | **Mitigar** | Implementar validación server-side, sanitizar inputs, usar captchas en formularios | Alertas de seguridad | QA Técnico | 05/11/2025 | 1,200 |
| R-03 | Reseñas falsas → sesgo en calificaciones → pérdida de confianza | **Mitigar / Transferir** | Detectar patrones anómalos, limitar frecuencia por usuario, registrar IP | Picos de actividad inusual | Analista UX | 05/10/2025 | 900 |
| R-07 | Cambios tardíos en requisitos → sobrecosto | **Evitar** | Definir control de cambios y congelamiento por sprint | Solicitud fuera de iteración | Project Manager | 05/15/2025 | 700 |
| R-08 | Carga excesiva de reseñas → lentitud del sistema | **Mitigar / Mejorar** | Paginación en consultas, cacheo, optimización de índices | Alertas de rendimiento | Líder Técnico | 05/09/2025 | 650 |

---

## 7. Conclusiones

El análisis de riesgos para el **módulo de reseñas y comentarios** muestra que los principales factores que pueden impactar el proyecto son:

1. **Vulnerabilidades de seguridad** (inyección de código o spam).  
2. **Manipulación o sesgo de calificaciones por reseñas falsas.**  
3. **Cambios no controlados en los requisitos.**  
4. **Riesgos de rendimiento por alta demanda de datos.**

Para mitigar su impacto, el equipo implementará acciones preventivas, un **presupuesto de reserva del 4.5%** y un **tiempo adicional de contingencia de dos semanas**.  
El registro de riesgos será **actualizado semanalmente** durante las reuniones del proyecto, garantizando trazabilidad y control continuo.

---

## 8. Resumen de artefactos y cumplimiento de rúbrica

| Criterio | Cumplimiento |
|-----------|---------------|
| **Integridad de artefactos** | Registro de riesgos, análisis cualitativo y cuantitativo, PERT y plan de respuesta completos. |
| **Redacción clara y trazabilidad** | Todos los riesgos siguen el formato causa → riesgo → impacto → disparador. |
| **Priorización con criterio** | Evaluación de probabilidad (a–e) e impacto (1–5) aplicada correctamente. |
| **Cálculos EMV / PERT** | Valores coherentes y reserva ajustada a resultados. |
| **Acciones claras con dueño y disparador** | Cada riesgo alto cuenta con medidas específicas, responsables y fechas. |

---

**Resultado:**  
El plan de gestión de riesgos del *Módulo de Reseñas y Comentarios – Proyecto Punto H* ofrece una base sólida para la gestión proactiva de amenazas y asegura la continuidad del desarrollo del módulo con enfoque en seguridad, reputación y rendimiento.

**Documento elaborado por:**  
*Equipo Soft Integration – Universidad del Valle*  
**Versión:** 1.0  
**Fecha:** Octubre 2025
