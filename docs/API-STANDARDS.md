# API Standards

Este documento define os padrões da API da RomaWorks Platform.

---

# Padrão de rotas

Formato:


/api/v1/resource


Exemplo:


GET /api/v1/clients
POST /api/v1/clients
GET /api/v1/clients/:id


---

# Padrão de resposta

Sucesso

```json
{
    "data": {},
    "meta": {}
}
```

Erro

```json
{
    "error": {
        "code": "CLIENT_NOT_FOUND",
        "message": "Client not found"
    }
}
```


---

# Paginação

Formato:


GET /clients?page=1&limit=20


Resposta:


meta:
page
limit
total


---

# Validação

Toda entrada deve usar DTO + validation.

---

# Autenticação

Header obrigatório:


Authorization: Bearer (JWT)