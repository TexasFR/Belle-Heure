# Belle Heure — Institut de Beauté 🌸
Stack: Express + Supabase + Stripe

## Structure
```
belle-heure/
├── backend/
│   ├── server.js
│   ├── package.json
│   ├── .env.example
│   ├── supabase/
│   │   ├── client.js
│   │   └── schema.sql        ← Exécuter dans Supabase SQL Editor
│   ├── middleware/auth.js
│   └── routes/
│       ├── services.js
│       ├── schedule.js
│       ├── appointments.js
│       ├── gallery.js
│       ├── payments.js
│       └── users.js
└── frontend/
    └── index.html
```

## Installation

```bash
# 1. Supabase: exécuter backend/supabase/schema.sql dans SQL Editor
# 2. Storage: créer bucket "gallery" en mode Public
# 3. Backend
cd backend && cp .env.example .env
# Remplir .env avec vos clés Supabase et Stripe
npm install && npm run dev
# → http://localhost:3001
```

## Créer un admin
```sql
UPDATE public.profiles SET role = 'admin' WHERE id = 'votre-uuid';
```

## Variables .env requises
- SUPABASE_URL, SUPABASE_ANON_KEY, SUPABASE_SERVICE_ROLE_KEY
- STRIPE_SECRET_KEY, STRIPE_PUBLISHABLE_KEY, STRIPE_WEBHOOK_SECRET
- ADMIN_SECRET, PORT, NODE_ENV

## Webhooks Stripe
```bash
stripe listen --forward-to localhost:3001/api/payments/webhook
```
