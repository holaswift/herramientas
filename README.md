<p align="center">
  <picture>
    <img src="redes/assets/logo/hola-swift-horizontal-color.webp" alt="hola Swift" width="260">
  </picture>
</p>

<p align="center"><b>Herramientas para el equipo de hola Swift.</b><br>
<a href="https://holaswift.com/herramientas/">holaswift.com/herramientas</a></p>

---

Todo lo que necesitáis para firmar, publicar y presentar con la marca, sin instalar nada: se abre en el navegador.

- **[Firma de email](https://holaswift.com/herramientas/firmas/)**: rellenad vuestros datos, copiad la firma y pegadla en Gmail, Apple Mail u Outlook.
- **[Imágenes para redes](https://holaswift.com/herramientas/redes/)**: anuncios de charlas, quedadas y avisos con la marca, listos para descargar en cada formato.
- **[Kit de Discord](https://holaswift.com/herramientas/descargas/holaswift-discord.zip)**: iconos del servidor, banner, emojis y stickers, también animados.
- **[Kit de perfiles en redes](https://holaswift.com/herramientas/descargas/holaswift-redes.zip)**: fotos de perfil, cabeceras, destacados y bios para cada red.
- **[Presentaciones](https://holaswift.com/presentaciones/)**: la skill de Claude para hacer diapositivas, las fuentes y la plantilla para ponentes.
- **[Logos, vídeos y fotos](https://holaswift.com/prensa/#recursos)**: el mismo kit que usa la prensa.

**Estas páginas no salen en buscadores.** Compartid el enlace solo con quien colabore con hola Swift. Si algo no funciona o falta
material, avisad en el canal del equipo en Discord.

## Para quien mantiene esto

| Ruta | Qué es |
|---|---|
| `index.html` | La página de inicio de las herramientas |
| `firmas/` | El generador de firmas. `hola-swift-firma.png` es el logo que cargan las firmas desde los correos: **no lo mováis ni lo renombréis**, o las firmas ya enviadas lo perderán |
| `redes/` | El generador de imágenes para redes. Funciona en el navegador, sin servidor. `assets/` tiene las fuentes, los logos, el tubo y las pegatinas |
| `descargas/` | Los ZIP de Discord y de perfiles. Llegan solos desde el repositorio privado `marca` |

**Publicación:** GitHub Pages desde la rama `main` (Settings › Pages › Deploy from a branch › `main` / root). Como la web
principal usa el dominio `holaswift.com`, este repositorio se ve en `holaswift.com/herramientas/`.

**Fuera de buscadores y de modelos de lenguaje:**
- Cada página lleva `<meta name="robots" content="noindex, nofollow, …">`.
- El bloqueo de rastreadores (`Disallow: /herramientas/`) está en el `robots.txt` del repositorio `holaswift.github.io`,
  porque los buscadores solo leen el de la raíz del dominio. Si se borra de ahí, deja de aplicarse.
- No añadáis estas páginas al `sitemap.xml` de la web.

Esto aparta a los buscadores y a los bots de IA que respetan las reglas, pero no es una contraseña: quien tenga el enlace puede
entrar, y el contenido del repositorio se ve en github.com. No pongáis aquí nada confidencial (lo privado va en `marca`).

**Los ZIP se actualizan solos.** Cuando cambia `discord/` o `redes/kit/` en `marca`, su Action `zip-herramientas.yml`
regenera los dos ZIP, pone su tamaño en los botones de `index.html` y hace un commit aquí como `github-actions[bot]`.
No los editéis a mano: el siguiente cambio en `marca` los sobrescribe. Si hiciera falta generarlos a mano, desde la carpeta
que contiene `marca` y `herramientas`:

    (cd marca && zip -qr -X ../herramientas/descargas/holaswift-discord.zip discord -x '*.DS_Store')
    (cd marca/redes && rm -f ../../herramientas/descargas/holaswift-redes.zip && zip -qr -X ../../herramientas/descargas/holaswift-redes.zip kit -x '*.DS_Store')
