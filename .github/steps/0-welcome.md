# 👋 ¡Bienvenido/a al Workshop de GitHub Actions!

Este Issue es tu **tablero de progreso**. Aquí irás recibiendo el contenido de cada sesión y el feedback automático de tus actividades.

> No cierres ni edites este Issue manualmente — el workshop se encarga de eso por ti.

---

## 📘 Sesión 1 — ¿Qué es GitHub Actions?

**Teoría rápida:**

- **El problema que resuelve:** automatizar tareas repetitivas (correr tests, hacer deploys, enviar notificaciones) sin que una persona tenga que ejecutarlas a mano cada vez.
- **CI/CD en una frase:** *Integración Continua* = validar tu código automáticamente en cada cambio. *Entrega/Despliegue Continuo* = publicar esos cambios automáticamente.
- **El modelo mental de Actions:**

  ```
  Event (algo pasa) → Workflow (el archivo .yml) → Job (una máquina) → Step (un paso) → Action (una pieza reutilizable)
  ```

- **¿Dónde vive el código?** Todo workflow es un archivo `.yml` dentro de la carpeta `.github/workflows/` de tu repositorio. GitHub los detecta automáticamente, no hay que instalar nada.

---

## ⌨️ Actividad 1 — Tu primer workflow

1. En tu fork, crea el archivo `.github/workflows/hello-world.yml` (puedes hacerlo directo en el navegador: **Add file → Create new file**).
2. Pega este contenido exacto:

   ```yaml
   name: Hello World

   on:
     workflow_dispatch:

   jobs:
     saludar:
       runs-on: ubuntu-latest
       steps:
         - name: Decir hola
           run: echo "¡Hola! Este es mi primer workflow de GitHub Actions 🎉"
   ```

3. Guarda el archivo con un commit directo a `main` (mensaje sugerido: `Agrega mi primer workflow`).
4. Ese mismo push disparará automáticamente al "checker" del workshop, que revisará tu archivo y te dará feedback aquí mismo en unos segundos — vuelve a esta página y actualízala.
5. Además, ve a la pestaña **Actions** → selecciona **"Hello World"** en la lista de la izquierda → **Run workflow** → **Run workflow**, para verlo correr manualmente y leer el mensaje en el log.

> 💡 **Tip:** `workflow_dispatch` es el evento que te permite correr un workflow **manualmente** desde la pestaña Actions con un botón. Es el más útil mientras estás aprendiendo y quieres probar cambios a demanda.
