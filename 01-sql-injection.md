# SQL Injection — Bypass de autenticación

**Categoría OWASP:** A03:2021 — Injection
**Severidad:** Crítica

## Pasos realizados

1. Con Burp Suite interceptando el tráfico, se envió una petición de login al endpoint
   de autenticación de Juice Shop.
2. Se interceptó la petición en **Burp Proxy** y se envió a **Repeater**.
3. En el campo de email se inyectó el siguiente payload:

4. El payload altera la consulta SQL del servidor, convirtiéndola en una condición
   siempre verdadera, lo que permite autenticar sin conocer la contraseña real.
5. Resultado: inicio de sesión exitoso sin credenciales válidas (login como el
   primer usuario registrado en la base de datos).

## Evidencia

![SQL Injection en Burp Repeater](screenshots/sqli-repeater.png)

## Impacto

Un atacante puede eludir completamente el mecanismo de autenticación y acceder
a cuentas de usuario sin conocer sus credenciales.

## Remediación

- Usar consultas parametrizadas (prepared statements) en lugar de concatenar
  el input del usuario directamente en la consulta SQL.
- Validar y sanitizar toda entrada del usuario en el backend.
- Aplicar el principio de mínimo privilegio en la cuenta de base de datos usada
  por la aplicación.
