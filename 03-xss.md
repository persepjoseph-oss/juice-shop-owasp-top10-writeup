# Cross-Site Scripting (XSS)

**Categoría OWASP:** A03:2021 — Injection
**Severidad:** Media

## Pasos realizados

1. Se identificó un campo de entrada del sitio sin sanitización adecuada.
2. Se inyectó un payload de prueba tipo:
   ```html
   <script>alert('XSS')</script>
   ```
3. Al cargar/enviar el contenido, el navegador ejecutó el script inyectado,
   mostrando una ventana emergente con el contenido definido.

## Evidencia

![XSS ejecutado en el navegador](screenshots/xss-alert.png)

## Impacto

Un atacante podría inyectar JavaScript malicioso para robar cookies de sesión,
redirigir usuarios a sitios falsos o modificar el contenido visible de la página.
[Completar: indicar si fue reflejado (solo en esa petición) o almacenado
(persiste en la base de datos y afecta a otros usuarios)].

## Remediación

- Escapar/codificar correctamente todo output que incluya input del usuario
  antes de renderizarlo en HTML.
- Implementar una Content Security Policy (CSP) como capa adicional de defensa.
- Validar y sanitizar la entrada en el backend, no solo en el frontend.
