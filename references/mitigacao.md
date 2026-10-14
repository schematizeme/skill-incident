# Mitigar antes de diagnosticar

> O usuário não paga pela causa raiz; paga pelo serviço. A primeira pergunta é "como paro o
> sangramento?", não "por que quebrou?".

## 1. A ordem

1. **Estancar**: reduzir o impacto agora, mesmo sem entender. Diagnóstico profundo vem depois.
2. **Reverter o último que mudou** antes de teorizar: deploy, feature flag, config, migração,
   certificado, dependência. `git log`/painel de deploy da última hora é o primeiro lugar a olhar.
3. **Confirmar** pelo sinal do usuário (SLI), não pelo "deploy verde": métrica volta ao normal e
   fica por uma janela (10 min em SEV1/2) antes de declarar mitigado.
4. **Só então** diagnosticar com calma, preservando evidência (logs, dumps, estado) antes de reiniciar.

## 2. Alavancas, da mais barata à mais cara

| Alavanca | Quando | Cuidado |
|---|---|---|
| Desligar **feature flag** | Defeito atrelado a funcionalidade nova | A flag tem de existir antes (kill switch por feature de risco) |
| **Rollback** do deploy | Regressão logo após release | Migração destrutiva não volta: expand-contract evita (`schematize-database`) |
| Escalar / reiniciar | Saturação, vazamento de recurso | Reiniciar destrói evidência: capture antes; e só adia |
| **Desviar tráfego** (failover, região, cache stale) | Dependência fora | Teste de DR já feito (`schematize-infra → references/resiliencia.md`) |
| Degradar com graça | Dependência não essencial | Modo degradado precisa estar desenhado, não improvisado |
| Limitar taxa / bloquear origem | Abuso, tempestade de retry | Registrar a regra para remover depois |
| Rollforward (correção) | Rollback impossível | Só com revisão rápida de 2 pares; é a opção de maior risco |

## 3. Proibido na mitigação

- Ação destrutiva e irreversível (apagar dado, `DROP`, `terraform destroy`, force-push) sem decisão
  explícita do IC registrada. Em prd, o plano de rollback vem **antes** da ação.
- Mexer sem narrar: toda ação no canal antes de executar ("vou reverter X, ok?").
- "Corrigir" mudando várias coisas ao mesmo tempo: uma alavanca por vez, senão não se sabe o que funcionou.
- Disparar efeito externo de verdade para "testar" a correção (e-mail, cobrança, webhook): use o
  sandbox/sink da casa.

## 4. Declarar o fim

Mitigado != resolvido. **Mitigado**: impacto parou. **Resolvido**: causa tratada ou contornada de
forma estável, alertas limpos, status page encerrada, postmortem agendado (SEV1/2: em até 5 dias úteis).

Spam em massa por bot ou token de bot vazado: desligue o bot e revogue o token primeiro; ver `schematize-bots → references/ambientes-e-efeito-externo.md`.
