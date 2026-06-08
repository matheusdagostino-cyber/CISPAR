# consolidacao.md — Agente de consolidação (Fase 2, passe único)

Lê em conjunto com `CLAUDE.md`, `referencia/teste_irregularidade.md` e
`referencia/schema_achado.md`.

## Entrada

Os 4 inventários da Fase 1 (CONC, LIC, RISC, ENC).

## Faz, nesta ordem

1. **Dedup por cláusula.** A mesma cláusula apontada por vários agentes vira **um**
   item. Preservar todos os IDs de origem como referência cruzada.
2. **Consistência interna.** Contradições entre peças (corpo × anexos × minuta ×
   planilhas × estudos). É aqui que vive o antigo "Erros/Inconsistências".
3. **Carimbo da Situação** — para cada item, exatamente um:
   - **IRREGULAR** — descompasso direto e verificável com dispositivo vigente
     **nomeado, com artigo**.
   - **CONFORME** — verificado, sem descompasso; ou ponto sem norma em questão.
   - **DEPENDE DE FATO** — só se resolve com fato fora dos autos (nomear a premissa).

## Não faz

- Não gradua gravidade nem magnitude.
- Não sinaliza "suscitar" nem "reservar" (Fase 3, humano).
- Não cita jurisprudência (Fase 4).
- Não cria irregularidade a partir de premissa não confirmada → `DEPENDE DE FATO`.

## Saída

Tabela/lista consolidada no schema de `referencia/schema_achado.md` **com** o campo
`Situação` preenchido, agrupada por Situação, com contagem final por estado.
