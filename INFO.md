# Full-Stack Ownership con IA y Automatización
## De Código Legado a Infraestructura Moderna y Segura

---

## Resumen Ejecutivo

El programa capacita al desarrollador para asumir el control integral de un proyecto técnico. El enfoque se desplaza de "escribir código" a "gestionar sistemas", utilizando la IA para auditar, documentar, migrar bases de datos y desplegar aplicaciones bajo estándares de seguridad modernos.

---

## Estructura del Programa

| Módulo | Semanas | Clases | Enfoque |
|--------|---------|--------|---------|
| 1 — Control Total y Auditoría | 1–2 | 1, 2, 3 | Relevamiento, documentación y seguridad de BD |
| 2 — Migración y Refactorización | 3–4 | 4, 5, 6 | Modernización de stack, testing y seguridad proactiva |
| 3 — Automatización con Docker y n8n | 5–6 | 7, 8, 9 | Dockerización, orquestación y CI/CD |
| 4 — Despliegue y Proyecto Final | 7–8 | 10, 11, 12 | Deploy controlado, mentoría y presentación |

---

## Módulo 1: Control Total y Auditoría (Semanas 1–2)

**Objetivo:** Levantar el proyecto, entender la base de código existente y establecer el entorno de control.

### Clase 1 — Ingesta y Relevamiento de Proyectos Complejos (1h 30min)

**Objetivo:** Convertir un repositorio desconocido en un mapa mental y técnico claro en 90 minutos.

**Estructura:**

**Bloque 1 · Cambio de paradigma (10 min)**
- Antes: leer código manualmente, archivo por archivo
- Ahora: hacer que la IA lea el sistema completo
- Concepto clave: "No entendés archivo por archivo → entendés el sistema completo"

**Bloque 2 · Setup interactivo (15 min)**
- Herramientas: Cursor, Gemini 1.5 Pro (ventana de contexto extendida)
- Alternativa mobile: subir repo a GitHub + usar interfaz web + prompts

**Bloque 3 · Exploración total (25 min)**

Prompt 1 — Análisis general:
```
Analiza este proyecto completo.

Quiero:
1. Qué hace el sistema
2. Módulos principales
3. Flujo de datos
4. Riesgos técnicos
```

Prompt 2 — Profundización:
```
Identifica:
- Código duplicado
- Acoplamiento fuerte
- Posibles bugs
- Riesgos de seguridad
```

**Bloque 4 · Workshop (30 min)**
- Input: Repo real o ejemplo (Java / Python / Node)
- Generar: diagrama de arquitectura, flujo de datos
- Identificar: deuda técnica, vulnerabilidades
- Output priorizado: 🔴 crítico / 🟡 medio / 🟢 bajo

**Bloque 5 · Cierre y reflexión (10 min)**
- ¿Qué entendiste que antes te llevaba días?
- ¿Qué NO entendió bien la IA?

**Entregable:** Documento con arquitectura, flujo de datos y lista priorizada de riesgos.

---

### Clase 2 — Estrategias de Documentación Dinámica (1h 30min)

**Objetivo:** Crear documentación que no quede obsoleta, se genere automáticamente y sea útil para humanos y para la IA.

**Estructura:**

**Bloque 1 · Concepto clave (15 min)**
- "La documentación ya no se escribe → se genera y se mantiene sola"
- Tipos: Técnica, Funcional, Operativa

**Bloque 2 · Setup (15 min)**
- Herramientas: Cursor, Markdown/Wiki, archivos de contexto

**Bloque 3 · "Enseñarle a la IA" (25 min)**

Crear archivo `/docs/context.md`:
```markdown
Este sistema:
- Gestiona usuarios y autenticación
- Usa PostgreSQL como base de datos principal
- Expone una API REST (versión 2)

Reglas de negocio:
- No borrar datos críticos, solo soft-delete
- Validar todos los inputs antes de persistir
```

**Bloque 4 · Workshop (30 min)**

Paso 1 — Generación inicial:
```
Genera documentación completa del sistema:
- Arquitectura general
- Endpoints disponibles
- Modelo de datos y relaciones
```

Paso 2 — Auto-actualización: cada vez que cambie el código, actualizar la documentación automáticamente.

Paso 3 — Versionado: guardar en `/docs/`, integrar con Git.

**Checklist de evaluación:**
- ¿Se entiende el sistema sin leer código?
- ¿La IA puede usar esa documentación como contexto?

**Entregables:** Wiki técnica completa · Archivo de contexto reutilizable `context.md`

---

### Clase 3 — Gestión y Seguridad de la Base de Datos (1h 30min)

**Objetivo:** Entender y asegurar la base de datos usando IA como auditor especializado.

**Estructura:**

**Bloque 1 · Introducción (15 min)**
- Problemas típicos: queries lentas, SQL injection, backups inexistentes

**Bloque 2 · "Leer la DB como un mapa" (20 min)**
```
Analiza este esquema de base de datos.

Quiero:
- Relaciones entre tablas
- Tablas y columnas críticas
- Problemas de diseño
- Índices faltantes
```

**Bloque 3 · Optimización con IA (20 min)**

Ejemplo — Antes (vulnerable):
```sql
SELECT * FROM users WHERE email = 'test'
```

Después (seguro y eficiente):
```python
cursor.execute(
    "SELECT id, name, email FROM users WHERE email = %s",
    (email,)
)
```

**Bloque 4 · Workshop completo (30 min)**
- Parte 1 — Auditoría: SQL injection, falta de índices, datos sensibles expuestos
- Parte 2 — Seguridad: vulnerabilidades en la capa de acceso a datos
- Parte 3 — Backup: diseñar backups diarios con versionado y recuperación

**Buenas prácticas:**
- ORM con consultas parametrizadas (nunca concatenar strings)
- Variables parametrizadas en queries directas
- Logs de acceso a tablas sensibles
- Principio de mínimo privilegio para usuarios de BD

**Entregables:** Informe de seguridad · Queries optimizadas · Estrategia de backup automatizado

---

**Resultado del Módulo 1:**
- Leer cualquier base de código en minutos usando IA
- Documentar sistemas automáticamente con contexto reutilizable
- Auditar la seguridad básica de cualquier codebase
- Entender bases de datos complejas y sus riesgos
- Tener control real del sistema desde el primer día

---

## Módulo 2: Migración y Refactorización Segura (Semanas 3–4)

**Objetivo:** Evolucionar el código a una versión moderna y robusta sin romper producción.

### Clase 4 — Modernización de Stack (The Migration Path) (1h 30min)

**Objetivo:** Aprender a evolucionar un proyecto existente sin romper producción, usando IA para analizar dependencias, planificar migraciones y ejecutar refactorizaciones controladas.

**Bloque 1 · Auditoría técnica automática (20 min)**
```
Analizá este proyecto y generá un informe de modernización con:

1. Versión actual del stack
2. Dependencias obsoletas
3. Librerías con riesgo de seguridad
4. Patrones legacy detectados
5. Quick wins de refactor
6. Riesgos de migración
7. Plan incremental en fases
```

Documento resultado: `/docs/migration-assessment.md`

**Bloque 2 · Refactorización asistida (30 min)**

Python:
- `requirements.txt` → `pyproject.toml`
- Sin typing → type hints
- Validaciones manuales → Pydantic
- Errores genéricos → excepciones específicas

JavaScript/Node:
- CommonJS → ES Modules
- JS → TypeScript
- Callbacks → async/await
- Validaciones → Zod

Java:
- Java 8 → 21
- Spring Boot upgrade
- DTOs mejorados

```
Refactorizá este módulo para hacerlo moderno y mantenible.

Objetivos:
- Tipado fuerte
- Validación robusta de inputs
- Manejo explícito de errores
- Separación de responsabilidades
- Mantener compatibilidad funcional exacta
```

**Bloque 3 · Plan de despliegue seguro (25 min)**
- Blue/green deployment, canary release, feature flags, rollback

**Entregables:** `/docs/migration-assessment.md` · `/docs/migration-plan.md` · `/refactored-module/`

---

### Clase 5 — Testing Autónomo y Cobertura (1h 30min)

**Objetivo:** Usar IA para generar y mantener tests automáticos inteligentes que protejan el negocio durante la migración.

**Bloque 1 · Mapa de cobertura actual (20 min)**
```
Analizá este proyecto e identificá:

1. Módulos sin cobertura de tests
2. Funciones críticas de negocio
3. Escenarios de borde no considerados
4. Riesgos si esas funciones fallan
5. Prioridad de testing
```

**Bloque 2 · Generación automática de tests (35 min)**

Unit tests (pytest / Jest / JUnit / xUnit):
```
Generá tests unitarios completos para este archivo.

Incluir:
- Casos felices (happy path)
- Casos con inputs inválidos
- Edge cases y límites
- Mocks necesarios bien documentados
```

Integration tests:
```
Generá tests de integración para validar este flujo completo.
```

**Bloque 3 · Tests de regresión (20 min)**
```
Diseñá tests que aseguren que la nueva implementación
mantiene exactamente la lógica anterior.
```

**Entregables:** `/tests/unit/` · `/tests/integration/` · `/tests/regression/` · `/docs/testing-strategy.md`

---

### Clase 6 — Seguridad Proactiva y Análisis de Vulnerabilidades (1h 30min)

**Objetivo:** Convertir a la IA en un auditor permanente de seguridad del proyecto.

**Bloque 1 · Escaneo automático (25 min)**

Herramientas: Semgrep, Snyk, OWASP Dependency-Check, GitHub Advanced Security

```
Auditá este repositorio buscando vulnerabilidades:

1. Código inseguro (injections, XSS, CSRF)
2. Librerías con CVEs conocidos
3. Secretos o credenciales expuestos
4. Malas prácticas de autenticación
5. Nivel de severidad de cada hallazgo
6. Propuesta de remediación para cada uno
```

**Bloque 2 · Corrección asistida (30 min)**
```python
# Vulnerable:
query = f"SELECT * FROM users WHERE id={user_id}"

# Seguro:
cursor.execute("SELECT * FROM users WHERE id = %s", (user_id,))
```

**Bloque 3 · Automatización en CI/CD (20 min)**
```
Generá un pipeline de GitHub Actions que ejecute:
- Tests unitarios e integración
- Scan de dependencias (Snyk / OWASP)
- Análisis estático (Semgrep)
- Bloqueo si hay vulnerabilidades críticas
```

**Entregables:** `/docs/security-audit.md` · `/docs/remediation-plan.md` · `/.github/workflows/security.yml`

---

**Resultado del Módulo 2:**
- Proyecto modernizado con código limpio y dependencias actualizadas
- Suite de tests generada por IA con cobertura de regresión
- Pipeline CI/CD con escaneo de seguridad continuo

---

## Módulo 3: Automatización de Operaciones con n8n y Docker (Semanas 5–6)

**Objetivo:** Eliminar tareas manuales repetitivas de levantamiento de entornos, configuración de servicios, monitoreo, backups, deploy, validación de releases y respuesta a incidentes.

Stack: Docker · Docker Compose · n8n · Agentes IA conectados a repositorios · CI/CD automatizado

### Clase 7 — Dockerización Profesional del Entorno (1h 30min)

**Objetivo:** Crear imágenes Docker optimizadas para producción usando multi-stage builds.

**Bloque 1 · Por qué Docker (15 min)**
- Reproducibilidad de entornos garantizada
- Aislamiento y seguridad entre servicios
- Escalabilidad horizontal simplificada

**Bloque 2 · Multi-stage Dockerfile (25 min)**
```dockerfile
# Stage 1: Builder
FROM python:3.12-slim AS builder
WORKDIR /app
COPY pyproject.toml .
RUN pip install --no-cache-dir .

# Stage 2: Production
FROM python:3.12-slim
WORKDIR /app
COPY --from=builder /usr/local/lib /usr/local/lib
COPY src/ ./src/
RUN adduser --disabled-password appuser
USER appuser
EXPOSE 8000
CMD ["python", "-m", "uvicorn", "src.main:app"]
```

**Bloque 3 · Docker Compose (35 min)**
```yaml
services:
  app:
    build: .
    ports: ["8000:8000"]
    depends_on:
      db:
        condition: service_healthy

  db:
    image: postgres:16-alpine
    healthcheck:
      test: ["CMD", "pg_isready"]
      interval: 10s

  n8n:
    image: n8nio/n8n
    ports: ["5678:5678"]
```

**Entregables:** `Dockerfile` · `docker-compose.yml` · `.env.example`

---

### Clase 8 — Orquestación de Flujos de Mantenimiento en n8n (1h 30min)

**Objetivo:** Automatizar monitoreo, backups y alertas sin scripts manuales.

**Bloque 1 · ¿Qué es n8n? (15 min)**
- Automatización visual de workflows
- Open-source, self-hosted, sin vendor lock-in
- Más de 400 integraciones nativas

**Bloque 2 · Setup (15 min)**
- Con Docker: imagen `n8nio/n8n` (recomendado)
- Sin Docker: `npm install -g n8n && n8n start`
- Acceso en `http://localhost:5678`

**Bloque 3 · Flujo de monitoreo de BD (30 min)**
- Cron cada 5 minutos → conectar a la DB → `SELECT 1`
- Si falla: alerta en Slack/Telegram
- Si respuesta > 500ms: ejecutar script de diagnóstico
- Registrar cada check en tabla de auditoría

**Bloque 4 · Flujo de backup automatizado (25 min)**
- Trigger diario a las 03:00 AM
- Ejecutar `pg_dump` → comprimir → subir a Google Drive
- Eliminar backups con más de 30 días
- Enviar resumen por email

**Entregables:** `monitoring-flow.json` · `backup-flow.json`

---

### Clase 9 — Agentes de IA para CI/CD (1h 30min)

**Objetivo:** Conectar n8n con GitHub para automatizar el ciclo de vida completo del código.

**Bloque 1 · Integración n8n ↔ GitHub (20 min)**
- Webhook en GitHub → n8n
- Eventos: push, PR, release, workflow_run
- Trigger: push a `main` → iniciar pipeline

**Bloque 2 · GitHub Actions + n8n combinados (30 min)**
- GitHub Actions para build y tests
- n8n para orquestación de deploy y notificaciones
- Webhook de GHA → n8n para continuar el flujo

**Bloque 3 · Rollback automático (30 min)**
- Monitoreo post-deploy de métricas
- Si error rate > umbral → rollback automático
- Notificación del incidente con causa y versión restaurada

**Entregables:** `.github/workflows/deploy.yml` · `cicd-orchestrator.json` · `auto-rollback.json`

---

**Resultado del Módulo 3:**
- Entorno reproducible con Docker en cualquier servidor
- Monitoreo proactivo de BD con alertas automáticas
- Backups automatizados con verificación de integridad
- Pipeline CI/CD con rollback automático

---

## Módulo 4: Despliegue, Monitoreo y Proyecto Final (Semanas 7–8)

**Objetivo:** Poner el sistema en producción y asegurar su estabilidad.

### Clase 10 — Estrategias de Despliegue y Rollback (1h 30min)

**Estrategias:**
- **Blue/Green:** dos entornos idénticos, switch instantáneo del router
- **Canary release:** rollout gradual 5% → 25% → 100%
- **Feature flags:** activar funcionalidades sin nuevo deploy
- **Rolling update:** reemplazar una instancia a la vez sin downtime

**Simulación de deploy fallido:**
1. Simular un bug crítico en producción
2. Detectar el fallo a través de métricas
3. Ejecutar rollback al tag anterior
4. Documentar el post-mortem

**Criterios de go/no-go:**
- Error rate < 0.1% en los primeros 5 minutos
- Latencia P95 similar a la versión anterior (±20%)
- Health checks de todos los servicios en verde

**Entregables:** `/docs/deployment-strategy.md` · `/docs/runbook-rollback.md`

---

### Clase 11 — Taller de Casos Reales (Mentoría) (1h 30min)

**Formato:** trabajo intensivo sobre proyectos de los estudiantes.

**Casos típicos:**
- Migración de base de datos con datos reales
- Dockerización de una app legacy sin contenedores
- Agregar autenticación JWT a una API existente
- Configurar CI/CD desde cero en un repo existente
- Automatizar el deploy de un proyecto propio con n8n
- Auditoría de seguridad de dependencias del proyecto actual

**Entregable:** Avance documentado del proyecto personal con al menos un componente funcionando end-to-end.

---

### Clase 12 — Presentación de Ecosistemas Autónomos (1h 30min)

**Cierre:** demostración del proyecto final: de código legado a una app moderna, documentada, dockerizada y con mantenimiento automatizado.

**Criterios de evaluación:**
- ✅ Arquitectura documentada y comprensible sin leer código
- ✅ Levanta con `docker compose up`
- ✅ Al menos un flujo n8n funcionando
- ✅ Auditoría de seguridad básica superada
- ✅ Suite de tests que corra en CI
- ✅ Pipeline de deploy automático al pushear a `main`

**Próximos pasos sugeridos:**
- Agentes autónomos que auditan y mejoran código
- Scraping + embeddings + Neo4j para grafos de conocimiento
- Pipelines de ETL automatizados con IA
- MLOps: despliegue y monitoreo de modelos en producción

**Entregable final:** Repositorio público + README profesional + video demo de 3 minutos + documentación completa en `/docs/`

---

## Objetivos Esperados del Programa

| Objetivo | Descripción |
|----------|-------------|
| **Soberanía Técnica** | Capacidad de entrar en cualquier repositorio y entender la arquitectura total en minutos |
| **Migración Confiable** | Pasar de sistemas antiguos a modernos con una red de seguridad de tests automáticos |
| **Infraestructura como Código** | Dominar Docker para que el "en mi máquina funciona" desaparezca |
| **Mantenimiento Zero-Touch** | Flujos en n8n que gestionen logs, backups y alertas sin intervención humana constante |
