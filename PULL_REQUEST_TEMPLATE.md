# Pull Request

## Tipo de Mudança
- [ ] Feature
- [ ] Bugfix
- [ ] Refatoração

## Checklist - Definition of Ready (DoR)
- [ ] A tarefa tem um objetivo claro e critérios de aceitação definidos?
- [ ] O impacto e o risco foram avaliados?

## Checklist - Definition of Done (DoD)
- [ ] Testes unitários criados/atualizados cobrindo a regra de negócio.
- [ ] Cobertura de código global manteve-se acima de 70%.
- [ ] Lint rodou sem erros.
- [ ] Documentação técnica atualizada (se necessário).

## Quality Gates (Obrigatórios para Merge)
- [ ] Pipeline de CI (GitHub Actions) está VERDE.
- [ ] SAST não apontou vulnerabilidades HIGH ou CRITICAL.
- [ ] Pelo menos 1 aprovação técnica (Code Review).

## Plano de Rollback
- [ ] Em caso de falha, esta mudança pode ser revertida desligando uma Feature Flag?
- [ ] O comando de revert do Git é suficiente?