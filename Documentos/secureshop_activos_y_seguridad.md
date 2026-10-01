# Análisis de Activos de SecureShop - Actividad 1

## Integrantes
- Steven Egas
- Pablo Domínguez
- Juan Quimbiulco

## Identificación de Activos

- Datos de usuarios
- Credenciales
- Catálogo de productos
- Microservicio de Pedidos
- API Gateway
- Servicio de Pago
- Bases de Datos
- Logs de Auditoría
- Microservicio de Usuarios
- Claves de Cifrado


## Identificación y Clasificación de Activos

| Activo | Tipo | Consecuencia |
| :--- | :--- | :--- |
| **1. Datos de usuarios** | Información | **Acceso:** Violación de privacidad y demandas.<br>**Modificación:** Corrupción de perfiles.<br>**Indisponibilidad:** Bloqueo de cuentas. |
| **2. Credenciales** | Datos | **Acceso:** Toma de control de cuentas.<br>**Modificación:** Escalamiento de privilegios.<br>**Indisponibilidad:** Paralización del sistema. |
| **3. Catálogo de productos** | Información | **Acceso:** Exposición comercial.<br>**Modificación:** Pérdidas por alteración de precios.<br>**Indisponibilidad:** Detención de ventas. |
| **4. Microservicio de Pedidos** | Software | **Acceso:** Fraude en transacciones.<br>**Modificación:** Inyección de código malicioso.<br>**Indisponibilidad:** Imposibilidad de comprar. |
| **5. API Gateway** | Infraestructura | **Acceso:** Exposición de rutas internas.<br>**Modificación:** Redirección de tráfico.<br>**Indisponibilidad:** Interrupción total externa. |
| **6. Servicio de Pago** | Servicio | **Acceso:** Robo de datos financieros.<br>**Modificación:** Alteración de montos.<br>**Indisponibilidad:** Suspensión de cobros. |
| **7. Bases de Datos** | Infraestructura | **Acceso:** Extracción masiva de datos.<br>**Modificación:** Borrado o corrupción de registros.<br>**Indisponibilidad:** Colapso de microservicios. |
| **8. Logs de Auditoría** | Información | **Acceso:** Revelación de fallas internas.<br>**Modificación:** Ocultamiento de ataques.<br>**Indisponibilidad:** Ceguera ante incidentes. |
| **9. Microservicio de Usuarios** | Software | **Acceso:** Comprensión de autenticación.<br>**Modificación:** Inserción de puertas traseras.<br>**Indisponibilidad:** Suspensión de registros. |
| **10. Claves de Cifrado** | Datos | **Acceso:** Descifrado de comunicaciones.<br>**Modificación:** Ruptura de confianza criptográfica.<br>**Indisponibilidad:** Caída de canales seguros. || **11. Microservicio de Inventario** | Software | **Acceso:** Exposición de niveles de stock y proveedores.<br>**Modificación:** Ventas de productos inexistentes o stock falso.<br>**Indisponibilidad:** Imposibilidad de validar disponibilidad y procesar pedidos. |
| **12. Panel de Administración** | Software | **Acceso:** Control total de la tienda por un atacante.<br>**Modificación:** Cambio de configuraciones, roles y precios.<br>**Indisponibilidad:** Imposibilidad de gestionar la operación. |
| **13. Tokens de Sesión** | Datos | **Acceso:** Suplantación de identidad de usuarios activos.<br>**Modificación:** Escalamiento de privilegios mediante tokens alterados.<br>**Indisponibilidad:** Cierre masivo de sesiones y pérdida de compras en curso. |
| **14. Copias de Seguridad (Backups)** | Información | **Acceso:** Fuga de toda la información histórica.<br>**Modificación:** Restauración de datos corruptos o maliciosos.<br>**Indisponibilidad:** Imposibilidad de recuperarse ante un desastre. |
| **15. Servicio de Notificaciones** | Servicio | **Acceso:** Exposición de correos, teléfonos y contenido de mensajes.<br>**Modificación:** Envío de mensajes fraudulentos (phishing) a nombre de SecureShop.<br>**Indisponibilidad:** Usuarios sin confirmaciones ni alertas de seguridad. |


## 2. Identificación de Amenazas y Mecanismos de Mitigación

| Activo | Amenazas (3) | Mecanismo de Mitigación |
| :--- | :--- | :--- |
| **1. Datos de usuarios** | **1.** Fuga de datos<br>**2.** Acceso interno no autorizado<br>**3.** Ransomware | **1.** Enmascaramiento y cifrado en reposo<br>**2.** Principio de privilegios mínimos y control de accesos basados en roles<br>**3.** Respaldos inmutables y políticas estrictas de respaldo |
| **2. Credenciales** | **1.** Fuerza bruta / credential stuffing<br>**2.** Phishing<br>**3.** Almacenamiento inseguro | **1.** Limitación de intentos de inicio de sesión y uso de CAPTCHA<br>**2.** Implementación de autenticación multifactor (MFA)<br>**3.** Uso de funciones hash robustas con sal (Argon2 o bcrypt) |
| **3. Catálogo de productos** | **1.** Manipulación de precios<br>**2.** Web scraping masivo<br>**3.** Denegación de servicio (DoS) | **1.** Validación estricta de esquemas y control de autorización en el backend<br>**2.** Uso de firewalls de aplicaciones web (WAF) y limitación de tasa (rate limiting)<br>**3.** Escalado automático y balanceo de carga |
| **4. Microservicio de Pedidos** | **1.** Inyección SQL o NoSQL<br>**2.** IDOR (Referencias directas a objetos inseguras)<br>**3.** Repudio de transacciones | **1.** Uso de consultas parametrizadas y ORM seguros<br>**2.** Validación de propiedad del recurso en cada solicitud<br>**3.** Registro de auditoría con firma digital y no repudio |
| **5. API Gateway** | **1.** Ataques DDoS<br>**2.** Mala configuración de rutas y CORS<br>**3.** Interceptación Man-in-the-Middle | **1.** Protección contra DDoS en la capa de borde (Cloudflare/WAF)<br>**2.** Políticas estrictas de CORS y cierre de rutas de prueba o internas<br>**3.** Uso obligatorio de HTTPS/TLS en todas las comunicaciones |
| **6. Servicio de Pago** | **1.** Fraude con tarjetas robadas<br>**2.** Manipulación de montos o callbacks<br>**3.** Interceptación de datos financieros | **1.** Integración con pasarelas certificadas PCI-DSS<br>**2.** Validación de firmas criptográficas en las respuestas de pago<br>**3.** Tokenización de tarjetas y prohibición de almacenar PAN en texto plano |
| **7. Bases de Datos** | **1.** Inyección SQL<br>**2.** Exposición pública o claves por defecto<br>**3.** Borrado o corrupción de datos | **1.** Uso de ORM y separación estricta de capas de datos<br>**2.** Restricción de acceso en redes privadas sin salida directa a internet<br>**3.** Bitácoras de transacciones y respaldos automatizados frecuentes |
| **8. Logs de Auditoría** | **1.** Alteración o borrado de logs<br>**2.** Datos sensibles en registros<br>**3.** Saturación del almacenamiento | **1.** Envío centralizado de logs a un servidor WORM (Write Once, Read Many)<br>**2.** Enmascaramiento automático de datos personales y credenciales antes de registrar<br>**3.** Políticas de retención y rotación automática de almacenamiento |
| **9. Microservicio de Usuarios** | **1.** Autenticación rota<br>**2.** Enumeración de usuarios<br>**3.** Mass assignment | **1.** Uso de estándares robustos como OAuth2 y OpenID Connect<br>**2.** Respuestas de error genéricas en el inicio de sesión<br>**3.** Delimitación explícita de campos permitidos en las solicitudes DTO |
| **10. Claves de Cifrado** | **1.** Exposición en repositorios de código<br>**2.** Robo desde servidor comprometido<br>**3.** Falta de rotación de claves | **1.** Uso de gestores de secretos dedicados (Vault) y escaneo de código<br>**2.** Aislamiento de componentes y principio de menor privilegio en servidores<br>**3.** Establecer políticas automáticas de rotación periódica |
| **11. Microservicio de Inventario** | **1.** Manipulación de stock<br>**2.** Condiciones de carrera<br>**3.** Dependencias vulnerables | **1.** Validación de transacciones atómicas en base de datos<br>**2.** Uso de bloqueos optimistas o pesimistas para concurrencia<br>**3.** Análisis automatizado de dependencias y actualización continua |
| **12. Panel de Administración** | **1.** Acceso no autorizado por credenciales débiles<br>**2.** Ataques XSS / CSRF<br>**3.** Abuso de privilegios internos | **1.** Forzar contraseñas robustas y autenticación multifactor obligatoria (MFA)<br>**2.** Sanitización de salidas y uso de tokens anti-CSRF<br>**3.** Segmentación de red y registro detallado de acciones administrativas |
| **13. Tokens de Sesión** | **1.** Robo de token por XSS<br>**2.** Ataques de repetición (replay)<br>**3.** Tokens sin expiración o firma débil | **1.** Almacenamiento seguro de tokens en cookies HttpOnly y Secure<br>**2.** Implementación de caducidad corta y rotación de tokens<br>**3.** Uso de algoritmos de firma robustos como RS256 o HS256 con claves seguras |
| **14. Copias de Seguridad** | **1.** Robo de respaldos almacenados<br>**2.** Ransomware sobre respaldos<br>**3.** Respaldos corruptos o incompletos | **1.** Cifrado robusto de todas las copias de seguridad en reposo<br>**2.** Almacenamiento desconectado o respaldos inmutables aislados<br>**3.** Pruebas periódicas y automatizadas de restauración |
| **15. Servicio de Notificaciones**| **1.** Spoofing del remitente<br>**2.** Inyección en plantillas de correo<br>**3.** Abuso como relé de spam | **1.** Configuración estricta de registros SPF, DKIM y DMARC<br>**2.** Validación y escape de variables dinámicas en las plantillas<br>**3.** Limitación de tasa (rate limiting) de envío por usuario o IP |
