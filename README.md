# AUREL Estates v2 — React + Vite + Supabase

Includes public property browsing, filters, lead form, and password-protected Supabase Auth admin area for property CRUD, image uploads, enquiries, and site visits.

## 1. Supabase setup
1. Create a project at https://supabase.com/
2. Open SQL Editor and run `supabase/schema.sql`.
3. In Authentication → Providers, ensure Email is enabled.
4. In Authentication → Users, create your admin user with your email/password.
5. Copy Project URL and anon/public key from Settings → API.
6. Copy `.env.example` to `.env` and fill values.

## 2. Run locally
```bash
npm install
npm run dev
```
Open the URL Vite prints.

## 3. Deploy online (Vercel)
1. Upload/push this folder to a private GitHub repository.
2. Import it in https://vercel.com/ and choose Vite.
3. Add environment variables `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`.
4. Deploy. Add your production domain to Supabase Auth → URL Configuration → Site URL and Redirect URLs.

## 4. Secure admin access
Open `/admin` on your deployed domain. Sign in using the user created in Supabase Auth.
Database policies allow authenticated users to administer records. For a single-owner business, create only your own admin user and disable public signups in Supabase Auth settings.

## 5. Lead capture
Public enquiry and site visit forms insert into `leads` and `site_visits`. Admin view reads these tables. RLS permits public inserts but prevents anonymous reads. Do not collect sensitive information in forms.

## 6. Property images
Admin uploads to Supabase Storage bucket `property-images`; SQL config makes the bucket public for image display while upload/delete are restricted to authenticated users.

## Customize
Update brand details, WhatsApp phone, contact number, location and seed/sample properties in `src/App.jsx`.
