# OWASP Juice Shop — Pentesting Practice (OWASP Top 10)

Práctica de seguridad web usando [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/),
una aplicación intencionalmente vulnerable diseñada por OWASP para entrenamiento.
Entorno 100% local y legal — sin impacto a sistemas de terceros.

## Entorno

- **Target:** OWASP Juice Shop (Docker)
- **Proxy / herramienta de análisis:** Burp Suite Community
- **SO:** Kali Linux (máquina virtual)
- **Metodología:** OWASP Top 10 (2021)

## Despliegue

1. Instalación de Docker en Kali:
   ```bash

   ```

2. Despliegue de Juice Shop en un contenedor local:
   ```bash
  
   ```
   La aplicación queda disponible en `http://localhost:3000`.

3. Configuración de Burp Suite como proxy interceptor:
   - Burp → pestaña **Proxy** → listener activo en `127.0.0.1:8080`.
   - Firefox configurado con proxy manual `127.0.0.1:8080` (HTTP/HTTPS).
   - Certificado CA de Burp importado en Firefox para interceptar tráfico HTTPS sin advertencias.

4. Verificación: tráfico de `localhost:3000` visible en Burp → Proxy → HTTP history.

## Resumen de hallazgos

| # | Categoría OWASP | Vulnerabilidad | Severidad |
|---|---|---|---|
| 1 | A03:2021 — Injection | SQL Injection (bypass de login) | Crítica |
| 2 | A01:2021 — Broken Access Control | IDOR en pedidos de usuario | Alta |
| 3 | A03:2021 — Injection | Cross-Site Scripting (XSS) | Media |

Detalle de cada uno en los archivos individuales.

## Disclaimer

Todas las pruebas se realizaron contra una instancia local de OWASP Juice Shop,
una aplicación creada específicamente para práctica de seguridad. Ninguna prueba
se realizó contra sistemas de producción ni de terceros sin autorización.
