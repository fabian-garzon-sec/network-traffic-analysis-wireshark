# soc-labs-and-security-analysis
Markdown
Markdown
# SOC & Security Analysis Labs (Wireshark & OWASP Top 10)

Este repositorio contiene la documentación técnica de laboratorios prácticos orientados a análisis de tráfico de red, monitoreo de seguridad y evaluación de vulnerabilidades web clave alineadas con el estándar **OWASP Top 10**.

---

## Herramientas y Entornos
* **Análisis de Red:** Wireshark v4.x, CLI (`ping`, `nslookup`, `ipconfig`)
* **Seguridad Web:** Burp Suite, DVWA / Juiceshop / PortSwigger Web Security Academy
* **Sistemas:** Linux (Kali/Ubuntu), Windows 11

---

## Módulo 1: Análisis de Tráfico de Red (Wireshark)

### 1.1 Resolución de Nombres (DNS)
* **Filtro utilizado:** `dns`
* **Análisis:** Inspección de peticiones `Standard Query (A Record)` enviadas vía UDP/53. Verificación de tiempos de respuesta del servidor y mapeo correcto IP-Dominio.

### 1.2 Inspección de Sesiones TCP (Three-Way Handshake)
* **Filtro utilizado:** `tcp.flags.syn == 1 || (tcp.flags.syn == 1 && tcp.flags.ack == 1)`
* **Análisis del Flujo:**
  1. `[SYN]` Cliente $\rightarrow$ Servidor (Inicio de sincronización).
  2. `[SYN, ACK]` Servidor $\rightarrow$ Cliente (Confirmación y respuesta).
  3. `[ACK]` Cliente $\rightarrow$ Servidor (Conexión establecida).

---

## Módulo 2: Vulnerabilidades Web & OWASP Top 10

### 2.1 A03:2021 – Injection (SQL Injection - SQLi)
* **Descripción:** Identificación de puntos de entrada en formularios sin sanitizar que permiten la ejecución de consultas SQL no autorizadas.
* **Prueba de Concepto (PoC):** Inyección de payload básico `' OR '1'='1` para la evasión de autenticación en entornos de prueba controlados.
* **Mitigación:** Uso de consultas preparadas (Prepared Statements) y parametrización de entradas.

### 2.2 A01:2021 – Broken Access Control (Control de Acceso Roto)
* **Descripción:** Validación de fallas donde los usuarios pueden actuar fuera de sus permisos previstos (IDOR - Insecure Direct Object References).
* **Prueba de Concepto (PoC):** Modificación de parámetros de ID de usuario en la URL/petición (`/user?id=101` $\rightarrow$ `/user?id=102`) mediante interceptación de tráfico con Burp Suite.
* **Mitigación:** Implementación de controles de autorización basados en roles (RBAC) a nivel de servidor.

---

## Conclusiones y Aplicabilidad en SOC (Tier 1)
* **Triage de Alertas:** Capacidad para diferenciar tráfico legítimo de posibles escaneos o intentos de explotación mediante lectura directa de registros y capturas de paquetes.
* **Respuesta a Incidentes:** Comprensión clara de los vectores de ataque web comunes para realizar correlación de eventos en un SIEM o análisis de logs del servidor web.
