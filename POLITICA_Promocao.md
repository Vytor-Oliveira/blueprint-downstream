# Política de Promoção entre Ambientes

## 1. De Desenvolvimento para Staging (Dev -> Stg)
**Objetivo:** Integração e validação técnica.
- **Critérios:**
  - Pipeline de CI aprovado (Testes, Lint, SAST).
  - Code Review aprovado por 1 desenvolvedor.
  - Cobertura de testes ≥ 70%.
  - Tag de Release Candidate criada (ex: `v1.0.0-rc1`).

## 2. De Staging para Produção (Stg -> Prod)
**Objetivo:** Entrega de valor ao usuário final.
- **Critérios:**
  - Testes E2E (Smoke) passaram em Staging.
  - Aprovação do PO (se houver mudança funcional).
  - Janela de Deploy respeitada (fora de horários de congelamento/freeze).
  - Plano de Rollback validado (Runbook pronto).

## 3. Evidências
- Todo deploy deve ter link para o commit, status do pipeline e aprovações registradas no Pull Request.