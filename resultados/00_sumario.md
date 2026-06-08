# Sumário executivo — Análise CISPAR (run completo dos agentes)

> Inventário neutro produzido pelo pipeline de `CLAUDE.md`. O sistema **não gradua
> gravidade** nem decide estratégia — apenas reporta descompassos com carimbo binário,
> para instruir a decisão do usuário (Fase 3, humana). Toda remissão normativa veio
> marcada **"[verificar]"** — confirmar dispositivo e vigência antes de qualquer uso.

## Corpus analisado (completo — 8 documentos, ~1.081 páginas)

| Documento | Páginas | Texto |
|---|---|---|
| 883962.0._EDITAL_1 | 72 | nativo |
| 421072_ANEXOS_DO_EDITAL | 200 | nativo |
| 951763_MINUTA_DE_CONTRATO_E_ANEXOS (16 anexos) | 557 | nativo |
| 885134_Estudos_Socioambientais | 110 | nativo |
| 154472_TERMO_ADITIVO_DO_CISPAR | 6 | nativo |
| 10344_ESTATUTO_DO_CISPAR | 52 | **OCR** (pt, 300 dpi) |
| 36290_PROTOCOLO_INTENCOES | 30 | **OCR** (pt, 300 dpi) |
| 68264_TERMO_ADITIVO_DO_CONSORCIO | 54 | **OCR** (pt, 300 dpi) |

Os 3 documentos digitalizados foram OCR-ados nesta rodada e integrados ao corpus
(`corpus_texto/`). Trechos com ruído de OCR foram marcados para conferência no original
e, na consolidação, rebaixados para DEPENDE DE FATO (nunca IRREGULAR isolada por OCR).

## Resultado

**Fase 1 — Varredura (recall máximo, 197 itens brutos):**

| Agente | Itens |
|---|---|
| Concessão (CONC) | 67 |
| Gestão Comercial / Riscos (RISC) | 52 |
| Licitação (LIC) | 32 |
| Caderno de Encargos (ENC) | 24 |
| Institucional / Governança (INST) | 22 |

**Fase 2 — Consolidação (120 itens; 77 fundidos no dedup):**

| Situação | Qtde |
|---|---|
| **IRREGULAR** | 22 |
| **DEPENDE DE FATO** | 25 |
| **CONFORME** | 73 |

As IRREGULAR são todas **contradições internas verificáveis** entre peças vinculantes de
mesmo nível normativo (divergência numérica, remissão cruzada quebrada, prazos
incompatíveis, divergência de escopo/terminologia, listas de entes divergentes),
ancoradas no dever de vinculação ao instrumento convocatório / clareza e no regime dos
consórcios. Nenhuma irregularidade foi afirmada por descompasso com norma externa — como
as remissões vieram "[verificar]", sem confirmação de vigência caem em CONFORME (com
nota) ou DEPENDE DE FATO, conforme a regra "só IRREGULAR com dispositivo".

## IRREGULAR — 22 contradições internas

**Contrato / Anexos (C-001 a C-018):**

| ID | Descompasso |
|---|---|
| C-001 | Inadimplência do MUNICÍPIO: 60 dias (Cl. 22.5) × 90 dias (Anexo 4, 2.9) |
| C-002 | Inadimplência de municípios (RPU): Matriz C.8 aloca à concessionária × 36.17 e Anexo 4 (1.2.5) admitem reequilíbrio |
| C-003 | Força maior: janela de segurabilidade 2 anos (N.1) × 1 ano (N.3) |
| C-004 | Remissão quebrada: 27.2.1 reajusta "na forma da cl. 24" (Outorga Fixa; reajuste é a 26) |
| C-005 | Remissão quebrada: 34.4 executa garantias na ordem da "31.3" (sede da SPE; modalidades estão na 34.3) |
| C-006 | Remissão quebrada: 35.11.1 cita "subcláusula 35.10.1" inexistente |
| C-007 | Divergência numérica: TBR de Arapuá "2,867" × TBM "2,8567" (Quadro 39) |
| C-008 | Autoridade recursal: 17.3 (Presidente do CISPAR) × 17.3.1 (Comissão Especial) |
| C-009 | Coleta seletiva de orgânicos: "84 meses" (Quadro 5) × "85º mês" (marcos) |
| C-010 | Prazo de 120 dias: Plano de Operacionalização (Quadro 4) × Plano de Execução Contratual (6.3.2) |
| C-011 | Novo aterro: "48 meses" (Quadro 5) × "49º mês" (marcos) |
| C-012 | Triagem mecanizada/UVR: "24 meses" (Quadro 5) × "25º mês" (marcos) |
| C-013 | PRAD: cronograma manda "executar" × Apêndice A.B atribui execução aos municípios |
| C-014 | Numeração repetida no item 6.3 (dois "6.3.2.1" etc.) |
| C-015 | Catadores: texto "pelo menos 7" × Quadro 20 "Total 76" |
| C-016 | Anexo 15 (UTR) × Caderno 6.2.f remete ao "Anexo 19"; capa ainda "DOCOMENTOS" |
| C-017 | Sigla "UTL" (Anexo 3, 7.8) × "UTR" no restante |
| C-018 | Anexo 16: "RECEITAS ACESSÓRIAS" × "RECEITAS EXTRAORDINÁRIAS" |

**Institucional / consórcio (C-104 a C-107):**

| ID | Descompasso |
|---|---|
| C-104 | Lista de consorciados 18 (Protocolo/Estatuto) × 19 (Termo Aditivo): inserção de João Pinheiro |
| C-105 | Lacuna na numeração dos Contratos de Programa (salto 006 → 008, sem 007) |
| C-106 | Estatuto art. 8º §1º IX (inclui "prestação") × art. 10 (só estudo/planejamento/fiscalização/regulação) |
| C-107 | Marco do prazo de 2 anos de ratificação: Estatuto (publicação da Ata) × Protocolo (1ª subscrição) |

## DEPENDE DE FATO — 25 itens (premissa/documento externo nomeado)

Inclui as **lacunas da cadeia de competência** levantadas pela camada institucional, que
merecem atenção prioritária na Fase 3:

| ID | Premissa/documento faltante |
|---|---|
| C-108 | "2º Termo Aditivo" (delegação do SMRSU) invocado pelo edital, **ausente do corpus** |
| C-109 | Só 9 de 19 municípios com lei de ratificação do SMRSU; demais não constam |
| C-111 | Status "projeto/minuta" × "aditivo assinado": ata e leis ratificadoras de 2023 ausentes |
| C-112 | Convênio CISPAR–ARISB e ato de indicação pela Assembleia não juntados |
| C-113 | Resolução CISPAR nº 01/2023, invocada pelo edital, ausente do corpus |
| C-110, C-114 | Trechos OCR (rateio de Varjão; assinaturas de Pirapora/Paracatu) — conferir no original |

Os demais (C-019 a C-036) tratam de suficiência de prazos da licitação, requisitos de
habilitação frente ao mercado, critérios de indenização que remetem a regras da ANA ainda
não editadas, anexos em aberto/não juntados, e metas/dimensionamento do Caderno × Estudos.
Ver `02_consolidado.md` para o detalhamento completo.

## Próximos passos (Fase 3+, humano)

1. **Filtro do usuário:** priorizar, ponderar gravidade/peso comercial, decidir suscitar
   vs. reservar e selecionar itens para pesquisa.
2. **Pesquisa targetada (Fase 4):** confirmar vigência dos dispositivos "[verificar]" e
   buscar jurisprudência **apenas** dos itens selecionados (TCU autoritativo).
3. **Lacunas de corpus:** requerer ao consórcio os documentos ausentes nomeados nos itens
   DEPENDE DE FATO (2º Termo Aditivo, Resolução 01/2023, convênio ARISB, leis ratificadoras).

## Arquivos

- `01_varredura_concessao.md` · `01_varredura_licitacao.md` · `01_varredura_riscos.md` · `01_varredura_encargos.md` · `01_varredura_institucional.md` — inventários brutos da Fase 1.
- `02_consolidado.md` — 120 itens carimbados (IRREGULAR / DEPENDE DE FATO / CONFORME), com IDs de origem cruzados.
