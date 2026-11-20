# PROYECTO_TRAINAPP

App web **mobile-first** para registrar entrenos de gimnasio: series por ejercicio, calorías estimadas y editables, calendario, peso corporal y estadísticas. Datos privados de un único usuario en Supabase, desplegada en Vercel (plan gratuito).

## Estado

Fase 0 completada: **spec aprobado** el 2026-11-20. No hay código de aplicación todavía; se implementará tarea por tarea siguiendo el plan del spec.

- [Spec aprobado](docs/spec.md) — fuente de verdad de requisitos, datos y pruebas.
- [AGENTS.md](AGENTS.md) — reglas de trabajo, convenciones y política de git.

## Stack previsto

Next.js 15 (App Router, TypeScript) · Tailwind CSS v4 · shadcn/ui · Supabase (Postgres + Auth + RLS) · `@supabase/ssr` · Zod · Recharts · Vitest / Testing Library / Playwright.

## Puesta en marcha

La aplicación aún no existe. Cuando se complete la tarea T01:

```bash
npm install
cp .env.example .env.local   # rellenar con valores reales; NUNCA commitear .env.local
npm run dev
```

## Variables de entorno

| Variable | Público/Secreto | Descripción |
|---|---|---|
| `NEXT_PUBLIC_SUPABASE_URL` | Público | URL del proyecto Supabase. |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Público (RLS) | Clave anónima; segura en el navegador porque RLS protege los datos. |
| `SUPABASE_SERVICE_ROLE_KEY` | **Secreto** | Solo scripts locales/admin; jamás en el bundle del navegador. |
| `NEXT_PUBLIC_SITE_URL` | Público | URL base para los redirects de Auth (`http://localhost:3000` en local). |

`.env`, `.env.local` y `.env.*` están ignorados por git; solo se versiona `.env.example`.

## Despliegue

Vercel detectará el proyecto en la raíz del repo. Añadir las variables anteriores en *Project Settings → Environment Variables* y desplegar. Dominio gratuito: `https://<nombre-proyecto>.vercel.app`.

> Nota: los proyectos gratuitos de Supabase pueden pausarse por inactividad; comprobar las condiciones vigentes del plan.

## Git

Cada operación git (commit, push, etc.) requiere aprobación explícita del usuario justo antes de ejecutarse. Ver [AGENTS.md](AGENTS.md).
