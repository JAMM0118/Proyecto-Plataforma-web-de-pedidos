---
title: Plan de Gestión de Riesgos – Proyecto Punto H

---

# Plan de Gestión de Riesgos – Proyecto Punto H

**Proyecto:** Punto H – Aplicación Web para pedidos universitarios  
**Equipo:** Soft Integration  
**Fecha:** Octubre 2025  
**Versión:** 1.0  

---

## 1. Introducción

El presente documento define el **plan de gestión de riesgos** para el desarrollo del módulo de **pedidos** de la aplicación web **Punto H**, la cual conecta a estudiantes de Univalle con restaurantes y cocineros independientes.

El objetivo es **identificar, analizar, priorizar y planificar respuestas** ante eventos que puedan afectar los objetivos del proyecto en **alcance, cronograma, presupuesto o calidad**.

---

## 2. Identificación de riesgos

Cada riesgo se redacta siguiendo el formato:  
> Debido a [causa], [riesgo] podría ocurrir, lo que impactaría [objetivo] en [impacto cuantificable].  
> Disparador: [señal temprana].

| ID | Categoría | Causa | Riesgo | Objetivo afectado | Impacto (medida) | Disparador | Dueño |
|----|------------|--------|---------|-------------------|------------------|-------------|--------|
| R-01 | Proveedor | Retrasos de API externa para pagos | La integración de pasarela de pagos podría no completarse a tiempo | Cronograma | +14 días | Issue sin respuesta 48h | Líder técnico |
| R-02 | Datos | Falta de información completa de restaurantes y menús | Los listados podrían aparecer incompletos o erróneos | Calidad | Catálogo con <85% de datos | Reporte de QA semanal | Analista funcional |
| R-03 | Equipo | Baja experiencia del equipo en Node.js | Retrasos en la implementación del backend | Cronograma | +10 días | Retraso >3 días en primeras tareas | Líder de desarrollo |
| R-04 | Usuarios | Poca participación de estudiantes en pruebas piloto | Fallos no detectados en usabilidad y flujo de pedidos | Calidad | Feedback insuficiente (<5 usuarios activos en prueba) | Reporte de pruebas vacío | Analista UX |
| R-05 | Infraestructura | Fallas en despliegue o servidores | Caídas en ambiente de pruebas o producción | Disponibilidad | Downtime >5% mensual | Alertas del servidor | DevOps |
| R-06 | Cambios de alcance | Solicitudes tardías de nuevas funciones | Atrasos y sobrecostos en cronograma | Alcance y costo | +8% presupuesto | Solicitud de cambio fuera de iteración | Project Manager |
| R-07 | Seguridad | Implementación inadecuada de autenticación JWT | Acceso no autorizado a información sensible | Calidad/Seguridad | Vulnerabilidad crítica OWASP | Alerta de auditoría | Líder backend |
| R-08 | Pagos | Errores en procesamiento de pagos | Transacciones fallidas o duplicadas | Presupuesto y reputación | Pérdidas estimadas 5% | Logs de errores en API de pagos | QA técnico |
| R-09 | Comunicación | Falta de coordinación entre desarrolladores frontend y backend | Integraciones fallidas entre módulos | Cronograma | +7 días | Merge requests sin revisión | Scrum Master |
| R-10 | Cronograma | Subestimación de tareas críticas | Entregas fuera del sprint planificado | Cronograma | +10 días | Burn-down con desviación >20% | Project Manager |

---

## 3. Análisis cualitativo

Escalas:
- **Probabilidad (a–e):**  
  a=remota (≤5%), b=poco probable (6–20%), c=probable (21–50%), d=altamente probable (51–80%), e=casi con certeza (81–99%).  
- **Impacto (1–5):**  
  1=mínimo, 2=menor, 3=moderado, 4=alto, 5=crítico.

| ID | Prob (a–e) | Imp (1–5) | Prioridad |
|----|-------------|------------|------------|
| R-01 | c | 4 | **Alto** |
| R-02 | b | 3 | Moderado |
| R-03 | d | 3 | **Alto** |
| R-04 | c | 2 | Bajo |
| R-05 | b | 4 | Moderado |
| R-06 | c | 4 | **Alto** |
| R-07 | b | 5 | Moderado |
| R-08 | c | 3 | Moderado |
| R-09 | d | 3 | **Alto** |
| R-10 | c | 3 | Moderado |

Riesgos **altos** priorizados para análisis cuantitativo:
- R-01: Retraso proveedor de pagos  
- R-03: Baja experiencia del equipo  
- R-06: Cambios de alcance  
- R-09: Falta de coordinación entre equipos  

---

## 4. Análisis cuantitativo (EMV)

Cálculo:  
E(costo) = probabilidad × impacto_en_$.  
E(tiempo) = probabilidad × impacto_en_días.

| Riesgo | Tipo | Prob | Impacto Costo (USD) | E(Costo) | Impacto Tiempo (d) | E(Tiempo) |
|---------|------|------|--------------------|-----------|--------------------|------------|
| R-01 Retraso proveedor | Amenaza | 0.6 | +2,000 | +1,200 | +14 | +8.4 |
| R-03 Experiencia limitada | Amenaza | 0.7 | +1,500 | +1,050 | +10 | +7.0 |
| R-06 Cambios de alcance | Amenaza | 0.5 | +2,500 | +1,250 | +12 | +6.0 |
| R-09 Falta de coordinación | Amenaza | 0.6 | +1,000 | +600 | +7 | +4.2 |

**Totales esperados:**  
- **E(Costo total):** 1,200 + 1,050 + 1,250 + 600 = **4,100 USD**  
- **E(Tiempo total):** 8.4 + 7.0 + 6.0 + 4.2 = **25.6 días**

**Reserva recomendada:**  
- **Presupuesto adicional:** +4%  
- **Tiempo de contingencia:** +2 semanas  

---

## 5. Estimación PERT (ejemplo de tarea crítica)

Tarea crítica: *Implementación del módulo de pedidos y notificaciones.*

| Escenario | Duración (días) |
|------------|----------------|
| O (Optimista) | 15 |
| M (Más probable) | 22 |
| P (Pesimista) | 35 |

Cálculos:  
- **TE (Tiempo Esperado)** = (15 + 4×22 + 35) / 6 = **23 días**  
- **σ (Desviación Estándar)** = (35 − 15) / 6 = **3.3 días**

Interpretación:
- 50% de probabilidad de terminar en **23 días**.  
- 84% de probabilidad de terminar en **26.3 días (TE + σ)**.  
- 97.5% de probabilidad de terminar en **29.6 días (TE + 2σ)**.

---

## 6. Plan de respuesta al riesgo

El siguiente plan define las estrategias de acción para los riesgos **altos** identificados (R-01, R-03, R-06 y R-09).  
Cada riesgo cuenta con una estrategia, acciones concretas, disparadores, responsables y presupuesto asignado.

| ID | Riesgo (causa → riesgo → impacto) | Estrategia | Acciones | Disparador | Dueño | Fecha | Presupuesto (USD) |
|----|-----------------------------------|-------------|-----------|-------------|--------|--------|--------------------|
| R-01 | Proveedor de pasarela de pagos con demoras → integración no completada a tiempo → +14 días de retraso en entregas | **Mitigar** | Realizar una prueba de integración (PoC) anticipada; establecer contrato con penalidad por retraso; preparar plan B con otro proveedor de pagos | Issue sin respuesta por más de 48h | Líder técnico | 05/11/2025 | 1,200 |
| R-03 | Baja experiencia del equipo en Node.js → retrasos en implementación backend → +10 días al cronograma | **Mitigar / Mejorar** | Realizar capacitación express en Node.js y Express; asignar mentor técnico; dividir tareas críticas entre desarrolladores con más experiencia | Retraso >3 días en primeras tareas del sprint | Líder de desarrollo | 05/08/2025 | 900 |
| R-06 | Solicitudes tardías de nuevas funcionalidades → sobrecarga de tareas → +8% presupuesto | **Evitar** | Implementar congelamiento de requisitos al inicio de cada sprint; definir proceso formal de control de cambios (CR); comunicar límites de alcance | Solicitud de cambio fuera de iteración | Project Manager | 05/15/2025 | 700 |
| R-09 | Falta de comunicación entre frontend y backend → integraciones fallidas → +7 días de retraso | **Mitigar / Transferir** | Establecer reuniones de sincronización diaria; usar Swagger para documentar endpoints; aplicar revisión cruzada antes de mergear código | Merge request sin revisión o error de integración en test | Scrum Master | 05/10/2025 | 500 |

---

## 7. Conclusiones

El análisis de riesgos demuestra que los principales factores que podrían impactar el proyecto **Punto H** son:
1. La **dependencia de proveedores externos** (pasarela de pagos).  
2. La **experiencia técnica del equipo** en nuevas tecnologías.  
3. Los **cambios no controlados en el alcance**.  
4. La **coordinación entre equipos de desarrollo**.

Para reducir su efecto, el equipo implementará acciones tempranas de mitigación, reserva de presupuesto (≈4%) y de tiempo (+2 semanas).  
El **seguimiento y actualización** del registro de riesgos se realizará semanalmente en las reuniones del equipo de proyecto, asegurando trazabilidad y respuesta oportuna.

---


Documento elaborado por: *Nicolas Rojas, Esteban Revelo, Jhon Martinez, Juan Posso*  
*Equipo Soft Integration – Universidad del Valle*  
*Versión:* 1.0  
*Fecha:* Octubre 2025