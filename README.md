# 🎸 GuitarLA - Tienda de Guitarras

Aplicación web de comercio electrónico para la venta de guitarras. El proyecto fue desarrollado para practicar el manejo de estado global en React, custom hooks, y persistencia con `localStorage`.

🔗 **[Ver demo en vivo](https://tiendaguitarr.netlify.app)**

---

## ✨ Funcionalidades

- Catálogo de 12 guitarras con nombre, descripción y precio
- Carrito de compras con dropdown al hover
- Agregar productos al carrito (incrementa la cantidad si ya existe)
- Incrementar / decrementar / eliminar ítems individuales
- Vaciar el carrito completo
- Total calculado en tiempo real
- **Persistencia del carrito** — sobrevive recargas de página gracias a `localStorage`

---

## 🚀 Tecnologías

- [React 18](https://react.dev/)
- [Vite 5](https://vitejs.dev/)
- CSS personalizado con Bootstrap 5 embebido
- Google Fonts — [Outfit](https://fonts.google.com/specimen/Outfit)

---

## 🧠 Decisiones técnicas

**Custom hook `useCart`**  
Toda la lógica del carrito fue extraída a un hook personalizado para mantener `App.jsx` limpio y separar responsabilidades. El hook expone únicamente las funciones y el estado necesarios, sin acoplar la lógica al componente visual.

**`useMemo` para `isEmpy`**  
La verificación de carrito vacío está memoizada con `useMemo` para evitar que React recalcule ese valor en cada render cuando el carrito no ha cambiado.

**Inicialización lazy del estado**  
`useState(initialCart)` recibe una función en lugar de un valor directo, lo que hace que `localStorage` se lea solo una vez al montar el componente, y no en cada render.

**`useEffect` para sincronizar con `localStorage`**  
Cada vez que el array `car` cambia, un efecto serializa el estado y lo persiste. Esto desacopla la sincronización de la lógica de negocio.

---

## 📁 Estructura del proyecto

```
guitar02/
├── public/
│   └── img/              # Logo, carrito, header e imágenes de guitarras
├── src/
│   ├── components/
│   │   ├── Guitar.jsx    # Tarjeta de producto individual
│   │   └── Header.jsx    # Encabezado con carrito desplegable
│   ├── data/
│   │   └── db.js         # Catálogo de 12 guitarras (datos estáticos)
│   ├── hooks/
│   │   └── useCart.js    # Custom hook con toda la lógica del carrito
│   ├── App.jsx
│   ├── index.css         # Estilos globales + Bootstrap embebido
│   └── main.jsx
├── index.html
├── vite.config.js
└── package.json
```

---

## ⚙️ Instalación y uso

```bash
git clone https://github.com/tu-usuario/Tienda-de-Guitarras.git
cd guitar02
npm install
npm run dev
```

---

## 📝 Scripts disponibles

| Script | Descripción |
|---|---|
| `npm run dev` | Inicia Vite en modo desarrollo con HMR |
| `npm run build` | Genera el build de producción en `/dist` |
| `npm run preview` | Sirve el build localmente para revisión |
| `npm run lint` | Ejecuta ESLint sobre todo el proyecto |
