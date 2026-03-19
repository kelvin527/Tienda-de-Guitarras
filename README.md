# 🎸 GuitarLA - Tienda de Guitarras

Aplicación web de comercio electrónico para la venta de guitarras, construida con **React + Vite**. Permite a los usuarios explorar el catálogo, agregar productos al carrito, y gestionar las cantidades, con persistencia en `localStorage`.

---

## 🚀 Tecnologías

- [React 18](https://react.dev/)
- [Vite 5](https://vitejs.dev/)
- CSS personalizado (Bootstrap 5 embebido en `index.css`)
- Google Fonts — [Outfit](https://fonts.google.com/specimen/Outfit)

---

## 📁 Estructura del proyecto

```
guitar02/
├── public/
│   └── img/              # Logo, imagen del carrito, header e imágenes de guitarras
├── src/
│   ├── components/
│   │   ├── Guitar.jsx    # Tarjeta de producto individual
│   │   └── Header.jsx    # Encabezado con carrito desplegable
│   ├── data/
│   │   └── db.js         # Catálogo de 12 guitarras (datos estáticos)
│   ├── hooks/
│   │   └── useCart.js    # Custom hook con toda la lógica del carrito
│   ├── App.jsx           # Componente raíz
│   ├── App.css           # Estilos adicionales de la app
│   ├── index.css         # Estilos globales + Bootstrap embebido
│   └── main.jsx          # Punto de entrada de React
├── index.html
├── vite.config.js
└── package.json
```

---

## ⚙️ Instalación y uso

```bash
# 1. Clonar el repositorio
git clone https://github.com/tu-usuario/Tienda-de-Guitarras.git
cd guitar02

# 2. Instalar dependencias
npm install

# 3. Iniciar servidor de desarrollo
npm run dev

# 4. Build para producción
npm run build

# 5. Previsualizar el build
npm run preview
```

---

## 🧩 Componentes

### `App.jsx`
Componente raíz. Consume el hook `useCart` y distribuye las funciones y el estado a `Header` y `Guitar`.

### `Header.jsx`
Muestra el logo y el carrito de compras. El carrito es un dropdown que aparece al hacer hover. Incluye:
- Tabla con los productos agregados (imagen, nombre, precio, cantidad)
- Botones para incrementar / decrementar / eliminar cada ítem
- Total a pagar calculado dinámicamente
- Botón para vaciar el carrito
- Mensaje de "carrito vacío" cuando no hay ítems

### `Guitar.jsx`
Tarjeta de producto que muestra imagen, nombre, descripción y precio. Incluye el botón **Agregar al Carrito** que llama a `addCart`.

---

## 🪝 Hook: `useCart`

Centraliza toda la lógica de estado del carrito en `src/hooks/useCart.js`.

| Función / Estado | Descripción |
|---|---|
| `data` | Catálogo completo de guitarras (de `db.js`) |
| `car` | Array de productos en el carrito |
| `addCart(guitar)` | Agrega un ítem o incrementa su cantidad si ya existe |
| `removeFromCart(id)` | Elimina un ítem del carrito por su `id` |
| `incrementCart(id)` | Incrementa en 1 la cantidad de un ítem |
| `decrementCart(id)` | Decrementa en 1 la cantidad (mínimo 0) |
| `clearCart()` | Vacía el carrito completamente |
| `carTotal()` | Retorna el total calculado (`quantity * price`) |
| `isEmpy` | `boolean` — `true` si el carrito está vacío (memoizado con `useMemo`) |

**Persistencia:** el carrito se guarda automáticamente en `localStorage` mediante un `useEffect` que se dispara cada vez que `car` cambia. Al cargar la app, el estado inicial se recupera desde `localStorage`.

---

## 📦 Datos del catálogo

El archivo `src/data/db.js` exporta un array de 12 guitarras con la siguiente estructura:

```js
{
  id: 1,
  name: 'Lukather',
  image: 'guitarra_01',   // resuelve a public/img/guitarra_01.jpg
  description: '...',
  price: 299
}
```

---

## 📝 Scripts disponibles

| Script | Descripción |
|---|---|
| `npm run dev` | Inicia Vite en modo desarrollo con HMR |
| `npm run build` | Genera el build de producción en `/dist` |
| `npm run preview` | Sirve el build localmente para revisión |
| `npm run lint` | Ejecuta ESLint sobre todo el proyecto |
