# Kortline — CB Jaca

PWA single-file de gestión de asistencia, equipos, partidos y estadísticas para baloncesto.
Desarrollada por **Mario Nadal Ara** · Stack: HTML + CSS + Vanilla JS · Datos en `localStorage`.

Repositorio: [github.com/MarioNadal/kortline-app](https://github.com/MarioNadal/kortline-app) · URL desplegada: [marionadal.github.io/kortline-app/](https://marionadal.github.io/kortline-app/)

---

## Estado actual

**Versión publicada: v1.0.0** — primera estable pública. Reset semántico desde la serie v1.8.x de desarrollo interno.

Para el alcance, la política de ramas y el plan de v2 (live game) y v3 (Firebase), ver [`ROADMAP.md`](ROADMAP.md).
Para el historial detallado por versión, ver [`CHANGELOG.md`](CHANGELOG.md).
Para el manual de usuario, ver [`MANUAL_USUARIO_KORTLINE.md`](MANUAL_USUARIO_KORTLINE.md).

---

## Qué hace v1.0.0

- Pase de lista de entrenamientos con cuatro estados (presente, ausente, justificado, tarde) y justificación opcional.
- Gestión de equipos, plantillas, posiciones, dorsales y colores.
- Convocatorias de partido con titulares y capitán.
- Detalle de partido con resultado por cuartos editable a mano (Q1/Q2/Q3/Q4 + prórrogas).
- Estadísticas agregadas por jugador y equipo, con riesgo FEB de asistencia.
- Export/import JSON, exportación a Excel y PDF, compartir por WhatsApp.
- PWA instalable con modo offline real (service worker con caché versionada).
- Diseño dark mobile-first con la paleta del club.

**Fuera del alcance de v1.0.0:** el seguimiento en vivo del partido (scoreboard live, faltas, tiempos muertos, quinteto en pista, shot chart en directo). Esa funcionalidad se desarrolla en paralelo en la rama `v2-live` para una futura v2.0.0.

---

## Tabla de versiones publicadas

| Versión | Fecha | Resumen |
|---|---|---|
| **v1.0.2** | 2026-05-13 | Patch: ocultar los 4 toggles de live en "Crear partido" y actualizar el texto del overlay de orientación. |
| v1.0.1 | 2026-05-13 | Patch: ocultar la sección "Modo rápido (live game)" del panel de Ajustes. |
| v1.0.0 | 2026-05-13 | Primera estable pública. Gestión + resultados manuales. Live game desactivado vía feature flag. |

(Las versiones v1.8.x previas formaron parte del desarrollo interno y se conservan en `CHANGELOG.md`.)

---

## Stack

- HTML + CSS + JavaScript vanilla, sin dependencias propias.
- CDN: Chart.js, jsPDF (+autotable), SheetJS (XLSX), Google Fonts (Barlow Condensed + DM Sans).
- Datos en `localStorage` (claves `cbj:t`, `cbj:p`, `cbj:s`, `cbj:m`, `cbj:ev`...).
- Service Worker con app-shell precacheado, network-first para HTML y cache-first para assets.
- Single-file: todo CSS, JS y HTML en un único `index.html`.

---

## Desarrollo

La app es un único `index.html`. No hay build ni pipeline. Para desarrollar basta con abrir el archivo en un navegador moderno. Para probar el service worker, servir desde un host con `python3 -m http.server` o similar (los SW no funcionan con `file://`).

Para el control de versiones y ramas, ver `ROADMAP.md`.

---

## Licencia

© Mario Nadal Ara · CB Jaca. Uso interno del club.
