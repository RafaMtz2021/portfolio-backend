
📁 Estructura recomendada del proyecto
bash
Copy
Edit
/directus
├── docker-compose.yaml
├── render.yaml
├── .env.render.example
├── .gitignore
├── uploads/               # (vacío o con tus imágenes)
├── extensions/            # (opcional: hooks, endpoints, etc.)
├── README.md
✅ 1. render.yaml

services:
  - type: web
    name: directus
    env: docker
    plan: free
    autoDeploy: true
    region: oregon
    image:
      url: directus/directus:11.6.1
    envVars:
      - key: DB_CLIENT
        value: pg
      - key: DB_HOST
        sync: false
      - key: DB_PORT
        value: 5432
      - key: DB_DATABASE
        sync: false
      - key: DB_USER
        sync: false
      - key: DB_PASSWORD
        sync: false
      - key: ADMIN_EMAIL
        sync: false
      - key: ADMIN_PASSWORD
        sync: false
      - key: PUBLIC_URL
        sync: false
      - key: SECRET
        sync: false
✅ 2. .env.render.example

DB_CLIENT=pg
DB_HOST=your-postgres-host.render.com
DB_PORT=5432
DB_DATABASE=directus
DB_USER=directus_user
DB_PASSWORD=supersecure

ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=admin123
SECRET=mysecretkey
PUBLIC_URL=https://your-directus-service.onrender.com
⚠️ No subas tus valores reales de producción. Usa este archivo como plantilla y configura los valores reales en el panel de Render.

✅ 3. .gitignore

.env*
uploads/
data/
node_modules/
✅ 4. README.md

# Directus Backend – Render & Docker Compose

Este proyecto contiene una instalación mínima de Directus CMS lista para:

- 🧪 Desarrollo local con Docker Compose
- 🚀 Deploy en [Render](https://render.com)

---

## 🧪 Desarrollo local

### 1. Clonar repositorio
```bash
git clone https://github.com/tu-usuario/directus-backend.git
cd directus-backend

2. Crear archivo .env local (opcional)
Usa los mismos valores que .env.render.example.

3. Levantar servicios

docker-compose up -d
Accede a http://localhost:8055

🚀 Deploy en Render
Crea un nuevo servicio en Render

Usa el repositorio conectado

Render detectará render.yaml

Agrega manualmente las variables de entorno:

DB_HOST, DB_USER, etc.

El servicio se desplegará en https://tu-directus.onrender.com

📁 Carpetas importantes
/uploads: Archivos subidos por Directus

/extensions: Endpoints o hooks personalizados (opcional)

📦 Basado en
Imagen oficial: directus/directus:11.6.1

PostgreSQL compatible
