# Portfolio Website

A personal website built with React and Vite. It includes profile, education, and contact sections. Supabase provides the contact-message backup.

## Requirements

- Node.js 20.19+ or 22.12+
- npm
- A Supabase project for the contact form backup

## Run locally

1. Install the project dependencies:

   ```bash
   npm install
   ```

2. Create a local environment file from the example:

   ```bash
   cp .env.example .env.local
   ```

   On Windows PowerShell, use:

   ```powershell
   Copy-Item .env.example .env.local
   ```

3. Set the Supabase values in `.env.local`:

   ```dotenv
   VITE_SUPABASE_URL=https://your-project-id.supabase.co
   VITE_SUPABASE_ANON_KEY=your-supabase-anon-or-publishable-key
   ```

   Find these values in your Supabase project's API settings. The anon/publishable key is used by the browser and is not a substitute for database security; the SQL scripts below configure Row Level Security (RLS).

4. Start the development server:

   ```bash
   npm run dev
   ```

   Open the local URL printed by Vite.

## Supabase database setup

1. Create a Supabase project and open its **SQL Editor**.
2. Run [`supabase/contact_messages.sql`](./supabase/contact_messages.sql) to create the table used by the contact form.

The contact form can insert messages, but public clients cannot read them.

## Build and checks

```bash
npm run build
npm run preview
npm run lint
```

`npm run preview` serves the production build locally after `npm run build`.

## Deploy the website

The repository includes a Vercel configuration for client-side project-detail routes. To deploy with Vercel:

1. Import the repository into Vercel.
2. Add `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` as project environment variables.
3. Deploy the site.

Make sure the Supabase SQL script has been applied before testing the contact feature.
