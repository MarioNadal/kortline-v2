# Kortline v2 — CB Jaca

PWA single-file de gestión integral de baloncesto: asistencia, equipos, convocatorias, partidos con **marcador en vivo completo** y estadísticas.
Desarrollada por **Mario Nadal Ara** · Stack: HTML + CSS + Vanilla JS · Datos en `localStorage`.

Repositorio: [github.com/MarioNadal/kortline-v2](https://github.com/MarioNadal/kortline-v2) · URL desplegada: [marionadal.github.io/kortline-v2/](https://marionadal.github.io/kortline-v2/)

> Este repo es la rama de desarrollo del **marcador en vivo (v2)**, independiente del v1 estable ([kortline-app](https://github.com/MarioNadal/kortline-app), sin live game). Aquí `FEATURE_LIVE_GAME` está activo.

---

## Estado actual

**En desarrollo activo · pre-release v2.0.0.** Sin tags/releases todavía — se sube directamente a `main` según se van cerrando piezas del live game.

> **Módulo de Incidencias mergeado a `main`** (2026-08-02, desde `feat/incidencias-jugador`). Ver `CHANGELOG.md` para el detalle.

Para el plan de ramas y la relación con v1 (`kortline-app`) y v3 (Firebase), ver [`ROADMAP.md`](ROADMAP.md).
Para el historial detallado, ver [`CHANGELOG.md`](CHANGELOG.md) *(nota: desactualizado respecto al trabajo de live game — pendiente de ponerse al día)*.
Para el manual de usuario, ver [`MANUAL_USUARIO_KORTLINE.md`](MANUAL_USUARIO_KORTLINE.md).

---

## Qué hace hoy

**Gestión (heredado de v1):**
- Pase de lista de entrenamientos con cuatro estados (presente, ausente, justificado, tarde) y justificación opcional.
- Gestión de equipos, plantillas, posiciones, dorsales y colores.
- Convocatorias de partido con titulares y capitán, toggles de entrenador/ayudantes para compartir.
- Estadísticas agregadas por jugador y equipo, con riesgo FEB de asistencia.
- Export/import JSON, exportación a Excel y PDF, compartir por WhatsApp.
- PWA instalable, dark mobile-first con la paleta del club.

**Marcador en vivo (lo nuevo de v2):**
- Reloj de partido con parada automática en falta (si está activado) y en cada sustitución.
- Faltas por jugador y de equipo, con bonus FIBA (5 faltas de equipo → 2 TL) y tiros libres con nº sugerido según tipo de falta (personal / técnica / antideportiva / descalificante).
- Descalificación automática (5 personales, 2 técnicas, 2 antideportivas, o técnica+antideportiva) con sustitución forzosa obligatoria y aviso de "banquillo agotado" si no queda a quién meter.
- Quinteto en pista con sustituciones, tracking de minutos y +/-.
- Modo "acciones de equipo" (sin jugador concreto) para cuando el rival no tiene plantilla registrada — faltas y canastas de equipo van al lado correcto (propio/rival) independientemente de qué pestaña estés mirando.
- Shot chart con mapa de cancha tocable, en modo jugador individual y en modo equipo.
- Vista de estadísticas en directo (cards en landscape, tabla en portrait) con toggle equipo propio / rival.
- Selector de tipo de jugada (🧍 Estático · 🏃 Transición · 🧱 Bloqueo directo) en el panel de acciones — etiqueta cada tiro de campo propio, base para futuros KPIs de equipo del plan anual. Se activa por partido con el toggle **🎬 Tipo de jugada** al crear/editar el partido (por defecto OFF).

**Lesiones:**
- Marcar/editar/dar de alta una lesión por jugador, con origen (entreno/partido/fuera) y nota libre.
- Auto-justifica el pase de lista durante toda la baja (y revierte automáticamente los días que dejen de estar en rango si se edita la fecha de inicio).
- Congela el % de asistencia previo a la lesión (snapshot) para que el riesgo FEB no penalice al jugador mientras está lesionado.
- Historial de lesiones por jugador (fecha inicio/fin, días, origen).

**Incidencias** (activable/desactivable en Ajustes del club → Gestión de jugadores):
- Registro de normas incumplidas por jugador (puntualidad, material, actitud, convivencia, otro), independiente de Lesiones.
- Escalado automático 1ª vez / 2ª vez / 3ª vez / reincidencia grave según la tabla de `Mandamientos_CBJaca_2026-2027.docx`, con consecuencia sugerida editable.
- Botón ⚠️ en la fila del jugador (pantalla Equipo) con contador de incidencias.

---

## Stack

- HTML + CSS + JavaScript vanilla, sin dependencias propias.
- CDN: Chart.js, jsPDF (+autotable), SheetJS (XLSX), Google Fonts (Barlow Condensed + DM Sans).
- Datos en `localStorage` (claves `cbj:t`, `cbj:p`, `cbj:s`, `cbj:m`, `cbj:ev`, `cbj:cfg`...).
- Single-file: todo CSS, JS y HTML en un único `index.html`. Sin build ni pipeline.
- `?demo` en la URL carga un partido de prueba en curso (12 jugadores, Q3) sin tocar datos reales — útil para probar el live game sin arriesgar la info del equipo.

---

## Desarrollo

La app es un único `index.html`. Para desarrollar basta con abrir el archivo en un navegador moderno. Para probar el service worker (si está activo en esta rama), servir desde un host con `python3 -m http.server` o similar — los SW no funcionan con `file://`.

Para el control de versiones y ramas, ver `ROADMAP.md`.

---

## Licencia

© Mario Nadal Ara · CB Jaca. Uso interno del club.
