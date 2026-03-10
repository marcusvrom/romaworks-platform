# RomaWorks Platform

RomaWorks Platform é uma **Core Platform SaaS multi-tenant** desenvolvida pela RomaWorks para criar aplicações de gestão e automação para pequenas empresas.

O primeiro produto baseado nesta plataforma é:

**RomaSchedule** — sistema de agendamento e relacionamento com clientes para negócios de atendimento como:

- barbearias
- salões de beleza
- clínicas de estética
- estúdios de tatuagem
- consultórios

---

# Objetivo da plataforma

Criar uma **base reutilizável** que permita construir rapidamente múltiplos produtos SaaS com:

- autenticação
- multi-tenancy
- CRM
- agendamentos
- chatbot
- notificações
- pagamentos

---

# Stack tecnológica

Frontend
- Angular
- Angular Material
- PWA (Progressive Web App)

Backend
- Node.js
- NestJS

Banco
- PostgreSQL

Infraestrutura
- Docker
- Nginx
- Redis

Arquitetura
- Multi-tenant com `tenant_id` UUID
- `tenant_id` presente no JWT

---

# Estrutura do projeto
romaworks-platform
├ docs
├ apps
│ ├ api
│ └ web
├ infra
│ ├ docker
│ ├ nginx
│ └ scripts


---

# Como rodar o projeto localmente

## Requisitos

- Docker
- Node.js
- npm ou pnpm

## Subir ambiente

```bash
docker-compose up -d
```

## Rodar backend

```bash
cd apps/api
npm install
npm run start:dev
```

## Rodar frontend

```bash
cd apps/web
npm install
npm start
```

## Documentação

# Veja a pasta docs:

- ARCHITECTURE.md

- MULTI-TENANCY.md

- ROADMAP.md

- API-STANDARDS.md

## Status do projeto

🚧 Em desenvolvimento (MVP)

## Licença

Proprietary — RomaWorks


---

# 📄 ARCHITECTURE.md

Este é **o documento mais importante do projeto**.

```md
# Architecture — RomaWorks Platform

Este documento descreve a arquitetura da plataforma SaaS da RomaWorks.

---

# Visão geral

RomaWorks Platform é uma **Core Platform multi-tenant** que serve como base para múltiplos produtos SaaS.

Arquitetura:

Frontend
→ Angular (PWA)

Backend
→ NestJS API

Banco
→ PostgreSQL

Mensageria
→ Redis

Infra
→ Docker + Nginx

---

# Arquitetura de alto nível
Browser
↓
Angular Web App
↓
API Gateway (NestJS)
↓
Application Services
↓
Database (PostgreSQL)


---
# Multi-tenancy

A plataforma utiliza isolamento por:


tenant_id UUID


Todas as entidades devem possuir `tenant_id`.

Exemplo:


clients
appointments
services
users


---
# Autenticação

Sistema baseado em:

JWT

Payload:


{
sub: user_id,
tenant_id: uuid,
role: role
}


---

# Módulos principais

Core modules

- Auth
- Tenants
- Users
- Permissions
- Notifications
- Audit Logs

Business modules

- Clients
- Employees
- Services
- Appointments
- Payments
- Chatbot

---

# Infraestrutura inicial

1 VPS

Containers:

- nginx
- api
- postgres
- redis
- worker

---

# Escalabilidade futura

Separação futura:

- API nodes
- database cluster
- message queue
- CDN