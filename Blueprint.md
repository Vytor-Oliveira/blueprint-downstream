# Blueprint do Downstream — Projeto Exemplo

## 1. Contexto & Git (Previsibilidade)
- **Fluxo:** Trunk-Based Development leve (branches curtas).
- **Branches:** `main` (prod), `staging` (homologação), `dev` (integração), `feat/xyz` (trabalho).
- **Commits:** Padrão Conventional Commits (ex: `feat:`, `fix:`, `chore:`).
- **Quality Gates (Bloqueiam Merge):**
  - CI aprovado (Lint + Testes).
  - Cobertura de código ≥ 70%.
  - SAST sem vulnerabilidades HIGH ou CRITICAL.
  - Revisão de código (Code Review) aprovada por 1 par.

## 2. Qualidade & Testes (Pirâmide)
- **Unitários (70%):** Jest (foco em regras de negócio isoladas).
- **Integração (20%):** Testes de API e Banco de dados em containers.
- **E2E (10%):** Smoke test em Staging para validar fluxos críticos.
- **Lint/SAST:** ESLint (estilo) e CodeQL/SonarQube (segurança). Bloqueiam o pipeline se falharem.

## 3. CI/CD & Pipeline
- **Pipeline Mínimo:** `Install` -> `Lint` -> `Test` -> `Coverage` -> `SAST` -> `Build`.
- **Artefato:** Imagem Docker imutável gerada no estágio de Build.

## 4. Releases & Rollback
- **Estratégia:** Canary Release (liberação gradual: 10% -> 50% -> 100%).
- **Gatilhos de Rollback:**
  - Taxa de erro 5xx ≥ 2% por 5 minutos.
  - Latência p95 ≥ 600ms.
- **Plano de Ação:** Reverter para a tag Docker anterior via `kubectl` ou painel de CD.

## 5. Observabilidade & DORA
- **Logs:** Estruturados (JSON) contendo `correlation-id` e `stacktrace`.
- **Métricas:** Taxa de erros (5xx) e Latência (p95).
- **DORA Metrics (Mensal):**
  - *Lead Time:* Tempo do commit até produção.
  - *Change Failure Rate:* % de deploys que exigiram rollback.
- **PDCA:** Reunião quinzenal para revisar métricas DORA e incidentes, gerando ações de melhoria (Kaizen).