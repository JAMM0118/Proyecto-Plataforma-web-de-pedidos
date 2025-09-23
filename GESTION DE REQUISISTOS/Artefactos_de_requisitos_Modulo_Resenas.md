
# Artefactos de requisitos – Módulo Reseñas y Comentarios

## 1. Plan de gestión de requisitos

### 1.1 Técnicas de elicitation a utilizar
- Entrevistas: estudiantes (usuarios finales), restaurantes y cocineros independientes.  
- Grupos focales: 5–10 estudiantes para validar expectativas sobre utilidad y formato de las reseñas.  
- Talleres JAD: Soft Integration + Bienestar universitario para definir reglas de moderación.  
- Observación: revisión de sistemas de reseñas en apps similares (UberEats, Rappi).  
- Prototipos: pantallas de “Dejar reseña” y “Ver comentarios” para validación temprana.  

### 1.2 Responsables
- Levantamiento de requisitos: Analista de requisitos y líder técnico de Soft Integration.  
- Aprobación: Gerente del proyecto (Soft Integration) + Representante de Bienestar Universitario.  

### 1.3 Documentación
- Requisitos registrados en plantillas RF y RNF.  
- Historias de usuario documentadas en backlog ágil (Jira/Trello).  
- RTM mantenida en hoja colaborativa (Google Sheets).  

### 1.4 Priorización
- Método **MoSCoW**: MUST, SHOULD, COULD, WON’T.  

### 1.5 Control de cambios
- Uso de formato CR (Change Request) con: ID, descripción, justificación, impacto, decisión.  
- Comité de requisitos analiza impacto en tiempo, costo y calidad.  
- Actualización de backlog, RTM y SRS cuando aplique.  

---

## 2. Catálogo de requisitos

### 2.1 Requisitos funcionales (RF)

| ID    | Nombre                     | Descripción                                                                 | Origen             | Prioridad | Criterios de aceptación |
|-------|-----------------------------|-----------------------------------------------------------------------------|--------------------|-----------|--------------------------|
| RF-01 | Crear reseña                | El usuario puede dejar una reseña escrita y una puntuación (1–5 estrellas).  | Estudiantes        | MUST      | Dado que el pedido está entregado, cuando el usuario selecciona “Dejar reseña”, entonces el sistema registra la reseña. |
| RF-02 | Editar reseña               | El usuario puede modificar una reseña propia dentro de un plazo de 24 horas. | Estudiantes        | SHOULD    | Dado que una reseña existe, cuando el usuario selecciona “Editar”, entonces el sistema actualiza el contenido. |
| RF-03 | Eliminar reseña             | El usuario puede eliminar sus reseñas.                                       | Estudiantes        | SHOULD    | Dado que el usuario accede a sus reseñas, cuando selecciona “Eliminar”, entonces el sistema la retira. |
| RF-04 | Ver reseñas de un pedido    | Los usuarios pueden visualizar reseñas asociadas a un pedido específico.     | Estudiantes        | MUST      | Dado que el usuario abre el detalle de un pedido, cuando consulta reseñas, entonces el sistema muestra lista ordenada. |
| RF-05 | Ver reseñas de proveedor    | Los usuarios pueden consultar todas las reseñas y calificaciones de un proveedor. | Estudiantes    | MUST      | Dado que el usuario accede al perfil del proveedor, cuando selecciona “Ver reseñas”, entonces el sistema muestra comentarios. |
| RF-06 | Filtrar reseñas             | Los usuarios pueden filtrar reseñas por fecha, puntuación o relevancia.      | Estudiantes        | COULD     | Dado que el usuario abre reseñas de un proveedor, cuando aplica filtros, entonces el sistema muestra resultados. |
| RF-07 | Reportar reseña             | Los usuarios y proveedores pueden reportar reseñas ofensivas o fraudulentas. | Usuarios/Proveedores | MUST   | Dado que un usuario encuentra una reseña inadecuada, cuando selecciona “Reportar”, entonces el sistema envía el caso a revisión. |
| RF-08 | Moderar reseñas             | Los administradores pueden revisar y aprobar/rechazar reseñas reportadas.    | Administradores    | MUST      | Dado que una reseña fue reportada, cuando el administrador la revisa, entonces puede aprobarla o retirarla. |
| RF-09 | Calificación promedio       | El sistema calcula y muestra la calificación promedio de cada proveedor.     | Sistema            | MUST      | Dado que un proveedor tiene reseñas, cuando otro usuario consulta el perfil, entonces el sistema muestra el promedio. |

### 2.2 Requisitos no funcionales (RNF)

| ID    | Categoría            | Enunciado                                                              | Métrica/Umbral       | Verificación                        | Prioridad |
|-------|----------------------|------------------------------------------------------------------------|----------------------|-------------------------------------|-----------|
| RNF-01 | Rendimiento          | El sistema debe mostrar reseñas en menos de 2 segundos en el 95% de consultas. | ≤ 2s                 | Prueba de carga con 100 usuarios simultáneos | MUST |
| RNF-02 | Disponibilidad       | El módulo de reseñas debe estar disponible el 99% del tiempo mensual. | ≥ 99% uptime         | Monitoreo SLA                       | MUST |
| RNF-03 | Moderación automática | El sistema debe bloquear automáticamente palabras ofensivas en reseñas. | 100% coincidencias con lista negra | Prueba de contenido | MUST |
| RNF-04 | Escalabilidad        | El sistema debe soportar 1,000 reseñas diarias en la fase inicial.    | ≥ 1,000 reseñas/día  | Prueba de estrés                    | SHOULD |
| RNF-05 | Usabilidad           | El usuario debe poder dejar una reseña en máximo 3 pasos.             | ≤ 3 pasos            | Prueba de usabilidad con 10 usuarios | SHOULD |
| RNF-06 | Confidencialidad     | Los datos personales deben almacenarse cifrados.                      | 100% encriptados     | Revisión técnica                    | MUST |

---

## 3. Prototipo de baja fidelidad
- Pantalla **Dejar reseña**: campo de texto, estrellas, botón “Publicar”.  
- Pantalla **Reseñas del proveedor**: lista de comentarios con puntuación, filtros.  
- Pantalla **Moderación**: lista de reseñas reportadas, botones “Aprobar” / “Eliminar”.  

---

## 4. Matriz de trazabilidad inicial (RTM)

| Req ID | Descripción              | Historia de usuario | Componente      | Caso de prueba | Estado    |
|--------|--------------------------|---------------------|-----------------|----------------|-----------|
| RF-01  | Crear reseña             | HU-RC-01            | feedback-svc    | TC-RC-01       | Pendiente |
| RF-05  | Ver reseñas proveedor    | HU-RC-02            | feedback-svc    | TC-RC-02       | Pendiente |
| RF-07  | Reportar reseña          | HU-RC-03            | moderation-svc  | TC-RC-03       | Pendiente |
| RNF-01 | Tiempo de respuesta ≤ 2s | HU-RC-01            | backend         | PERF-RC-01     | Pendiente |

---

## 5. Procedimiento de control de cambios

### 5.1 Formato CR (Change Request)
- ID: CR-RC-##  
- Descripción del cambio: (ej. añadir reacciones tipo “me gusta” a reseñas).  
- Justificación: necesidad del usuario, cumplimiento de políticas.  
- Impacto: alcance, tiempo, costo, calidad.  
- Recomendación técnica: factibilidad del equipo.  
- Decisión: Aprobado / Rechazado / Diferido.  
- Responsable: Comité de proyecto (Soft Integration + Bienestar).  

### 5.2 Flujo de cambios
1. Stakeholder propone el cambio vía CR.  
2. Comité analiza impacto.  
3. Se decide y documenta la resolución.  
4. Se actualiza backlog, RTM y documentación.  
5. Se comunica a todos los interesados.  
