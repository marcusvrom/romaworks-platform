# Multi-Tenancy Model

RomaWorks Platform utiliza arquitetura **multi-tenant com isolamento lógico**.

---

# Identificação do tenant

Cada empresa possui:


tenant_id UUID


---

# Origem do tenant_id

O `tenant_id` é enviado no JWT.

Exemplo:


{
sub: user_id,
tenant_id: "uuid"
}


---

# Regras obrigatórias

1. Toda entidade deve possuir `tenant_id`

2. Toda query deve filtrar por `tenant_id`

Exemplo correto:


SELECT * FROM clients
WHERE tenant_id = :tenant_id


---

# Nunca confiar no frontend

O backend sempre extrai `tenant_id` do JWT.

---

# Entidades multi-tenant

- users
- clients
- employees
- services
- appointments
- payments
- chatbot

---

# Segurança adicional futura

Possível uso de:

PostgreSQL Row Level Security