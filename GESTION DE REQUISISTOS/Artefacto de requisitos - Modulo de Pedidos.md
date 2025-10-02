# Artefactos de requisitos - Módulo Pedidos

---

## 1. Plan de gestión de requisitos

### 1.1 Técnicas de elicitation a utilizar
- **Entrevistas**: estudiantes (usuarios finales) y restaurantes/cocineros independientes.  
- **Grupos focales**: 5–10 estudiantes para validar expectativas sobre reservas y pedidos.  
- **Talleres JAD**: Soft Integration + Bienestar universitario para definir reglas de negocio (descuentos, subsidios).  
- **Observación**: prácticas actuales de pedidos en restaurantes del sector.  
- **Prototipos**: pantallas de “Hacer pedido” y “Mis pedidos” para validación temprana.  

### 1.2 Responsables
- *Levantamiento de requisitos*: Analista de requisitos y líder técnico de Soft Integration.  
- *Aprobación*: Gerente del proyecto (Soft Integration) + Representante de Bienestar Universitario.  

### 1.3 Documentación
- Requisitos registrados en plantillas RF y RNF.  
- Historias de usuario documentadas en backlog ágil (Jira/Trello).  
- RTM mantenida en hoja colaborativa (Google Sheets).  

### 1.4 Priorización
- Método **MoSCoW**: MUST (imprescindible), SHOULD (importante), COULD (deseable), WON’T (fuera de alcance inmediato).  

### 1.5 Control de cambios
- Uso de un formato **CR (Change Request)** con: ID, descripción, justificación, impacto, decisión.  
- Comité de requisitos analiza impacto en tiempo, costo y calidad.  
- Actualización de backlog, RTM y SRS cuando aplique.  

---

## 2. Catálogo de requisitos

### 2.1 Requisitos funcionales (RF)

| ID    | Nombre | Descripción | Origen | Prioridad | Criterios de aceptación |
|-------|---------|-------------|--------|-----------|--------------------------|
| RF-01 | Crear pedido de comida | El estudiante puede seleccionar un restaurante o cocinero, elegir platos y confirmar pedido. | Estudiantes | MUST | Dado que el estudiante accede al catálogo, cuando selecciona un menú y confirma, entonces el sistema registra el pedido y genera un comprobante. |
| RF-02 | Reservar pedido para una hora específica | El estudiante puede programar un pedido para recogida/consumo en un horario definido. | Estudiantes | MUST | Dado que el estudiante accede a su carrito, cuando selecciona “reservar hora”, entonces el pedido queda agendado en el sistema. |
| RF-03 | Consultar estado del pedido | El estudiante puede consultar si el pedido está pendiente, confirmado, en preparación, entregado o cancelado. | Estudiantes | MUST | Dado que el estudiante abre “Mis pedidos”, cuando consulta un pedido, entonces el sistema muestra el estado actualizado. |
| RF-04 | Cancelar pedido | El estudiante puede cancelar un pedido antes de que sea confirmado/preparado. | Estudiantes | SHOULD | Dado que el pedido está pendiente, cuando selecciona “Cancelar”, entonces el sistema marca el pedido como cancelado y notifica al proveedor. |
| RF-05 | Filtrar pedidos | El estudiante puede filtrar menús por tipo de comida (vegana, vegetariana, rápida), precio o cercanía. | Estudiantes | SHOULD | Dado que el estudiante abre el catálogo, cuando aplica filtros, entonces el sistema muestra solo resultados que cumplen las condiciones. |
| RF-06 | Pagar pedido en línea | El estudiante puede pagar su pedido a través de una pasarela de pagos segura. | Estudiantes / Restaurantes | COULD | Dado que el estudiante confirma un pedido, cuando selecciona “Pagar en línea”, entonces el sistema procesa la transacción y actualiza el estado a “Pagado”. |
| RF-07 | Notificar cambios en el pedido | El sistema debe enviar notificaciones al estudiante sobre aceptación, rechazo o actualización del pedido. | Estudiantes | MUST | Dado que el estado de un pedido cambia, cuando se procesa la acción, entonces el sistema envía notificación por correo y alerta en la app. |
| RF-08 | Calificar pedido y proveedor | El estudiante puede dejar una reseña y puntuación después de recibir el pedido. | Estudiantes | SHOULD | Dado que un pedido está marcado como entregado, cuando el estudiante lo califica, entonces el sistema registra la reseña en la base de datos. |
| RF-09 | Visualizar historial de pedidos | El estudiante puede revisar sus pedidos anteriores con detalles y calificaciones. | Estudiantes | COULD | Dado que accede a “Historial”, cuando selecciona un pedido anterior, entonces el sistema muestra fecha, platos y proveedor. |
| RF-10 | Gestión de pedidos por restaurantes/cocineros | Los proveedores pueden aceptar, rechazar y actualizar el estado de los pedidos recibidos. | Restaurantes/cocineros | MUST | Dado que un proveedor recibe un pedido, cuando accede al panel de gestión, entonces puede confirmarlo o rechazarlo, generando la notificación al estudiante. |

---

### 2.2 Requisitos no funcionales (RNF)

| ID    | Categoría | Enunciado | Métrica/Umbral | Verificación | Prioridad |
|-------|------------|-----------|----------------|--------------|-----------|
| RNF-01 | Rendimiento | El sistema debe mostrar disponibilidad de menú en menos de 3 segundos en el 95% de las consultas. | ≤ 3s | Prueba de carga con 100 usuarios simultáneos | MUST |
| RNF-02 | Disponibilidad | El módulo de pedidos debe estar disponible el 99% del tiempo mensual. | ≥ 99% uptime | Monitoreo SLA | MUST |
| RNF-03 | Seguridad de pagos | Todas las transacciones deben cumplir con PCI DSS y usarse bajo TLS 1.3. | 100% de transacciones | Auditoría de seguridad | MUST |
| RNF-04 | Escalabilidad | El sistema debe soportar 500 pedidos diarios en la fase inicial, con capacidad de duplicar en 6 meses. | ≥ 500 pedidos/día | Prueba de estrés | SHOULD |
| RNF-05 | Usabilidad | El estudiante debe poder completar un pedido en máximo 5 pasos. | ≤ 5 pasos | Prueba de usabilidad con 10 usuarios | SHOULD |
| RNF-06 | Confidencialidad de datos | Los datos personales de estudiantes deben estar cifrados en la base de datos. | 100% encriptados | Revisión técnica | MUST |

---

## 3. Prototipo de baja fidelidad
1. **Pantalla “Hacer pedido”**: muestra lista de menús, botones “Agregar al carrito”, opción de programar hora.  
2. **Pantalla “Mis pedidos”**: listado de pedidos con estados (pendiente, confirmado, entregado, cancelado).  
3. **Pantalla “Detalle pedido”**: información de platos seleccionados, estado en tiempo real, botones cancelar/reprogramar, sección para calificación.  

> *(Faltan imágenes del prototipo)*

---

## 4. Matriz de trazabilidad inicial (RTM)

| Req ID | Descripción | Historia de usuario | Componente | Caso de prueba | Estado |
|--------|-------------|---------------------|-------------|----------------|--------|
| RF-01  | Crear pedido de comida | HU-01 | pedidos-svc | TC-PED-01 | Pendiente |
| RF-03  | Consultar estado de pedido | HU-02 | pedidos-svc | TC-PED-02 | Pendiente |
| RF-06  | Pagar pedido en línea | HU-03 | pagos-svc | TC-PAY-01 | Pendiente |
| RF-08  | Calificar pedido/proveedor | HU-04 | feedback-svc | TC-FB-01 | Pendiente |
| RNF-01 | Tiempo de respuesta ≤ 3s | HU-01 | backend | PERF-01 | Pendiente |
| RNF-03 | Seguridad en pagos PCI DSS | HU-03 | gateway | SEC-01 | Pendiente |

---

## 5. Procedimiento de control de cambios

### 5.1 Formato CR (Change Request)
- **ID:** CR-##  
- **Descripción del cambio:** (ej. añadir nueva forma de pago)  
- **Justificación:** necesidad del usuario, cumplimiento legal, etc.  
- **Impacto:** alcance, tiempo, costo, calidad.  
- **Recomendación técnica:** factibilidad del equipo.  
- **Decisión:** Aprobado / Rechazado / Diferido.  
- **Responsable:** Comité de proyecto (Soft Integration + Bienestar).  

### 5.2 Flujo de cambios
1. Stakeholder propone el cambio vía CR.  
2. Comité analiza impacto.  
3. Se decide y documenta la resolución.  
4. Se actualiza backlog, RTM y documentación.  
5. Se comunica a todos los interesados.  
