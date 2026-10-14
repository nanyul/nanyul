# Cómo publicar este perfil

Este proyecto es una adaptación para `nanyul` de la estructura del repo público
[emmi-lili/emmi-lili](https://github.com/emmi-lili/emmi-lili): banner animado, radares,
tarjetas de estadísticas y workflows que se actualizan solos.
Los scripts son de ella; el contenido, los datos y los logos del banner son tuyos.
Si lo publicas, conviene darle crédito (o avisarle) por la idea y el código base.

## 1. Subir al repo

1. Crea un repo **público** llamado `nanyul` en tu cuenta (igual que tu usuario).
2. Sube **todo** el contenido de esta carpeta, incluida `.github/` (es una carpeta oculta).

## 2. Poner tu foto en el banner

Ahora el banner usa las iniciales "YN" como retrato.

1. Guarda tu foto como `assets/source/photo.png` (de frente, buena luz, cabeza y hombros;
   con fondo transparente se ve mejor en el tema oscuro; tamaño sugerido ~420×480 px).
2. Regenera:

```bash
pip install -r scripts/banner/requirements.txt
python scripts/banner/generate.py
```

3. Sube los archivos nuevos (`assets/banner-*.v9.svg` y `scripts/banner/data/`).
   Si el banner no se actualiza en tu perfil, cambia `v9` por `v10` en el nombre y en el README (caché).

## 3. Activar los workflows

1. Repo → **Settings → Actions → General → Workflow permissions** → *Read and write permissions*.
2. Opcionalmente, crea un Personal Access Token (GitHub → Settings → Developer settings → Tokens) y
   guárdalo en el repo como secret llamado `METRICS_TOKEN` (**Settings → Secrets and variables →
   Actions**). Si no existe ese secret, el workflow usa automáticamente el token integrado de GitHub;
   el PAT permite obtener métricas más completas, especialmente las contribuciones.
3. Pestaña **Actions** → ejecuta manualmente *Charts and cards* y *Metrics* (**Run workflow**).
   Crean `card-*.svg` y `metrics.languages.svg`, que el README ya referencia.
   Hasta esa primera corrida esas dos imágenes se ven rotas.

## 4. Personalizar

| Qué | Dónde |
| --- | --- |
| Filas del panel `SYSTEM.INFO` (correo, LinkedIn, etc.) | `ROWS` en `scripts/banner/generate.py` |
| Valores de los radares (ahora son de ejemplo) | `assets/skills.json` y `assets/langmix.json` |
| Repos destacados en las tarjetas | `assets/projects.json` |
| Redes sociales | Bloque comentado en `README.md` |

Después de editar `skills.json`, `langmix.json` o `projects.json`, el workflow redibuja solo al hacer push.
