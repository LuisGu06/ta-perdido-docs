# Tá Perdido — Docs

Repositório público de documentação do projeto **Tá Perdido** (TCC → produto real).

O Tá Perdido é um app (web mobile inicialmente) para **descobrir eventos sazonais e lugares fixos** (restaurantes, parques, hotéis, lazer, natureza etc.), com **submissão de conteúdo pela comunidade** e **moderação por admin**.

> Este repositório contém **apenas documentação** (arquitetura, requisitos, contratos de API, diagramas e protótipos).  
> O código-fonte (backend e frontend) fica em repositórios privados.

## MVP (versão atual planejada)

### Público (sem login)
- Listar / buscar / filtrar itens publicados
- Ver detalhes do item (incluindo imagens)

### Submissões (sem login)
- Enviar sugestão de evento/lugar com até **5 imagens** (até **5MB** cada)
- As submissões ficam **pendentes** até revisão do admin

### Admin
- Tela dedicada para revisar submissões
- Aprovar/rejeitar (com motivo)
- Ao aprovar, o item é publicado

## Stack (backend)
- Java + Spring Boot
- PostgreSQL
- Storage S3-compatible: **Cloudflare R2**
- Imagens servidas via **URLs assinadas** (TTL padrão: 15 min)

## Documentos
- `docs/mvp.md` — escopo do MVP e regras de negócio
- `docs/architecture.md` — visão arquitetural (monólito modular)
- `docs/api/openapi.yaml` — contrato da API (fonte de verdade do front)
- `docs/roadmap.md` — MVP → V1 → V2
- `docs/ui/` — protótipos (PDF)
- `docs/diagrams/` — diagramas (DER / casos de uso / atividades)

## Como contribuir
Este repositório é focado em documentação. Sugestões via Issues/PRs são bem-vindas.
