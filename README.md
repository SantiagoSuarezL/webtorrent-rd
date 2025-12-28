<div align="center">

# 🌐 WebTorrent P2P Player

**Reproduce videos directamente desde torrents en tu navegador**

</div>

---

## ✨ Características

| Funcionalidad | Descripción |
|---------------|-------------|
| 🎥 **Streaming P2P** | Reproduce videos sin descargarlos completamente. |
| 🚀 **Sin Servidor** | Todo funciona directamente en el navegador. |
| 🔗 **Magnet Links** | Compatible con magnet URIs e info hashes. |
| 📡 **WebRTC** | Conexiones P2P usando WebTorrent y WebRTC. |

---

## 🔧 Prerrequisitos

- **Navegador moderno** con soporte para WebRTC (Chrome, Firefox, Edge)
- **Conexión a internet** activa

> **Nota:** No requiere instalación de software adicional.

---

## 📥 Instalación

### Opción 1: Uso directo

Simplemente abre el archivo `index.html` en tu navegador.

### Opción 2: Servidor local

```bash
# Usando Python
python -m http.server 8000

# O usando Node.js
npx http-server
```

Luego accede a `http://localhost:8000`

---

## 🚀 Uso

### 1. Obtener un Magnet Link

Necesitas un magnet link o info hash de un archivo de video torrent.

**Formato aceptado:**
```
magnet:?xt=urn:btih:INFO_HASH&dn=nombre&tr=tracker
```

O simplemente el info hash:
```
INFO_HASH
```

### 2. Proceso de reproducción:

- Pega el magnet link o info hash en el campo de texto.
- Haz clic en **"Iniciar descarga P2P"**.
- Espera a que se conecte a peers y obtenga metadata.
- El video comenzará a reproducirse automáticamente.

> **Info:** El reproductor mostrará el progreso de descarga y número de peers conectados.

---

## 📁 Estructura del Proyecto

```
webtorrent-p2p-player/
└── index.html          # Aplicación completa (HTML + CSS + JS)
```

---

## 🛠️ Funcionamiento Técnico

### Trackers Configurados

El proyecto usa los siguientes trackers WebSocket:

```javascript
'wss://tracker.openwebtorrent.com'
'wss://tracker.btorrent.xyz'
'wss://tracker.openwebtorrent.com:443'
```

### Formatos de Video Soportados

- `.mp4`
- `.webm`
- `.mkv`

### Flujo de Trabajo

```
Usuario → Magnet Link → WebTorrent Client → WebRTC Peers → Buffer → Video Player
```

---

## 🐛 Troubleshooting

### ❌ Error: "No se obtuvo metadata en 60 segundos"

El torrent puede no tener seeders activos o los trackers no responden. Verifica que el magnet link sea válido y tenga peers disponibles.

### 📡 No se conecta a peers

- Verifica tu firewall o antivirus.
- Algunos ISPs bloquean conexiones P2P.
- Intenta con otro magnet link con más seeders.

### 🎬 El video no reproduce

- Asegúrate de que el torrent contenga archivos de video (mp4, webm, mkv).
- Algunos formatos pueden no ser compatibles con tu navegador.
- Verifica la consola del navegador (F12) para más detalles.

### 🔒 Error CORS o HTTPS

Si usas HTTPS, algunos trackers WebSocket pueden no funcionar. Usa HTTP en local o configura trackers compatibles con HTTPS.

---

## ⚙️ Personalización

### Agregar más trackers

Edita el array `trackers` en el código:

```javascript
const trackers = [
    'wss://tracker.openwebtorrent.com',
    'wss://tu-tracker-personalizado.com',
    // Agrega más aquí
];
```

### Cambiar timeout de metadata

Modifica la línea del timeout:

```javascript
// De 60 segundos a 120 segundos
}, 120000);
```

### Deshabilitar autoplay

Remueve el atributo `autoplay` del elemento `<video>`:

```html
<video id="player" controls></video>
```

---

## ⚠️ Disclaimer

> **ADVERTENCIA:** Este proyecto es para fines educativos y de demostración. El usuario es responsable de:
> - Cumplir con las leyes de derechos de autor de su país.
> - Usar solo contenido legal y con los permisos apropiados.
> - No distribuir contenido protegido por derechos de autor.

> **Nota:** Los desarrolladores no se hacen responsables del contenido accedido a través de esta herramienta.

---

## 📚 Recursos

- [WebTorrent Documentation](https://webtorrent.io/docs)
- [WebRTC Basics](https://webrtc.org/)
- [BitTorrent Protocol](http://www.bittorrent.org/beps/bep_0003.html)

---

<div align="center">

**Hecho con ❤️ usando WebTorrent y WebRTC**

**¿Te sirvió el proyecto? ¡No olvides compartirlo! 🌟**

</div>
