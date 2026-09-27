---
name: feature-checklist
description: A skill to run against any new backend endpoint or frontend page in this project, to check it against the project's quality rules before it's considered done.
---

# Feature Checklist

Run this checklist against every new backend endpoint or frontend page before considering the work complete.

## Backend

- [ ] Controllers only handle HTTP concerns. All business and database logic lives in the service, never in the controller.
- [ ] Every create/update DTO uses `class-validator` decorators.
- [ ] The global `ValidationPipe` has `whitelist: true` and `forbidNonWhitelisted: true`, so unknown properties are rejected instead of silently stripped.
- [ ] `category` is validated against the fixed enum: `equipment`, `electrical`, `plumbing`, `facility`, or `other`.
- [ ] The `?category=` filter validates the same fixed enum, and invalid values return `400` in both create and filter requests.
- [ ] `status` is never accepted from the client on create. The backend always sets it to `open`.
- [ ] No `any` types are used unless unavoidable. If one is used, add a comment explaining why.
- [ ] Every new or changed endpoint has Swagger decorators and appears correctly at `/api`.
- [ ] Tests exist for the new behavior, and `npm test` and `npm run lint` pass before committing.

## Frontend

- [ ] Pages use components from `components/ui/` instead of raw HTML elements where the shared UI component exists.
- [ ] Pages call the API and never access MongoDB directly.

## Scope

- [ ] Check `specs/campus-maintenance.md` before adding anything outside the MVP feature list.
- [ ] Nothing outside the MVP feature list is added without checking the specification first.