# schematize-incident — resposta a incidente

> **Comande, mitigue, comunique, aprenda, feche a porta.** Severidade SEV1-4 por critério objetivo,
> papéis (IC, comms, ops, escriba), mitigar antes de diagnosticar, LGPD/ANPD quando há dado pessoal,
> postmortem blameless e incidente recorrente virando ADR + piso + gate.

Pacote de **skill normativa para [Claude Code](https://claude.com/claude-code)**.
Parte do catálogo **schematize skills**.

## Por que ela existe

A `schematize-observability` detecta e alerta; a `schematize-infra` recupera. Faltava o meio: quem manda,
o que se diz ao cliente, quando a ANPD entra, e como o aprendizado vira regra de máquina e não conselho.

## Instalar

### Pelo app schematize (recomendado)

```bash
schematize install incident    # requer o CLI schematize instalado
```

### Manual

```bash
git clone https://github.com/schematizeme/skill-incident.git /tmp/skill-incident
bash /tmp/skill-incident/install.sh .        # instala em .claude/ do projeto atual
```

## O que tem dentro

- **SKILL.md** — o contrato: 12 pisos inegociáveis, a fronteira com as skills vizinhas e o mapa de references.
- **references/** — severidade, papéis e comando, mitigação, comunicação, LGPD, postmortem, recorrência e anexo volátil (com data e fonte).
- **scripts/** — `check-postmortem.sh`, o gate do postmortem (funciona só com bash; exit 2 = nada verificado), e seu teste.
- **assets/** — templates (postmortem, timeline, status), `CLAUDE.md` sempre-on e comandos `/inc-*`.

## Licença

MIT. Veja `LICENSE`.
