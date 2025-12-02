# Runbook de Rollback

## Gatilhos (Quando acionar o rollback)
Inicie este procedimento IMEDIATAMENTE se, nos primeiros 15 minutos após o deploy:
1. **Taxa de Erros:** Respostas 5xx excederem 2% do total.
2. **Latência:** O tempo de resposta p95 exceder 600ms.
3. **Funcional:** Falha crítica no login ou checkout (Smoke Test falhou).

## Procedimento de Rollback (Passo a Passo)

### Passo 1: Estancar o sangramento
- Se usar **Feature Flag**: Desligue a flag associada à nova feature no painel de controle.
- Se for **Canary Release**: Zere o tráfego da versão nova (peso 0%).

### Passo 2: Reverter a Versão
1. Identifique a versão estável anterior (ex: `v1.2.0`).
2. Execute o comando de revert no orquestrador:
   ```bash
   kubectl rollout undo deployment/minha-app
   # OU reimplante a tag da imagem Docker anterior