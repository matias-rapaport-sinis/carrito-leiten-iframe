# carrito-leiten-iframe

Carrito de compras embebible en iframe para el ERP Leiten.

## Deploy

Producción: https://hikoki-ver-carrito-leiten.vercel.app

## Comunicación cross-origin (postMessage)

### Padre → Iframe

```js
// Enviar cart token
iframe.contentWindow.postMessage({ type: 'SET_TOKEN', token: '<cartToken>' }, '*')

// Enviar sesión después del login
iframe.contentWindow.postMessage({ type: 'SET_SESSION', idSesion: '<idSesion>' }, '*')
```

### Iframe → Padre

```js
// Click en "Ir a pagar"
{ type: 'GO_CHECKOUT', idSesion: '<idSesion>', cartToken: '<cartToken>' }
```

## API utilizada

- `GET /api/carrito` — obtener carrito
- `PUT /api/carrito/items/{idItem}` — actualizar cantidad `{ cantidad: N }`
- `DELETE /api/carrito/items/{idItem}` — eliminar línea
