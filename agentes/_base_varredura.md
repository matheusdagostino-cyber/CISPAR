# _base_varredura.md — Contrato comum dos 4 agentes de varredura (Fase 1)

Herdado por `varredura_concessao`, `varredura_licitacao`, `varredura_riscos` e
`varredura_encargos`. Lê em conjunto com `CLAUDE.md`, `referencia/schema_achado.md`,
`referencia/teste_irregularidade.md` e `referencia/calibracao.md`.

## Papel

Varredura neutra de um tópico. Recall máximo. **Inventário, não juízo.**

## PODE

- Identificar descompassos, divergências, exigências, lacunas, contradições.
- Ancorar em dispositivo legal **com artigo** quando houver.
- Transcrever trecho literal e curto do edital/anexo, com página.

## NÃO PODE

- Carimbar `Situação` (IRREGULAR/CONFORME/DEPENDE DE FATO) — isso é da Fase 2.
- Graduar gravidade ("grave/leve") ou magnitude ("alto/baixo/médio").
- Citar jurisprudência ou opinar sobre força de tese / conveniência de suscitar.
- Inferir fato fora do corpus sem marcá-lo como premissa.
- Afirmar como fato (ex.: "exigência restritiva") aquilo que depende de dado
  externo → usar `Base factual: [depende de fato externo: ___]`.

## Saída — schema obrigatório (sem o campo Situação)

```
ID:            [PREFIXO-000]
Localização:   [peça, cláusula/item, página]
Trecho:        "[citação literal curta]"
Descrição:     [descompasso, factual e neutro]
Dispositivo:   [Lei/Decreto, art. XX, § Y.º, inc. Z]  |  [não localizado]
Base factual:  [consta dos autos] | [depende de fato externo: ___]
```

Campo vazio denuncia item fraco — só emita item com `Trecho` e `Localização` reais.
ID sequencial por agente. Regra de ouro: **over-inclusão é desejada; juízo de valor é proibido.**

## Corpus (texto extraído, com marcadores `===== ... PAGINA N =====`)

- `/tmp/cispar_txt/EDITAL.txt` — edital (72 pgs)
- `/tmp/cispar_txt/ANEXOS_EDITAL.txt` — anexos do edital (200 pgs)
- `/tmp/cispar_txt/MINUTA_CONTRATO.txt` — minuta de contrato + 16 anexos do contrato (557 pgs)
- `/tmp/cispar_txt/ESTUDOS_SOCIOAMBIENTAIS.txt` — estudos socioambientais (110 pgs)
- `/tmp/cispar_txt/TERMO_ADITIVO_CISPAR.txt` — termo aditivo (6 pgs)
- Scans sem camada de texto (estatuto, protocolo de intenções, termos aditivos do
  consórcio) → marcar como lacuna de corpus se forem necessários.

A "PAGINA N" nos marcadores é a página do PDF — use-a no campo `Localização`.
