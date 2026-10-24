# MEDICO

Practice management and prescription platform. Current state: database, access rules, prescription
lifecycle, real PDF generation and an authorized export service, all tested. The web and mobile apps
are not built yet. See `docs/IMPLEMENTATION_STATUS.md` for exactly what exists and what does not, and
`docs/SECURITY.md` for the security model.

## Run the checks

```
bash scripts/pg-test-cluster.sh start       # needs PostgreSQL 16 server binaries
npx tsx --test "packages/**/*.test.ts"      # all tests
npx tsc --noEmit -p tsconfig.json           # type check
```

## Layout

- `supabase/migrations`: schema, Row Level Security, prescription rules, storage policies, export audit
- `packages/types`, `packages/business-logic`: shared types, validation, role matrix
- `packages/pdf`: prescription PDF generator
- `packages/api-core`: server-side services (authorized PDF export) and database adapter
- `packages/db-tests`: tests that run the migrations on a real PostgreSQL and attack the access rules
