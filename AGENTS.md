# AGENTS.md — PROYECTO_TRAINAPP

## Regla de oro (SDD)

Trabajar siempre en **español**. Antes de escribir código de aplicación debe existir un spec aprobado en `docs/spec.md`. El usuario aprueba escribiendo literalmente `spec aprobado`. Los cambios de alcance se proponen primero; si algo es ambiguo, se añade a «Preguntas abiertas» con una opción por defecto, nunca se inventa.

## Git: aprobación obligatoria

El usuario debe aprobar **expresamente, justo antes de cada ejecución**, cualquier operación git (`init`, `add`, `commit`, `push`, `checkout`, `merge`, `rebase`, `reset`, etc.). Sin esa aprobación: no se ejecuta nada. Antes de pedirla, mostrar `git status` y `git diff` de lo que se va a incluir. No modificar la configuración de git, no usar `--force`, no hacer commits vacíos ni incluir secretos o `.env`. Remote: `https://github.com/Meraxesfire/PROYECTO_TRAINAPP`.

## Estado del proyecto

- **Fase 0 completada:** spec aprobado el 2026-11-20 (`docs/spec.md`).
- **Pendiente:** Fase 1, tareas T01–T06 (ver §13 del spec). Todavía no hay código de aplicación.

## Estructura prevista

```
PROYECTO_TRAINAPP/
├── AGENTS.md              # reglas para agentes (este archivo)
├── README.md              # puesta en marcha para personas
├── docs/spec.md           # spec aprobado, fuente de verdad
├── .env.example           # plantilla de variables (sin valores reales)
├── .gitignore
├── src/                   # app Next.js 15 (se crea en T01)
├── supabase/migrations/   # migraciones 0001…0009 (T03–T05)
└── ...
```

El proyecto Next.js vive en la **raíz del repo** para que Vercel lo detecte sin configuración adicional.

## Convenciones

- UI, documentación y mensajes de error en español (`es-ES`); identificadores de código en inglés.
- Sistema métrico (kg, cm) y coma decimal en pantalla.
- **Una tarea por vez**, comprobada contra sus criterios de aceptación antes de pasar a la siguiente.
- Toda tabla nueva lleva RLS; los cálculos derivados (IMC, calorías, duración) se implementan en funciones/triggers de Supabase, nunca solo en el cliente.
- Las claves `NEXT_PUBLIC_*` son públicas y están protegidas por RLS; `SUPABASE_SERVICE_ROLE_KEY` es secreta y solo se usa en scripts locales.
- No añadir comentarios al código salvo que aporten contexto no obvio o el usuario lo pida.

## Comandos

Pendiente de crear en T01. Una vez existan, esta es la lista prevista:

| Comando | Uso |
|---|---|
| `npm run dev` | Servidor local. |
| `npm run build` | Compilación de producción. |
| `npm run lint` | Linter. |
| `npm run typecheck` | Comprobación de tipos. |
| `npm test` | Pruebas unitarias (Vitest). |
| `npx playwright test` | Pruebas E2E. |
| `supabase db push` | Aplicar migraciones locales. |
| `supabase gen types typescript --project-id <ref>` | Regenerar tipos de BD. |

**Antes de dar por terminada cualquier tarea:** ejecutar lint, typecheck y las pruebas correspondientes del §12 del spec.
