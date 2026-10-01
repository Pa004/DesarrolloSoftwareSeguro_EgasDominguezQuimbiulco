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


## Identificación de Amenazas por Activo
 
| Activo | Amenazas (3) |
| :--- | :--- |
| **1. Datos de usuarios** | **1. Fuga de datos:** Exfiltración de información personal.<br>**2. Acceso interno no autorizado:** Permisos excesivos que permiten consultar datos sin necesidad.<br>**3. Ransomware:** Cifrado de los datos para exigir un rescate. |
| **2. Credenciales** | **1. Fuerza bruta / credential stuffing:** Pruebas masivas de contraseñas filtradas o débiles.<br>**2. Phishing:** Engaño para que el usuario entregue sus credenciales.<br>**3. Almacenamiento inseguro:** Contraseñas en texto plano o con hashing débil. |
| **3. Catálogo de productos** | **1. Manipulación de precios:** Cambios no autorizados mediante APIs sin control.<br>**2. Web scraping masivo:** Extracción automatizada del catálogo por la competencia.<br>**3. Denegación de servicio (DoS):** Saturación del servicio que sirve el catálogo. |
| **4. Microservicio de Pedidos** | **1. Inyección (SQL/NoSQL/comandos):** Entradas maliciosas que alteran la lógica o los datos.<br>**2. IDOR:** Acceso a pedidos ajenos cambiando identificadores.<br>**3. Repudio de transacciones:** El usuario niega un pedido por falta de trazabilidad. |
| **5. API Gateway** | **1. Ataques DDoS:** Saturación del punto de entrada.<br>**2. Mala configuración de rutas y CORS:** Exposición de endpoints internos.<br>**3. Man-in-the-Middle:** Interceptación del tráfico sin TLS adecuado. |
| **6. Servicio de Pago** | **1. Fraude con tarjetas:** Compras con datos de tarjetas robados.<br>**2. Manipulación de montos o callbacks:** Alteración de importes o falsas confirmaciones de pago.<br>**3. Interceptación de datos financieros:** Captura de datos de pago en tránsito o en logs. |
| **7. Bases de Datos** | **1. Inyección SQL:** Consultas maliciosas que extraen o modifican información.<br>**2. Exposición pública / credenciales por defecto:** Bases accesibles desde internet o con claves por defecto.<br>**3. Borrado o corrupción de datos:** Eliminación intencional o accidental de registros. |
| **8. Logs de Auditoría** | **1. Alteración o borrado de logs:** El atacante elimina sus huellas.<br>**2. Datos sensibles en logs:** Registro de contraseñas o tokens en texto claro.<br>**3. Saturación del almacenamiento:** Exceso de eventos que detiene el registro. |
| **9. Microservicio de Usuarios** | **1. Autenticación rota:** Fallas en el login que permiten saltarse la verificación.<br>**2. Enumeración de usuarios:** Respuestas que revelan qué cuentas existen.<br>**3. Mass assignment:** Envío de campos extra (ej. role=admin) para escalar privilegios. |
| **10. Claves de Cifrado** | **1. Exposición en código o repositorios:** Claves incluidas en commits o variables de entorno.<br>**2. Robo desde servidor comprometido:** Extracción de claves tras acceder al servidor.<br>**3. Falta de rotación:** Claves antiguas o débiles que nunca se renuevan. |
| **11. Microservicio de Inventario** | **1. Manipulación de stock:** Cambios no autorizados que causan sobreventa o falsos agotados.<br>**2. Condiciones de carrera:** Compras simultáneas que dejan el inventario inconsistente.<br>**3. Dependencias vulnerables:** Librerías desactualizadas explotables. |
| **12. Panel de Administración** | **1. Acceso no autorizado:** Contraseñas débiles o ausencia de MFA.<br>**2. XSS / CSRF:** Acciones administrativas ejecutadas con scripts o peticiones falsas.<br>**3. Abuso de privilegios:** Administradores que actúan indebidamente sin control. |
| **13. Tokens de Sesión** | **1. Robo de token:** Captura por XSS o sniffing para suplantar al usuario.<br>**2. Ataque de repetición (replay):** Reutilización de un token válido interceptado.<br>**3. Tokens sin expiración o firma débil:** Tokens eternos o falsificables. |
| **14. Copias de Seguridad** | **1. Robo de respaldos:** Acceso a backups sin cifrar.<br>**2. Ransomware sobre respaldos:** Cifrado o borrado de las copias.<br>**3. Respaldos corruptos o desactualizados:** Copias que fallan al restaurar. |
| **15. Servicio de Notificaciones** | **1. Spoofing del remitente:** Mensajes falsos que aparentan ser de SecureShop.<br>**2. Inyección en plantillas:** Inserción de enlaces maliciosos.<br>**3. Abuso como relé de spam:** Envío masivo de mensajes no autorizados. |
