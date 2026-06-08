# Sumário executivo — Análise CISPAR (run dos agentes)

> Inventário neutro produzido pelo pipeline de `CLAUDE.md`. O sistema **não gradua
> gravidade** nem decide estratégia — apenas reporta descompassos com carimbo binário,
> para instruir a decisão do usuário (Fase 3, humana). Toda remissão normativa veio
> marcada **"[verificar]"** — confirmar dispositivo e vigência antes de qualquer uso.

## Corpus analisado

| Documento | Páginas | Camada de texto |
|---|---|---|
| 883962.0._EDITAL_1 | 72 | sim |
| 421072_ANEXOS_DO_EDITAL | 200 | sim |
| 951763_MINUTA_DE_CONTRATO_E_ANEXOS (16 anexos) | 557 | sim |
| 885134_Estudos_Socioambientais | 110 | sim |
| 154472_TERMO_ADITIVO_DO_CISPAR | 6 | sim |
| 10344_ESTATUTO_DO_CISPAR | 52 | **scan (sem texto)** — lacuna de corpus |
| 36290_PROTOCOLO_INTENCOES | 30 | **scan (sem texto)** — lacuna de corpus |
| 68264_TERMO_ADITIVO_DO_CONSORCIO | 54 | **scan (sem texto)** — lacuna de corpus |

Os 4 documentos digitalizados não têm camada de texto e não passaram por OCR nesta
rodada — devem ser submetidos a OCR e revarridos para fechar o corpus.

## Resultado

**Fase 1 — Varredura (recall máximo, 175 itens brutos):**

| Agente | Itens |
|---|---|
| Concessão (CONC) | 67 |
| Licitação (LIC) | 32 |
| Gestão Comercial / Riscos (RISC) | 52 |
| Caderno de Encargos (ENC) | 24 |

**Fase 2 — Consolidação (103 itens; 72 fundidos no dedup):**

| Situação | Qtde |
|---|---|
| **IRREGULAR** | 18 |
| **DEPENDE DE FATO** | 18 |
| **CONFORME** | 67 |

As 18 IRREGULAR são todas **contradições internas verificáveis** entre peças de mesmo
nível normativo (divergência numérica, remissão cruzada quebrada, prazos incompatíveis,
divergência de escopo/terminologia), ancoradas no dever de vinculação ao instrumento
convocatório e de clareza. Nenhuma irregularidade foi afirmada por descompasso com norma
externa — como as remissões vieram "[verificar]", sem confirmação de vigência elas caem
em CONFORME (com nota) ou DEPENDE DE FATO, conforme a regra "só IRREGULAR com dispositivo".

## IRREGULAR — 18 contradições internas

| ID | Descompasso |
|---|---|
| C-001 | Inadimplência do MUNICÍPIO: 60 dias (Cl. 22.5) × 90 dias (Anexo 4, 2.9) |
| C-002 | Inadimplência de municípios (RPU): Matriz C.8 aloca à concessionária × 36.17 e Anexo 4 (1.2.5) admitem reequilíbrio |
| C-003 | Força maior: janela de segurabilidade 2 anos (N.1) × 1 ano (N.3) |
| C-004 | Remissão quebrada: 27.2.1 manda reajustar "na forma da cl. 24" (Outorga Fixa; reajuste é a 26) |
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

## DEPENDE DE FATO — 18 itens (premissa externa nomeada em cada um)

Suficiência de prazos da licitação (C-019), requisitos de habilitação econômica/técnica
frente ao mercado (C-020/021), critérios de indenização que remetem a regras da ANA ainda
não editadas (C-022/026), anexos em aberto ou não juntados (C-023 arrolamento, C-024
tarifa-base RSD em branco, C-025 apólices), vinculação a planos não publicados (C-027), e
metas/dimensionamento operacional do Caderno × Estudos (C-028 a C-036). Ver `02_consolidado.md`.

## Próximos passos (Fase 3+, humano)

1. **Filtro do usuário:** priorizar, ponderar gravidade/peso comercial, decidir suscitar
   vs. reservar e selecionar itens para pesquisa.
2. **OCR + revarredura** dos 3 scans (estatuto, protocolo, termo aditivo do consórcio).
3. **Pesquisa targetada (Fase 4):** confirmar vigência dos dispositivos "[verificar]" e
   buscar jurisprudência **apenas** dos itens selecionados (TCU autoritativo).

## Arquivos

- `01_varredura_concessao.md` · `01_varredura_licitacao.md` · `01_varredura_riscos.md` · `01_varredura_encargos.md` — inventários brutos da Fase 1.
- `02_consolidado.md` — 103 itens carimbados (IRREGULAR / DEPENDE DE FATO / CONFORME), com IDs de origem.
