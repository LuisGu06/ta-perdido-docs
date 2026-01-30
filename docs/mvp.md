# MVP A — Escopo Fechado

## Objetivo
Publicar uma primeira versão em produção (web mobile) para descoberta de **eventos sazonais** e **lugares fixos**, com **submissão pública de conteúdo** e **moderação por admin**.

## Tipos de conteúdo
- **EVENT**: evento sazonal com data de início obrigatória.
- **PLACE**: lugar fixo (restaurantes, hotéis, parques, lazer, natureza etc.).

> “Restaurante”, “hotel”, “parque”, etc. são **categorias**, não tipos.

## Papéis
### Visitante (sem login)
- Listar, buscar, filtrar e ver detalhes de conteúdos publicados.

### Admin
- Revisar submissões pendentes (com imagens).
- Ajustar dados da submissão antes de aprovar (opcional, mas recomendado).
- Aprovar/rejeitar (com motivo).
- Ao aprovar, o conteúdo fica publicado.

## Funcionalidades do MVP
### Público
- Listagem paginada de conteúdos **PUBLISHED**.
- Busca `q` (título + descrição).
- Filtros: `type`, `category`, localização (`country/state/city`) e, para EVENT, `from/to`.
- Página de detalhe com galeria de imagens.

### Submissões (sem login)
- Enviar submissão de EVENT/PLACE com:
  - até **5 imagens**
  - até **5MB** por imagem
  - **sem vídeo**
  - imagem opcional
- Submissões entram como **PENDING**.

### Admin
- Tela dedicada para fila de submissões.
- Aprovar → cria conteúdo **PUBLISHED**.
- Rejeitar → marca **REJECTED** (com motivo).
- Remover imagens inadequadas antes de aprovar.

## Regras de status
### Listing (conteúdo publicado)
- `DRAFT | PUBLISHED | ARCHIVED`
- Visitante vê apenas `PUBLISHED`.

### Submission (submissões)
- `PENDING | APPROVED | REJECTED`

## Imagens (storage)
- Storage S3-compatível: **Cloudflare R2** (MVP).
- Imagens retornam ao front via **URLs assinadas** (TTL padrão: 15 min).
- Listagem retorna apenas **capa**; detalhe retorna **galeria**.

## Fora do MVP (V1/V2)
- Login/cadastro de usuário final.
- Favoritos (será V1).
- Curtidas e comentários (V2).
- Denúncias/relatórios e moderação avançada (V2).
- Busca avançada (full-text ranking, sinônimos etc.).
