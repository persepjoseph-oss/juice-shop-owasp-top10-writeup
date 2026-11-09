# IDOR — Acceso no autorizado a pedidos de otro usuario

**Categoría OWASP:** A01:2021 — Broken Access Control
**Severidad:** Alta

## Pasos realizados

1. Se inició sesión con una cuenta de usuario normal.
2. Se accedió a la sección de "Mis pedidos" y se interceptó la petición con Burp Proxy.
3. La petición incluía un identificador numérico del recurso (por ejemplo,
   `/rest/order/<id>`).
4. Se modificó ese ID en **Burp Repeater** por el de otro recurso no asignado
   al usuario autenticado.
5. El servidor respondió con los datos del pedido de otro usuario, sin validar
   que perteneciera a la sesión actual.

## Evidencia

![IDOR en Burp Repeater](screenshots/idor-repeater.png)

## Impacto

Exposición de datos privados de otros usuarios (detalles de compra, dirección,
productos) por una falla de validación de autorización a nivel de objeto.

## Remediación

- Verificar en el backend, en cada petición, que el recurso solicitado pertenezca
  al usuario autenticado (no solo validar que esté logueado).
- Usar identificadores no predecibles (UUID) en lugar de IDs secuenciales,
  como capa adicional de defensa.
