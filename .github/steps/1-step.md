## ✅ ¡Paso 1 completo!

Tu workflow `hello-world.yml` tiene un trigger `workflow_dispatch`, un `runs-on` y un step con `run` — y corrió correctamente. Bien hecho 🎉

---

## 📘 Sesión 2 — Anatomía de un workflow

**Teoría rápida:**

- `name`: el nombre visible del workflow en la pestaña Actions.
- `on`: qué evento(s) lo disparan.
- `jobs`: uno o más trabajos; cada uno corre en **una máquina limpia** (`runs-on`).
- `steps`: la secuencia de pasos dentro de un job. Se ejecutan **en orden**, de arriba hacia abajo.
- `run` vs `uses`:
  - `run` ejecuta comandos de shell directamente.
  - `uses` invoca una **Action** ya construida (por ti, por tu equipo o por la comunidad).
- `actions/checkout@v4` es casi siempre el primer step: sin él, el job **no** tiene acceso a los archivos de tu repositorio.

---

## ⌨️ Actividad 2 — Dispara tu workflow con un push

Edita `.github/workflows/hello-world.yml` para que quede así:

```yaml
name: Hello World

on:
  push:
    branches:
      - main

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

Guarda los cambios con un commit directo a `main`. En cuanto GitHub reciba el push, tu workflow se ejecutará **solo**, sin que tengas que apretar ningún botón — así es como funciona la integración continua en la práctica. El checker del workshop también reaccionará y te dará feedback aquí mismo.

Revisa la pestaña **Actions**, abre la ejecución más reciente y confirma que el step "Mostrar los archivos del repositorio" efectivamente lista los archivos de tu repo — eso confirma que el `checkout` funcionó.

> 💡 **Tip:** si quitaras el `uses: actions/checkout@v4`, el step `ls -la` seguiría corriendo, pero la máquina estaría vacía y no verías tus archivos. Es un buen experimento mental para entender por qué el checkout es casi siempre obligatorio.
