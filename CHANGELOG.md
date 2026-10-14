# Changelog — schematize-incident

Todas as mudanças relevantes deste pacote, no formato [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/),
com versionamento [SemVer](https://semver.org/lang/pt-BR/).

## [0.1.0] — 2026-10-14
Primeira versão. Faltava a dona do ciclo humano do incidente: a observabilidade detecta, a infra recupera, mas
ninguém mandava classificar, comandar, comunicar, tratar dado pessoal e aprender. O incidente dos 5.000 e-mails
(2026-08) mostrou o custo de fechar incidente com conselho em vez de ADR + piso + gate.

### Adicionado
- `SKILL.md` com 12 pisos, fronteira com observability/infra/docs/archive/pentest/iam e 9 comandos `/inc-*`.
- `references/`: severidade (SEV1-4), papéis e comando, mitigação, comunicação, LGPD/ANPD, postmortem blameless, recorrência e anexo volátil.
- `scripts/check-postmortem.sh` (+ teste com 16 casos, vermelhos plantados): seções, timeline, mitigação, impacto numérico, porquês, dono e prazo nas ações, linguagem de culpa, decisão LGPD/ANPD; waiver `inc-ok`.
- `assets/templates/`: postmortem, timeline viva, atualização de status.
