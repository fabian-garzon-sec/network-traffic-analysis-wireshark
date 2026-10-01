Markdown
# Cybersecurity & Web Application Hacking Labs 

Este repositorio contiene la documentación técnica, capturas y evidencias de laboratorios prácticos orientados a la ciberseguridad ofensiva, pruebas de penetración (*pentesting*) y análisis de vulnerabilidades en aplicaciones web y entornos de red controlados.

## Objetivos del Proyecto
* **Identificación y Explotación de Vulnerabilidades Web:** Demostrar el funcionamiento de fallos de seguridad comunes como Inyecciones SQL (SQLi), Cross-Site Scripting (XSS) y fallos en bibliotecas criptográficas (Heartbleed).
* **Uso de Herramientas Estándar de la Industria:** Documentar el flujo de trabajo práctico utilizando suites de seguridad en entornos Kali Linux.
* **Prácticas en Entornos Controlados:** Aplicar conceptos sobre máquinas vulnerables locales (*bWAPP*, *bee-box*) garantizando la seguridad del entorno.

---

## Herramientas Utilizadas

| Herramienta | Categoría | Uso en los Laboratorios |
| :--- | :--- | :--- |
| **Nmap** | Reconocimiento / Escaneo | Descubrimiento de puertos y análisis de vulnerabilidades con scripts NSE (`ssl-heartbleed`). |
| **Metasploit Framework** | Explotación / Auditoría | Escaneo y verificación de la vulnerabilidad OpenSSL Heartbleed en servicios HTTPS/TLS. |
| **SQLmap** | Explotación de BD | Automatización de la detección e inyección SQL sobre parámetros vulnerables. |
| **BeEF (Browser Exploitation Framework)** | Hacking Ético / Web | Evaluación de vectores de ataque basados en navegador mediante XSS. |
| **bWAPP / bee-box** | Entorno de Pruebas | Aplicación web deliberadamente vulnerable basada en PHP/MySQL para la ejecución de pruebas. |

---

## Laboratorios Destacados

### 1. Auditoría de SSL/TLS (OpenSSL Heartbleed - CVE-2014-0160)
* **Reconocimiento:** Uso de Nmap NSE para identificar bibliotecas SSL vulnerables en el puerto objetivo (`8443`).
* **Análisis y Verificación:** Ejecución de módulos auxiliares en Metasploit (`scanner/ssl/openssl_heartbleed`) sobre `192.168.20.8` para validar la fuga de memoria del servidor en tiempo real.

### 2. Inyección SQL Automatizada (SQLi)
* Pruebas de extracción de datos con `sqlmap` sobre endpoints locales (`192.168.56.101`), identificando puntos de entrada vulnerables a SQLi en la aplicación objetivo.

### 3. Explotación Web y Hooking de Navegadores (BeEF & XSS)
* Configuración del servicio BeEF para interactuar con sesiones web vulnerables mediante la ejecución de scripts en cliente (XSS).

---

## Descargo de Responsabilidad (Disclaimer)
Todo el contenido, comandos y evidencias presentadas en este repositorio fueron ejecutados dentro de un **entorno de laboratorio local estrictamente controlado y aislado** (redes de prueba `192.168.x.x` / `127.0.0.1`). Este material se publica únicamente con fines educativos, de aprendizaje y de investigación profesional en ciberseguridad.

---
**Autor:** Fabian Garzon[cite: 158, 159, 160, 161]
