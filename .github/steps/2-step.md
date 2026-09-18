## ✅ ¡Paso 2 completo!

Tu workflow ahora usa `checkout`, corre con cada `push` a `main`, y tiene varios steps en secuencia. 🎉

---

## 📘 Sesión 3 — Events y triggers

**Teoría rápida:**

- `push`: se dispara con cada commit enviado a una rama (puedes filtrar por `branches` o `paths`).
- `pull_request`: se dispara cuando se abre, actualiza o reabre un PR — ideal para validar cambios **antes** de que lleguen a `main`.
- `schedule`: dispara el workflow en horarios fijos usando sintaxis **cron** (ej. `'0 9 * * 1'` = todos los lunes a las 9:00 UTC).
- `workflow_dispatch`: el botón manual que ya usaste en la Sesión 1.
- Un mismo workflow puede tener **varios triggers a la vez** — no son excluyentes entre sí.

---

## ⌨️ Actividad 3 — Múltiples triggers en un solo workflow

Edita `.github/workflows/hello-world.yml` para agregar `pull_request` y `schedule`:

```yaml
name: Hello World

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
  schedule:
    - cron: '0 9 * * 1'
  workflow_dispatch:

jobs:
  saludar:
    runs-on: ubuntu-latest
    steps:
      - name: Descargar el código del repositorio
        uses: actions/checkout@v4

      - name: Decir hola
        run: echo "¡Hola! Este es mi primer workflow de GitHub Actions 🎉"

      - name: Mostrar los archivos del repositorio
        run: ls -la
```

Pasos a seguir:

1. Guarda los cambios en una **rama nueva** (no en `main` directamente), por ejemplo `mi-primer-pr`.
2. Abre un **Pull Request** de `mi-primer-pr` hacia `main`.
3. En cuanto lo abras, verás dos cosas suceder solas:
   - Tu workflow correrá automáticamente por el trigger `pull_request` (revisa la pestaña **Checks** del PR).
   - Un comentario aparecerá en tu propio PR felicitándote — esa es otra Action reaccionando al mismo evento.
4. Haz **merge** del PR a `main`. Eso disparará el workflow otra vez, ahora por el trigger `push`, y el checker del workshop revisará tu archivo final aquí en este Issue.
5. No necesitas esperar hasta el próximo lunes para "ver" el `schedule` funcionando en vivo: ese trigger queda configurado y listo para correr automáticamente en el horario que definiste.

> 💡 **Tip:** `pull_request` y `push` son eventos distintos aunque ambos puedan tocar `main`. Por eso muchos equipos corren tests en `pull_request` (para revisar *antes* de mezclar) y despliegues en `push` a `main` (para publicar *después* de mezclar).
