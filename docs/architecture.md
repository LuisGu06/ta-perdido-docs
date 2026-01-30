# Arquitetura — Baseline (MVP A)

> Este documento descreve a arquitetura **planejada** para o MVP.  
> Ele será atualizado conforme a implementação evoluir.

## Visão geral
- Frontend: **React (web mobile)** consumindo API REST versionada (`/v1`)
- Backend: **Java + Spring Boot** (monólito modular)
- Banco: **PostgreSQL**
- Storage de imagens: **Cloudflare R2** (S3-compatible)
- Entrega de imagens: **URLs assinadas** (TTL padrão: 15 min)

## Estilo arquitetural
**Monólito modular** para reduzir complexidade operacional no MVP e acelerar entrega.
Separação em camadas:
- API (Controllers/DTO/Validation)
- Application (casos de uso/serviços)
- Domain (entidades e regras de negócio)
- Infra (JPA, Storage S3, Security, Jobs)

## Módulos do domínio (MVP A)
1) **Catalog (Public)**
- Listagem/detalhe de conteúdos `PUBLISHED`
- Busca/filtros/paginação

2) **Submissions (Public)**
- Recebe submissões sem login
- Salva imagens no bucket de submissões (R2)

3) **Moderation (Admin)**
- Fila de submissões `PENDING`
- Admin ajusta dados e remove imagens
- Approve → cria conteúdo `PUBLISHED` e promove imagens
- Reject → marca `REJECTED` (com motivo)

4) **Media/Storage**
- Upload (multipart) → bucket `submissions`
- Promoção (copy+delete) → bucket `public`
- Geração de URL assinada para leitura

## Contratos e padrões
- API versionada: `/v1`
- Paginação padrão: `page`, `size`, retorno com `items`, `page`, `size`, `total`
- Listagem retorna somente **capa** (signed URL)
- Detalhe retorna **galeria** (signed URLs)

## Segurança (MVP A)
- Público: somente leitura + submissão
- Admin: JWT (apenas para rotas `/v1/admin/**`)
- CORS restrito ao domínio do front

## Evolução (MVP B)
- Adicionar usuário final (cadastro/login)
- Favoritos (tabela já prevista)
- `submissions.submitted_by_user_id` passa a ser preenchido
