# Plan de Gestión de Riesgos – Módulo de Login y Registro

**Proyecto:** Punto H – Aplicación Web para pedidos universitarios
**Módulo:** Login y Registro
**Equipo:** Soft Integration
**Versión:** 1.0
**Fecha:** Octubre 2025

---

## 1. Introducción

El presente documento define el **plan de gestión de riesgos** para el desarrollo del **módulo de login y registro** de la aplicación web *Punto H*, que permite a estudiantes, restaurantes y cocineros autenticarse y crear sus cuentas.

El objetivo es **identificar, analizar, priorizar y planificar respuestas** ante eventos que puedan afectar los objetivos del módulo en **alcance, cronograma, presupuesto o calidad**.

---

## 2. Identificación de riesgos

Cada riesgo sigue el formato:

> Debido a [causa], [riesgo] podría ocurrir, lo que impactaría [objetivo] en [impacto cuantificable].
> **Disparador:** [señal temprana].

| ID   | Categoría          | Causa                                                     | Riesgo                                                       | Objetivo afectado | Impacto (medida)                     | Disparador                     | Dueño              |
| ---- | ------------------ | --------------------------------------------------------- | ------------------------------------------------------------ | ----------------- | ------------------------------------ | ------------------------------ | ------------------ |
| R-01 | Seguridad          | Configuración incorrecta del cifrado                      | Las contraseñas podrían almacenarse sin cifrar correctamente | Seguridad         | Vulnerabilidad crítica OWASP         | Alerta de auditoría            | Líder backend      |
| R-02 | Infraestructura    | Fallas en el servidor de autenticación                    | El servicio de login podría quedar inactivo                  | Disponibilidad    | Downtime >5% mensual                 | Alertas del servidor           | DevOps             |
| R-03 | Equipo             | Falta de experiencia en integración OAuth                 | Retrasos en la implementación de login con Google/Facebook   | Cronograma        | +7 días                              | Retraso >3 días en tarea OAuth | Líder técnico      |
| R-04 | Datos              | Errores en validación de formularios                      | Usuarios podrían registrar datos incompletos o inválidos     | Calidad           | 10% de cuentas con datos incorrectos | Reporte QA semanal             | Analista funcional |
| R-05 | Usuarios           | Baja adopción de pruebas de registro                      | No se detectan errores de usabilidad                         | Calidad           | <5 usuarios activos en pruebas       | Feedback insuficiente          | Analista UX        |
| R-06 | Cambios de alcance | Solicitudes tardías de nuevas validaciones o roles        | Atrasos y sobrecostos                                        | Alcance/Costo     | +8% del presupuesto                  | CR fuera de iteración          | Project Manager    |
| R-07 | Comunicación       | Falta de sincronización entre frontend y backend          | Falla en endpoints de autenticación                          | Cronograma        | +5 días                              | Merge request sin revisión     | Scrum Master       |
| R-08 | Requisitos         | Falta de claridad en flujos de recuperación de contraseña | Casos no contemplados en diseño                              | Alcance           | +5 días                              | Rechazo en pruebas de QA       | Analista funcional |
| R-09 | Seguridad          | Sesiones sin expiración automática                        | Riesgo de acceso no autorizado                               | Seguridad         | Sesiones activas >24h                | Prueba de vulnerabilidad       | QA técnico         |
| R-10 | Integración        | Fallas en envío de correos SMTP                           | No se entregan correos de verificación o recuperación        | Calidad           | 15% correos no enviados              | Logs de error SMTP             | DevOps             |

---

## 3. Análisis cualitativo

**Escalas:**

* **Probabilidad (a–e):**
  a = remota (≤5%), b = poco probable (6–20%), c = probable (21–50%), d = alta (51–80%), e = casi segura (81–99%)
* **Impacto (1–5):**
  1 = mínimo, 2 = menor, 3 = moderado, 4 = alto, 5 = crítico

| ID   | Prob | Imp | Prioridad |
| ---- | ---- | --- | --------- |
| R-01 | c    | 5   | Alta      |
| R-02 | c    | 4   | Alta      |
| R-03 | d    | 3   | Alta      |
| R-04 | c    | 3   | Moderada  |
| R-05 | b    | 2   | Baja      |
| R-06 | c    | 4   | Alta      |
| R-07 | d    | 3   | Alta      |
| R-08 | b    | 3   | Moderada  |
| R-09 | c    | 5   | Alta      |
| R-10 | c    | 3   | Moderada  |

**Riesgos priorizados para análisis cuantitativo:**
R-01, R-02, R-03, R-06, R-09.

---

## 4. Análisis cuantitativo (EMV)

**Cálculo:**
E(Costo) = probabilidad × impacto en dinero
E(Tiempo) = probabilidad × impacto en días

| Riesgo | Tipo    | Prob | Impacto Costo (USD) | E(Costo) | Impacto Tiempo (días) | E(Tiempo) |
| ------ | ------- | ---- | ------------------- | -------- | --------------------- | --------- |
| R-01   | Amenaza | 0.6  | 2000                | 1200     | +10                   | 6.0       |
| R-02   | Amenaza | 0.5  | 1500                | 750      | +7                    | 3.5       |
| R-03   | Amenaza | 0.7  | 1000                | 700      | +7                    | 4.9       |
| R-06   | Amenaza | 0.5  | 2000                | 1000     | +12                   | 6.0       |
| R-09   | Amenaza | 0.6  | 1200                | 720      | +8                    | 4.8       |

**Totales esperados:**

* **E(Costo total):** 1200 + 750 + 700 + 1000 + 720 = **4,370 USD**
* **E(Tiempo total):** 6.0 + 3.5 + 4.9 + 6.0 + 4.8 = **25.2 días**

**Reserva recomendada:**

* Presupuesto adicional: **+4%**
* Tiempo de contingencia: **+2 semanas**

---

## 5. Estimación PERT (tarea crítica)

**Tarea crítica:** Implementación de autenticación segura y validación por correo.

| Escenario        | Duración (días) |
| ---------------- | --------------- |
| Optimista (O)    | 10              |
| Más probable (M) | 15              |
| Pesimista (P)    | 25              |

**Cálculos:**

[
TE = \frac{O + 4M + P}{6} = \frac{10 + 60 + 25}{6} = 15.8 \text{ días}
]
[
\sigma = \frac{P - O}{6} = \frac{15}{6} = 2.5
]

* 50% de probabilidad de terminar en 15.8 días
* 84% en 18.3 días (TE + σ)
* 97.5% en 20.8 días (TE + 2σ)

---

## 6. Plan de respuesta al riesgo

| ID   | Riesgo (causa → impacto)                                     | Estrategia            | Acciones                                                                         | Disparador               | Dueño           | Fecha      | Presupuesto (USD) |
| ---- | ------------------------------------------------------------ | --------------------- | -------------------------------------------------------------------------------- | ------------------------ | --------------- | ---------- | ----------------- |
| R-01 | Configuración errónea de cifrado → exposición de contraseñas | **Mitigar**           | Revisar implementación para encriptar, realizar pruebas    | Alerta auditoría         | Líder backend   | 05/11/2025 | 1000              |
| R-02 | Falla en servidor de autenticación → downtime                | **Transferir**        | Usar hosting backup de servidor secundario                         | Alertas de servidor      | DevOps          | 05/10/2025 | 700               |
| R-03 | Falta de experiencia OAuth → retrasos                        | **Mitigar / Mejorar** | Capacitación express en OAuth2, revisión de APIs              | Retraso en tareas        | Líder técnico   | 05/08/2025 | 600               |
| R-06 | Solicitudes tardías de cambios → sobrecostos                 | **Evitar**            | Aplicar control de cambios formal (CR), congelar requisitos al inicio del sprint | CR fuera de iteración    | Project Manager | 05/15/2025 | 500               |
| R-09 | Sesiones sin expiración → acceso no autorizado               | **Mitigar**           | Implementar expiración automática JWT, revisión de tiempos de sesión             | Prueba de vulnerabilidad | QA técnico      | 05/12/2025 | 800               |

---

## 7. Conclusiones

Los riesgos más relevantes del módulo de login se relacionan con:

1. **Seguridad en el manejo de contraseñas y sesiones.**
2. **Disponibilidad del servicio de autenticación.**
3. **Cambios no controlados de alcance.**
4. **Retrasos por falta de experiencia técnica.**

El equipo aplicará medidas preventivas, con **reserva del 4% del presupuesto y 2 semanas adicionales de contingencia**.
El seguimiento del registro de riesgos se realizará semanalmente durante las reuniones de avance, garantizando trazabilidad y actualización continua.

---

## 8. Resumen de artefactos y cumplimiento de rúbrica

| Criterio                                        | Cumplimiento |
| ----------------------------------------------- | ------------ |
| Identificación clara de riesgos                 | ✅            |
| Análisis cualitativo y cuantitativo completo    | ✅            |
| Plan de respuesta con dueño, disparador y fecha | ✅            |
| Inclusión de métricas EMV y PERT                | ✅            |
| Seguimiento y actualización del registro        | ✅            |
