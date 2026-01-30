# Roadmap

## MVP
**Objetivo:** colocar no ar um catálogo funcional de EVENT e PLACE com submissões públicas e moderação.

- Catálogo público (sem login): listagem, busca, filtros, detalhe
- Tipos: EVENT (start_at obrigatório) e PLACE
- Submissões sem login com 0–5 imagens (5MB, sem vídeo)
- Admin: fila de submissões + approve/reject + edição antes de aprovar
- Storage: Cloudflare R2 (S3-compatible) + URLs assinadas (TTL 15 min)
- Paginação e ordenação básica
- Rate limit + cleanup de imagens (submissões rejeitadas)

## V1 (pós-MVP)
**Objetivo:** aumentar retenção e qualidade operacional.

- Cadastro/login de usuário final
- Favoritos
- Acompanhamento de submissões pelo usuário
- Melhorias de busca (ex.: ordenação melhor, filtros adicionais)
- Observabilidade básica melhorada (dashboards, alertas simples)

## V2
**Objetivo:** engajamento e recursos sociais.

- Curtidas e comentários
- Denúncias/report + moderação avançada
- Geolocalização “perto de mim” (se fizer sentido)
- Notificações

## Fora do escopo (por enquanto)
- Marketplace/monetização
- Parceiros (role PARTNER)
- App nativo (depende do sucesso do web)
