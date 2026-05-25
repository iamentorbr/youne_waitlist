# YOUNE — Landing Page

## Como configurar o Supabase na landing

Abra o arquivo `index.html` e localize estas duas linhas:

```
const SB_URL = '%%SB_URL%%';
const SB_KEY = '%%SB_KEY%%';
```

Substitua pelos seus dados do Supabase:
- SB_URL → Settings → API → Project URL
- SB_KEY → Settings → API → anon public key

Exemplo:
```
const SB_URL = 'https://xyzxyz.supabase.co';
const SB_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...';
```

## Deploy na Vercel
1. Acesse vercel.com → Add New Project
2. Deploy without Git → arraste esta pasta
3. Clique Deploy

## Tabela no Supabase (execute no SQL Editor)

```sql
CREATE TABLE IF NOT EXISTS youne_waitlist (
  id bigserial primary key,
  email text unique not null,
  lang text default 'en',
  source text default 'landing',
  created_at timestamptz default now()
);

ALTER TABLE youne_waitlist ENABLE ROW LEVEL SECURITY;
CREATE POLICY "allow_insert" ON youne_waitlist FOR INSERT WITH CHECK (true);
CREATE POLICY "allow_select" ON youne_waitlist FOR SELECT USING (true);
```
