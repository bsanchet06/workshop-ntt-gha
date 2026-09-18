## 🎉 ¡Workshop Semana 1 completado!

En tres sesiones aprendiste:

- [x] Qué es GitHub Actions y el modelo `Event → Workflow → Job → Step → Action`.
- [x] La anatomía completa de un workflow: `on`, `jobs`, `runs-on`, `steps`, `run` vs `uses`.
- [x] Cuatro triggers funcionando en el mismo archivo: `workflow_dispatch`, `push`, `pull_request` y `schedule`.

### 🔎 Ahora que ya sabes esto...

Échale un ojo a los workflows que estuvieron corriendo todo este tiempo dentro de `.github/workflows/`:

- `0-start-workshop.yml`
- `1-check-progress.yml`
- `2-celebrate-pr.yml`

Son workflows reales, usando exactamente los mismos conceptos que acabas de aprender (más un poco de `if` y contexts que verás pronto). Ya puedes empezar a leerlos.

### Lo que viene (Semana 2)

- Runners: hosted vs self-hosted.
- Variables y contexts (`${{ github.* }}`).
- Secrets y cómo usarlos sin exponerlos en el log.

Guarda este repositorio (tu fork) — lo seguirás extendiendo en las próximas sesiones.

¡Buen trabajo! 🚀
