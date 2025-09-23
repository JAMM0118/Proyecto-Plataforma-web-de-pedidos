# Artefactos de requisitos – Módulo Login y Registro

## 1. Plan de gestión de requisitos

### 1.1 Técnicas de elicitation a utilizar

* **Entrevistas**: con estudiantes, restaurantes y cocineros para entender sus necesidades de autenticación y registro.
* **Cuestionarios**: para recopilar expectativas sobre facilidad de acceso y seguridad.
* **Talleres JAD**: con el equipo técnico y Bienestar Universitario para definir políticas de privacidad y validación de identidad.
* **Observación**: de procesos actuales de acceso a plataformas universitarias.
* **Prototipos**: pantallas de login, registro y recuperación de contraseña para validación temprana.

### 1.2 Responsables

* **Levantamiento de requisitos**: Analista de requisitos y Líder técnico.
* **Aprobación**: Gerente del proyecto + Representante de Bienestar Universitario.

### 1.3 Documentación

* Requisitos documentados en plantillas de RF y RNF.
* Historias de usuario en backlog ágil (Jira/Trello).
* RTM en hoja colaborativa (Google Sheets).

### 1.4 Priorización

* Método **MoSCoW** (MUST, SHOULD, COULD, WON’T).

### 1.5 Control de cambios

* Uso de un **formato CR** con: ID, descripción, justificación, impacto, decisión.
* Comité de requisitos evalúa impacto en tiempo, costo y calidad.
* Actualización de backlog, RTM y SRS cuando corresponda.

---

## 2. Catálogo de requisitos

### 2.1 Requisitos funcionales (RF)

| ID    | Nombre                              | Descripción                                                                      | Origen       | Prioridad | Criterios de aceptación (Gherkin)                                                                                                                                           |
| ----- | ----------------------------------- | -------------------------------------------------------------------------------- | ------------ | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RF-01 | Registro de estudiante              | El estudiante puede registrarse proporcionando nombre, correo, contraseña y rol. | Estudiantes  | MUST      | **Dado** que el usuario accede a la pantalla de registro, **cuando** completa los campos y confirma, **entonces** el sistema crea la cuenta y envía correo de verificación. |
| RF-02 | Registro de restaurante/cocinero    | El proveedor puede registrarse con datos básicos, documento y RUT.               | Restaurantes | MUST      | Dado que el proveedor completa el formulario, cuando confirma, entonces el sistema registra los datos y queda pendiente de validación.                                      |
| RF-03 | Login de usuarios                   | El usuario puede iniciar sesión con correo y contraseña.                         | Todos        | MUST      | Dado que el usuario ingresa credenciales válidas, cuando hace clic en "Ingresar", entonces el sistema lo autentica y redirige a la pantalla principal.                      |
| RF-04 | Recuperación de contraseña          | El usuario puede recuperar su contraseña mediante correo de restablecimiento.    | Todos        | MUST      | Dado que el usuario solicita recuperar, cuando ingresa correo registrado, entonces el sistema envía enlace de restablecimiento.                                             |
| RF-05 | Validación de correo                | El sistema envía correo de verificación tras el registro.                        | Todos        | SHOULD    | Dado que el usuario se registra, cuando abre su correo, entonces encuentra enlace de validación y activa su cuenta.                                                         |
| RF-06 | Edición de perfil                   | El usuario puede actualizar datos personales básicos.                            | Todos        | COULD     | Dado que el usuario inicia sesión, cuando accede a "Perfil" y edita datos, entonces el sistema actualiza la información.                                                    |
| RF-07 | Bloqueo tras intentos fallidos      | El sistema bloquea la cuenta tras 5 intentos fallidos.                           | Seguridad    | MUST      | Dado que el usuario falla 5 veces seguidas, cuando intenta ingresar de nuevo, entonces el sistema bloquea temporalmente el acceso.                                          |
| RF-08 | Inicio de sesión con redes sociales | El usuario puede autenticarse con Google o Facebook.                             | Estudiantes  | COULD     | Dado que el usuario selecciona "Ingresar con Google", cuando se autentica, entonces el sistema lo redirige como usuario válido.                                             |
| RF-09 | Cierre de sesión                    | El usuario puede cerrar su sesión de manera segura.                              | Todos        | MUST      | Dado que el usuario está logueado, cuando selecciona "Cerrar sesión", entonces el sistema finaliza la sesión y lo redirige al login.                                        |
| RF-10 | Notificación de registro            | El sistema notifica al usuario la creación exitosa de su cuenta.                 | Todos        | SHOULD    | Dado que el usuario completa el registro, cuando este es exitoso, entonces el sistema envía notificación al correo y muestra mensaje en pantalla.                           |

---

### 2.2 Requisitos no funcionales (RNF)

| ID     | Categoría        | Enunciado                                                                     | Métrica/Umbral          | Verificación                     | Prioridad |
| ------ | ---------------- | ----------------------------------------------------------------------------- | ----------------------- | -------------------------------- | --------- |
| RNF-01 | Rendimiento      | El login debe completarse en menos de 2 segundos en el 95% de los casos.      | ≤ 2s                    | Prueba de carga con 100 usuarios | MUST      |
| RNF-02 | Seguridad        | Las contraseñas deben almacenarse cifradas con bcrypt.                        | 100% cifrado            | Revisión técnica                 | MUST      |
| RNF-03 | Disponibilidad   | El módulo debe estar disponible el 99% del tiempo mensual.                    | ≥ 99% uptime            | Monitoreo SLA                    | MUST      |
| RNF-04 | Escalabilidad    | El sistema debe soportar 1000 registros diarios y crecer al doble en 6 meses. | ≥ 1000 registros/día    | Prueba de estrés                 | SHOULD    |
| RNF-05 | Usabilidad       | El proceso de registro debe realizarse en máximo 3 pasos.                     | ≤ 3 pasos               | Prueba con 10 usuarios           | SHOULD    |
| RNF-06 | Confidencialidad | Los datos personales deben transmitirse únicamente bajo TLS 1.3.              | 100% conexiones seguras | Auditoría técnica                | MUST      |

---

## 3. Prototipo de baja fidelidad

1. **Pantalla de Login**: campos de correo y contraseña, botones "Ingresar" y "Recuperar contraseña".
2. **Pantalla de Registro**: formulario con datos básicos, selección de rol (estudiante / restaurante / cocinero).
3. **Pantalla de Recuperación de contraseña**: campo de correo y botón "Enviar enlace".

*(Se pueden realizar en papel, Figma o Balsamiq.)*

---

## 4. Matriz de trazabilidad inicial (RTM)

| Req ID | Descripción           | Historia de usuario | Componente   | Caso de prueba | Estado    |
| ------ | --------------------- | ------------------- | ------------ | -------------- | --------- |
| RF-01  | Registro estudiante   | HU-01               | auth-svc     | TC-REG-01      | Pendiente |
| RF-03  | Login usuario         | HU-02               | auth-svc     | TC-LOGIN-01    | Pendiente |
| RF-04  | Recuperar contraseña  | HU-03               | auth-svc     | TC-REC-01      | Pendiente |
| RF-07  | Bloqueo tras intentos | HU-04               | security-svc | TC-SEC-01      | Pendiente |
| RNF-01 | Tiempo respuesta ≤ 2s | HU-02               | backend      | PERF-01        | Pendiente |
| RNF-02 | Cifrado contraseñas   | HU-01               | database     | SEC-02         | Pendiente |

---

## 5. Procedimiento de control de cambios

### 5.1 Formato CR (Change Request)

* **ID:** CR-##
* **Descripción del cambio:** (ej. añadir login con biometría)
* **Justificación:** necesidad del usuario, cumplimiento legal, etc.
* **Impacto:** alcance, tiempo, costo, calidad.
* **Recomendación técnica:** factibilidad del equipo.
* **Decisión:** Aprobado / Rechazado / Diferido.
* **Responsable:** Comité de proyecto.

### 5.2 Flujo de cambios

1. Stakeholder propone el cambio vía CR.
2. Comité analiza impacto.
3. Se decide y documenta la resolución.
4. Se actualiza backlog, RTM y documentación.
5. Se comunica a los interesados.
