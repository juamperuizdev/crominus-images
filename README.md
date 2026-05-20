# 🧩 CROMINUS — Repositorio Oficial de Imágenes

Repositorio público que contiene los recursos gráficos utilizados en **CROMINUS**, el juego online de cromos y trading cards desarrollado por [Juampe Ruiz](https://www.juamperuiz.es).

Este repositorio sirve como **origen estático** para las imágenes de las colecciones, distribuidas mediante **GitHub Pages** en el dominio **https://images.crominus.es/** para garantizar velocidad, disponibilidad y una experiencia fluida para los jugadores.

---

## 🌟 Sobre CROMINUS

**CROMINUS** es un juego de navegador pensado para quienes disfrutan coleccionando, intercambiando y descubriendo nuevas temáticas. Aquí podrás reunir cromos, tarjetas y cartas de mundos muy distintos, desde videojuegos y música hasta cine, cultura y muchas otras colecciones que irán creciendo con el tiempo.

La idea es sencilla: juegas, consigues puntos llamados *Crominus* y los usas para obtener nuevos sobres de tus colecciones favoritas. Cuantos más explores, más opciones tendrás para ampliar tu álbum y avanzar dentro de la comunidad.

Al registrarte, obtendrás *2.500 crominus* para empezar a jugar. Podrás obtener más *Crominus* jugando a diario, aceptando intercambios y completando colecciones y retos.

**CROMINUS** está diseñado para ser fácil de entender, rápido de disfrutar y con un punto social que lo hace más vivo. No solo coleccionas: también puedes interactuar con otros jugadores, intercambiar, descubrir sorpresas y avanzar mediante medallas y retos que premian tu participación.

**¿Como funciona?**

Jugar a CROMINUS es muy simple. Entra en la plataforma, consigue puntos **CROMINUS** participando en el juego y canjéalos por sobres de las colecciones que más te gusten. Cada sobre puede acercarte a nuevas piezas, completar series o encontrar cartas que te falten para seguir avanzando.

Además, la experiencia no se limita a abrir sobres. **CROMINUS** incluye medallas, retos y sorpresas que añaden variedad y hacen que cada sesión tenga algo distinto. Así, coleccionar no es solo repetir una acción, sino progresar, descubrir y disfrutar del proceso.

**¿Qué hace especial a Crominus?**

**CROMINUS** mezcla colección, progreso y comunidad en una experiencia pensada para ser amena y adictiva. Puedes centrarte en tus temáticas favoritas, probar suerte con nuevos sobres o buscar intercambios con otros jugadores para completar tus colecciones más rápido.

El sistema está pensado para ofrecer una experiencia personalizada, de manera que cada jugador viva su propio recorrido dentro del juego. Eso hace que **CROMINUS** tenga vida propia: no todos coleccionan lo mismo, no todos avanzan igual y no todos descubren las mismas sorpresas.

**Comunidad y apoyo**

**CROMINUS** también quiere ser un punto de encuentro para coleccionistas. El intercambio entre jugadores forma parte de su esencia, porque completar una colección siempre es más divertido cuando hay comunidad detrás.

Si te gusta el proyecto, tu apoyo ayuda a que siga creciendo, a que lleguen nuevas colecciones, más funciones y más contenido para que la experiencia sea cada vez mejor. Aquí cada aportación cuenta, porque detrás hay trabajo real, desarrollo continuo y ganas de construir algo duradero.

**Otras características**

- Colecciones temáticas con cromos únicos  
- Un sistema de juego en constante evolución  
- Una experiencia visual cuidada al detalle  
- Un entorno pensado para disfrutar, coleccionar y completar

---

## 📁 Estructura del repositorio

Las imágenes están organizadas por colecciones:

```
crominus-images/
├── coleccion-001/
│     ├── referencia-001.webp
│     ├── referencia-002.webp
│     └── thumbs/
│           ├── referencia-001.webp
│           ├── referencia-002.webp
│           └── ...
├── coleccion-002/
│     ├── referencia-001.webp
│     └── thumbs/
│           ├── referencia-001.webp
│           └── ...
└── README.md
```

Cada carpeta representa una colección independiente. Los archivos siguen el formato `referencia-NNN.webp` donde `referencia` es el código interno de la colección y `NNN` es el número del cromo con padding de 3 dígitos.

---

## ⚡ Acceso vía GitHub Pages

Todas las imágenes se sirven directamente desde **https://images.crominus.es/** configurado mediante GitHub Pages con dominio personalizado.

### URLs de acceso

- **Imagen principal:** `https://images.crominus.es/collections/<collection-name>/<reference-NNN>.webp`
- **Thumbnail:** `https://images.crominus.es/collections/<collection-name>/thumbs/<reference-NNN>.webp`

### Ejemplo real

```
https://images.crominus.es/collections/pokemon-megaevolucion/cr-pk-mev-001.webp
https://images.crominus.es/collections/pokemon-megaevolucion/thumbs/cr-pk-mev-001.webp
```

## 🛠 Buenas prácticas para nuevas colecciones

- Utilizar formato **WebP** siempre que sea posible  
- Mantener nombres consistentes (`referencia-NNN.webp` con padding de 3 dígitos)  
- Evitar espacios y caracteres especiales  
- Subir imágenes optimizadas  
- Mantener una carpeta por colección
- Intentar mantener el mismo tamaño de imagen para todas las colecciones
- Generar thumbnails para cada imagen en subcarpeta `thumbs/`

## 🖼️ Tamaño de las imágenes

- Tamaño original estándar: 750x1050 px
- Tamaño colecciones Pokémon: 660x920 px
- Thumbnails: altura máxima 265px, ancho proporcional (aprox. 190px)
- Todas las imágenes mantienen su proporción original

---

## 🔗 Proyecto principal

El juego completo está disponible en:

👉 [crominus.es](https://www.crominus.es)

---

## 🧑‍💻 Autor

Proyecto creado y mantenido por [Juampe Ruiz](https://www.juamperuiz.es).  
Desarrollo backend, frontend, infraestructura y diseño visual.

---

## 📜 Licencia

Las imágenes contenidas en este repositorio están protegidas y no pueden ser reutilizadas fuera del proyecto **CROMINUS** sin permiso explícito del autor.
