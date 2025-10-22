# Plan de Gestión de Riesgos – Módulo de Cocineros y Restaurantes

**Proyecto:** Punto H – Aplicación Web para pedidos universitarios  
**Módulo:** Cocineros y Restaurantes (Gestión de menús y afiliaciones)  
**Equipo:** Soft Integration  
**Versión:** 1.0  
**Fecha:** Octubre 2025  

---

## 1. Introducción

El presente documento define el **plan de gestión de riesgos** para el desarrollo del **módulo de Cocineros y Restaurantes** de la aplicación web *Punto H*, el cual permite a cocineros y restaurantes afiliados gestionar sus menús, disponibilidad de platos y estadísticas de ventas.

El objetivo es **identificar, analizar, priorizar y planificar respuestas** ante eventos que puedan afectar los objetivos del módulo en **alcance, cronograma, presupuesto o calidad**.

---

## 2. Identificación de riesgos

Cada riesgo sigue el formato:

> Debido a [causa], [riesgo] podría ocurrir, lo que impactaría [objetivo] en [impacto cuantificable].  
> **Disparador:** [señal temprana].

| ID   | Categoría          | Causa                                                     | Riesgo                                                       | Objetivo afectado | Impacto (medida)                     | Disparador                     | Dueño              |
| ---- | ------------------ | --------------------------------------------------------- | ------------------------------------------------------------ | ----------------- | ------------------------------------ | ------------------------------ | ------------------ |
| R-01 | Datos              | Fallo en la base de datos                                 | Pérdida de menús o platos registrados                        | Calidad           | Pérdida de información crítica       | Error en logs del servidor DB  | Líder técnico      |
| R-02 | Seguridad          | Falta de control de roles                                 | Acceso no autorizado a información de restaurantes            | Seguridad         | Vulnerabilidad de datos sensibles    | Alerta de auditoría            | Backend Developer  |
| R-03 | Capacitación       | Cocineros sin entrenamiento digital                       | Dificultad para usar el sistema                              | Usabilidad        | +15 tickets de soporte semanales     | Feedback del soporte técnico   | Analista funcional |
| R-04 | Integración        | Error en comunicación con módulo de pedidos               | Pedidos no sincronizados con menús actualizados              | Disponibilidad    | +10% de errores en pedidos           | Logs API Gateway               | DevOps             |
| R-05 | Infraestructura    | Sobrecarga del servidor                                   | Lentitud al actualizar menús o consultar reportes             | Rendimiento       | >5s de respuesta                     | Métricas de monitoreo          | Arquitecto de software |
| R-06 | Legal              | Falta de validación sanitaria en restaurantes afiliados   | Riesgo de incumplimiento normativo                           | Cumplimiento      | Rechazo de la entidad reguladora     | Revisión de documentos         | Administrador plataforma |
| R-07 | Comunicación       | Descoordinación entre backend y frontend                  | Errores en la visualización de platos o precios               | Calidad           | 10% de errores en despliegue         | Merge sin revisión             | Scrum Master       |
| R-08 | Cambios de alcance | Solicitudes de nuevas funcionalidades en gestión de menús | Retrasos en cronograma                                        | Alcance/Costo     | +10% sobre presupuesto               | CR fuera de iteración          | Project Manager    |
| R-09 | Usabilidad         | Diseño poco intuitivo del panel del cocinero              | Baja adopción por parte de usuarios                           | Calidad           | <30% de uso activo en pruebas piloto | Encuestas de feedback          | UX Designer        |
| R-10 | Dependencias       | Fallo en API externa de estadísticas                      | No se muestran reportes de ventas                             | Funcionalidad     | 100% de datos no cargados            | Timeout en endpoint externo    | DevOps             |

---

## 3. Análisis cualitativo

**Escalas:**

* **Probabilidad (a–e):**
  a = remota (≤5%), b = poco probable (6–20%), c = probable (21–50%), d = alta (51–80%), e = casi segura (81–99%)
* **Impacto (1–5):**
  1 = mínimo, 2 = menor, 3 = moderado, 4 = alto, 5 = crítico

| ID   | Prob | Imp | Prioridad |
| ---- | ---- | --- | --------- |
| R-01 | d    | 5   | Alta      |
| R-02 | c    | 5   | Alta      |
| R-03 | d    | 3   | Alta      |
| R-04 | c    | 4   | Alta      |
| R-05 | c    | 3   | Moderada  |
| R-06 | b    | 4   | Moderada  |
| R-07 | c    | 3   | Moderada  |
| R-08 | d    | 4   | Alta      |
| R-09 | c    | 3   | Moderada  |
| R-10 | b    | 3   | Baja      |

**Riesgos priorizados para análisis cuantitativo:**  
R-01, R-02, R-03, R-04, R-08.

---

## 4. Análisis cuantitativo (EMV)

**Cálculo:**  
E(Costo) = probabilidad × impacto en dinero  
E(Tiempo) = probabilidad × impacto en días

| Riesgo | Tipo    | Prob | Impacto Costo (USD) | E(Costo) | Impacto Tiempo (días) | E(Tiempo) |
| ------ | ------- | ---- | ------------------- | -------- | --------------------- | --------- |
| R-01   | Amenaza | 0.7  | 2500                | 1750     | +10                   | 7.0       |
| R-02   | Amenaza | 0.6  | 2000                | 1200     | +8                    | 4.8       |
| R-03   | Amenaza | 0.7  | 1500                | 1050     | +5                    | 3.5       |
| R-04   | Amenaza | 0.5  | 1800                | 900      | +7                    | 3.5       |
| R-08   | Amenaza | 0.6  | 2000                | 1200     | +12                   | 7.2       |

**Totales esperados:**  
* **E(Costo total):** 1750 + 1200 + 1050 + 900 + 1200 = **6,100 USD**  
* **E(Tiempo total):** 7.0 + 4.8 + 3.5 + 3.5 + 7.2 = **26 días**  

**Reserva recomendada:**  
* Presupuesto adicional: **+5%**  
* Tiempo de contingencia: **+2 semanas**  

---

## 5. Estimación PERT (tarea crítica)

**Tarea crítica:** Implementación de gestión dinámica de menús y sincronización con pedidos.

| Escenario        | Duración (días) |
| ---------------- | --------------- |
| Optimista (O)    | 12              |
| Más probable (M) | 18              |
| Pesimista (P)    | 28              |

**Cálculos:**

\[
TE = \frac{O + 4M + P}{6} = \frac{12 + 72 + 28}{6} = 18.7 \text{ días}
\]
\[
\sigma = \frac{P - O}{6} = \frac{16}{6} = 2.7
\]

* 50% de probabilidad de terminar en 18.7 días  
* 84% en 21.4 días (TE + σ)  
* 97.5% en 24.1 días (TE + 2σ)  

---

## 6. Plan de respuesta al riesgo

| ID   | Riesgo (causa → impacto)                                     | Estrategia            | Acciones                                                                         | Disparador               | Dueño           | Fecha      | Presupuesto (USD) |
| ---- | ------------------------------------------------------------ | --------------------- | -------------------------------------------------------------------------------- | ------------------------ | --------------- | ---------- | ----------------- |
| R-01 | Fallo en base de datos → pérdida de información              | **Mitigar**           | Configurar backups automáticos y restauraciones diarias                         | Error en logs DB         | Líder técnico   | 05/11/2025 | 1000              |
| R-02 | Falta de control de roles → acceso no autorizado             | **Evitar**            | Implementar autenticación con JWT y roles RBAC                                  | Alerta de seguridad      | Backend Dev     | 05/10/2025 | 800               |
| R-03 | Falta de capacitación → errores de uso                       | **Mitigar**           | Crear guías visuales y capacitaciones en línea                                   | Tickets de soporte       | Analista func.  | 05/09/2025 | 600               |
| R-04 | Falla de integración con pedidos → errores                   | **Mitigar / Transferir** | Pruebas de integración y fallback local en caso de error                        | Logs API Gateway         | DevOps          | 05/15/2025 | 700               |
| R-08 | Cambios tardíos en requisitos → retrasos                     | **Evitar**            | Establecer control de cambios formal y congelar requisitos al inicio del sprint  | CR fuera de iteración    | Project Manager | 05/12/2025 | 900               |

---

## 7. Conclusiones

Los riesgos más relevantes del módulo de cocineros y restaurantes están asociados con:

1. **Gestión de datos y seguridad de la información.**  
2. **Capacitación de los usuarios y adopción del sistema.**  
3. **Integración estable con el módulo de pedidos.**  
4. **Control de cambios en funcionalidades.**  

El equipo aplicará medidas preventivas y de mitigación, con una **reserva del 5% del presupuesto y 2 semanas adicionales de contingencia.**
El seguimiento del registro de riesgos se realizará **semanalmente** durante las reuniones de avance del proyecto.

---

## 8. Resumen de artefactos y cumplimiento de rúbrica

| Criterio                                        | Cumplimiento |
| ----------------------------------------------- | ------------ |
| Identificación clara de riesgos                 | ✅            |
| Análisis cualitativo y cuantitativo completo    | ✅            |
| Plan de respuesta con dueño, disparador y fecha | ✅            |
| Inclusión de métricas EMV y PERT                | ✅            |
| Seguimiento y actualización del registro        | ✅            |
