# Welcome to your Lovable project

This project was built with [Lovable](https://lovable.dev).

## Build with Lovable

Open your project in the [Lovable editor](https://lovable.dev) and keep building.

- **Ship faster**: describe what you want to build and Lovable handles the code.
- **Stay in sync**: connect the project to GitHub and every change made in Lovable is committed straight to your repository.
- **Full ownership**: this code is yours. Push to your repository and your changes sync back into Lovable, ready for your next prompt.

## Development

Prefer working locally? You need Node.js and npm — [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating).

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm run dev
```

## Base de datos (Supabase)

La app guarda tickets de soporte, reportes y mensajes de contacto en Supabase.
Si no hay credenciales configuradas, usa `localStorage` como respaldo (modo
demostración) y todo sigue funcionando.

1. Crea un proyecto en [supabase.com](https://supabase.com).
2. Copia `.env.example` a `.env.local` y completa:

   ```sh
   VITE_SUPABASE_URL=https://tu-proyecto.supabase.co
   VITE_SUPABASE_ANON_KEY=tu-anon-key
   ```

3. Aplica el esquema: en Supabase Studio → **SQL Editor**, pega y ejecuta
   `supabase/migrations/0001_init.sql` (o usa `supabase db push` con la CLI).

El esquema incluye RLS de solo inserción pública: los visitantes pueden enviar
tickets/reportes/mensajes, pero no leer contenido ajeno. La consulta de un
ticket (`/ticket`) usa la función `get_ticket`, que exige número de seguimiento
+ correo. Nunca se debe exponer la clave `service_role`.

## Built with

- TanStack Start
- TypeScript
- React
- Tailwind CSS
- Supabase
