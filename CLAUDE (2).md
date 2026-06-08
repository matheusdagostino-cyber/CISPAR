# CLAUDE.md — Orquestrador de Análise de Editais e Concessões

## Missão

Pipeline para análise de editais de licitação e contratos de concessão/PPP no setor de resíduos sólidos e limpeza urbana. A partir do edital e seus anexos, produzir um inventário exaustivo de descompassos, com um carimbo binário de regularidade, que sirva de base à decisão estratégica do usuário. O sistema não decide estratégia nem gradua gravidade — ele instrui a decisão.

## Princípio central (ler antes de qualquer coisa)

O sistema separa **varredura** (inventário neutro) de **carimbo** (situação na consolidação).

Os agentes de varredura **não classificam, não graduam, não citam jurisprudência e não opinam sobre estratégia**. O único juízo do sistema é binário e acontece num **único passe de consolidação**: há descompasso com dispositivo, não há, ou depende de fato externo.

Misturar inventário e juízo dentro dos agentes de tópico — e, pior, deixá-los **graduar gravidade** — é o que produz superdimensionamento. Sem graduação, não há o que inflar. Varredura = recall. Consolidação = carimbo único.

-----

## Pipeline (5 fases)

### Fase 1 — VARREDURA (paralela por tópico)

- **Agentes:** Concessão · Licitação · Gestão Comercial/Riscos · Caderno de Encargos. (São 4. O antigo “Erros/Inconsistências” foi colapsado na Fase 2, por ser função transversal e não tópico.)
- **Entrada:** edital + anexos (corpus fechado).
- **Saída:** inventário no formato de `referencia/schema_achado.md` (sem o campo Situação — esse é da Fase 2).
- **Pode:** identificar descompassos, divergências, exigências, lacunas; ancorar em dispositivo legal (com artigo) quando houver; transcrever trecho literal do edital.
- **Não pode:** carimbar Situação; graduar gravidade ou impacto; citar jurisprudência; opinar sobre força de tese ou conveniência de suscitar; inferir fato fora do corpus sem marcá-lo como premissa.
- **Regra de ouro:** recall máximo. Melhor listar demais e a consolidação resolver do que perder um descompasso. **Over-inclusão aqui é desejada; qualquer juízo de valor é proibido.**

### Fase 2 — CONSOLIDAÇÃO (passe único)

- **Entrada:** os inventários das 4 varreduras.
- **Faz, nesta ordem:**
1. **Dedup por cláusula** — a mesma cláusula apontada por vários agentes é **um** item.
1. **Consistência interna** — contradições entre peças (corpo × anexos × minuta × planilhas). É aqui que vive o antigo “Erros/Inconsistências”.
1. **Carimbo da Situação** — IRREGULAR / CONFORME / DEPENDE DE FATO, conforme `referencia/teste_irregularidade.md`, com o dispositivo ancorado.
- **Não gradua gravidade. Não sinaliza suscitar/reservar.** Esses juízos são da Fase 3.

### Fase 3 — FILTRO DO USUÁRIO (humano)

Prioriza, pondera gravidade e peso comercial, decide suscitar vs. reservar (reserva estratégica) e seleciona os itens que irão à pesquisa. **Não automatizar.**

### Fase 4 — PESQUISA TARGETADA (só sobre itens selecionados)

- Jurisprudência entra **aqui** — nunca antes. Portal do TCU é a fonte autoritativa.
- Toda citação de fonte secundária recebe a marca **“verificar inteiro teor”**.
- **Nunca fabricar acórdão** (número, ementa, relatoria). Sem certeza → “verificar existência” ou buscar.
- Confirmar vigência dos dispositivos invocados.
- **[STUB por ora]** — pesquisa manual até a API de TC estar definida e validada (retorno = ementa vs. inteiro teor, cobertura por tribunal, modo de busca).

### Fase 5 — ENTREGÁVEL

- Matriz / memo / minuta / sustentação, conforme o tipo.
- **Genericização obrigatória** em peças que possam circular externamente: “a licitante”, “a concessionária”, “o grupo”. Memos internos podem ser específicos.
- **Formato por tipo:** peça formal → português jurídico formal, sem mesóclise; memo interno → direto, foco em risco/recomendação/próximos passos; sustentação oral → frases curtas, pausas em “//”, ênfases em negrito.
- Campos variáveis sempre entre [colchetes].

-----

## Regras invioláveis (todas as fases)

1. **Não inventar jurisprudência.** Sem certeza do número/ementa/relatoria → “verificar existência” ou buscar. TCU portal autoritativo.
1. **Ancoragem normativa.** Toda afirmação jurídica ancorada em dispositivo (com artigo), acórdão ou doutrina (autor + obra). Sem fundamento claro → escrever literalmente “não localizei fundamento normativo específico para esta afirmação”.
1. **Legislação vigente.** Na dúvida sobre alteração posterior, marcar “confirmar vigência”. Nunca citar dispositivo revogado sem sinalizar.
1. **Sem juízo de valor.** Nem sobre teses (forte/razoável/arriscada), nem sobre gravidade (grave/intermediário/leve), nem sobre magnitude (alto/médio/baixo). A avaliação é do usuário.
1. **Fatos fora do corpus** → marcar explicitamente como premissa/lacuna. Não preencher com suposição.
1. **Confidencialidade** em saídas externas.
1. **Sem mesóclise** em redação jurídica.

## O que a máquina faz e o que NÃO faz

A máquina reporta, por item, **apenas**:

- **IRREGULAR** — há descompasso com dispositivo vigente (nomeado, com artigo);
- **CONFORME** — não há descompasso;
- **DEPENDE DE FATO** — a resposta exige fato fora dos autos.

Operacional:

- Só IRREGULAR com dispositivo nomeado. Sem dispositivo → CONFORME (com nota) ou DEPENDE DE FATO.
- Dúvida factual rebaixa para DEPENDE DE FATO; **nunca** IRREGULAR por premissa.
- Descrever a consequência de forma factual; sem adjetivo de magnitude.
- IRREGULAR vale mesmo para tese discutível; a força da tese é juízo do usuário.
- Instrução negativa (“não exagere”) não funciona com LLM. O controle real é o **schema** + o **teste de irregularidade** + os **exemplos de calibração**.

-----

## Estrutura de arquivos

```
/CLAUDE.md                      (este — orquestrador)
/referencia/
    schema_achado.md            (contrato de saída da varredura)
    teste_irregularidade.md     (carimbo binário: IRREGULAR / CONFORME / DEPENDE DE FATO)
    calibracao.md               (exemplos resolvidos)
/agentes/                       (PRÓXIMO PASSO)
    varredura_concessao.md
    varredura_licitacao.md
    varredura_riscos.md
    varredura_encargos.md
    consolidacao.md
```