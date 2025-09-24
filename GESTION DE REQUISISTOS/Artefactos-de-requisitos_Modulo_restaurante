# Artefactos de requisitos - Módulo Restaurantes / Cocineros

## 1. Plan de gestión de requisitos

### 1.1 Técnicas de elicitation a utilizar
- **Entrevistas:** propietarios de restaurantes, cocineros independientes y administradores de menús.  
- **Grupos focales:** estudiantes y usuarios para validar expectativas sobre variedad y calidad de menús.  
- **Talleres JAD:** Soft Integration + Bienestar Universitario para definir reglas de negocio (menús subsidiados, convenios de afiliación).  
- **Observación:** prácticas actuales de gestión de menús en restaurantes locales.  
- **Prototipos:** pantallas de “Gestión de menús” y “Afiliación de restaurantes” para validación temprana.  

### 1.2 Responsables
- **Levantamiento de requisitos:** Analista de requisitos y líder técnico de Soft Integration.  
- **Aprobación:** Gerente del proyecto (Soft Integration) + Representante de Bienestar Universitario.  

### 1.3 Documentación
- Requisitos registrados en plantillas RF y RNF.  
- Historias de usuario documentadas en backlog ágil (Jira/Trello).  
- RTM mantenida en hoja colaborativa (Google Sheets).  

### 1.4 Priorización
- Método **MoSCoW**: MUST (imprescindible), SHOULD (importante), COULD (deseable), WON’T (fuera de alcance inmediato).  

### 1.5 Control de cambios
- Uso de un formato CR (Change Request) con: ID, descripción, justificación, impacto, decisión.  
- Comité de requisitos analiza impacto en tiempo, costo y calidad.  
- Actualización de backlog, RTM y SRS cuando aplique.  

---

## 2. Catálogo de requisitos

### 2.1 Requisitos funcionales (RF)

| ID     | Nombre                          | Descripción                                                                 | Origen            | Prioridad | Criterios de aceptación |
|--------|---------------------------------|-----------------------------------------------------------------------------|-------------------|-----------|-------------------------|
| RF-01  | Registrar restaurante afiliado  | El administrador puede registrar un nuevo restaurante con datos básicos.    | Admin / Cocineros | MUST      | Dado que el admin abre el formulario, cuando completa los datos, entonces el sistema guarda el restaurante. |
| RF-02  | Gestionar menú                  | El restaurante/cocinero puede crear, editar y eliminar platos de su menú.   | Cocineros         | MUST      | Dado que el cocinero accede a su panel, cuando gestiona platos, entonces el sistema actualiza el menú visible a estudiantes. |
| RF-03  | Definir disponibilidad de platos| El cocinero puede habilitar o deshabilitar platos según stock o día.        | Cocineros         | SHOULD    | Dado que el cocinero edita disponibilidad, cuando actualiza, entonces el sistema refleja el cambio en el catálogo de estudiantes. |
| RF-04  | Gestionar convenios             | El administrador puede asociar restaurantes a convenios o subsidios.        | Admin             | SHOULD    | Dado que el admin selecciona un restaurante, cuando aplica un convenio, entonces el sistema registra el beneficio asociado. |
| RF-05  | Consultar estadísticas de ventas| El cocinero/restaurante puede consultar reportes de ventas y reseñas.       | Cocineros         | COULD     | Dado que el proveedor accede a estadísticas, cuando consulta, entonces el sistema muestra ventas y calificaciones. |

### 2.2 Requisitos no funcionales (RNF)

| ID     | Categoría       | Enunciado                                                             | Métrica/Umbral  | Verificación             | Prioridad |
|--------|----------------|-----------------------------------------------------------------------|----------------|--------------------------|-----------|
| RNF-01 | Rendimiento    | El sistema debe mostrar el menú en menos de 3 segundos.                | ≤ 3s           | Prueba de carga con 100 usuarios | MUST |
| RNF-02 | Disponibilidad | El módulo de restaurantes debe estar disponible el 99% del tiempo.     | ≥ 99% uptime   | Monitoreo SLA            | MUST |
| RNF-03 | Seguridad      | Los datos de restaurantes y menús deben almacenarse cifrados.          | 100% cifrado   | Auditoría de seguridad   | MUST |
| RNF-04 | Escalabilidad  | El sistema debe soportar 200 restaurantes en la fase inicial.          | ≥ 200          | Prueba de estrés         | SHOULD |
| RNF-05 | Usabilidad     | Un cocinero debe poder registrar un plato en máximo 4 pasos.           | ≤ 4 pasos      | Prueba de usabilidad con 10 usuarios | SHOULD |

---

## 3. Prototipo de baja fidelidad
1. Pantalla **Gestión de menús**: lista de platos con opciones de agregar, editar o eliminar.  
2. Pantalla **Afiliación de restaurantes**: formulario para registrar datos del restaurante.  
3. Pantalla **Reportes de ventas**: gráficos con ventas por día y calificaciones promedio.  

*(Faltan imágenes del prototipo)*

---

## 4. Matriz de trazabilidad inicial (RTM)

| Req ID | Descripción                     | Historia de usuario | Componente         | Caso de prueba | Estado    |
|--------|---------------------------------|---------------------|-------------------|----------------|-----------|
| RF-01  | Registrar restaurante afiliado  | HU-01               | admin-svc         | TC-REST-01     | Pendiente |
| RF-02  | Gestionar menú                  | HU-02               | menu-svc          | TC-MENU-01     | Pendiente |
| RF-03  | Definir disponibilidad de platos| HU-03               | menu-svc          | TC-MENU-02     | Pendiente |
| RF-05  | Consultar estadísticas de ventas| HU-04               | reportes-svc      | TC-REP-01      | Pendiente |
| RNF-01 | Tiempo de respuesta ≤ 3s        | HU-02               | backend           | PERF-01        | Pendiente |

---

## 5. Procedimiento de control de cambios

### 5.1 Formato CR (Change Request)
- **ID:** CR-##  
- **Descripción del cambio:** (ej. añadir filtro de menús por alérgenos)  
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
