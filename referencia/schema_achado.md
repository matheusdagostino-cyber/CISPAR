# schema_achado.md — Contrato de saída da varredura

Todo item da Fase 1 (varredura) é emitido **exatamente** nestes campos. A disciplina do formato é o principal freio ao excesso: campo vazio denuncia item fraco.

A varredura reporta o **descompasso de forma factual** (trecho + descrição + dispositivo). Ela **não carimba** a Situação — quem carimba é a consolidação (Fase 2), para manter um critério único entre os quatro agentes.

## Campos

|Campo           |Conteúdo                                                                                                 |Quem preenche         |
|----------------|---------------------------------------------------------------------------------------------------------|----------------------|
|**ID**          |Sequencial por agente: `CONC-001`, `LIC-001`, `RISC-001`, `ENC-001`                                      |Varredura             |
|**Localização** |Peça + cláusula/item + página (ex.: “Minuta de contrato, cl. 12.4, p. 63”)                               |Varredura             |
|**Trecho**      |Citação literal e curta do edital/anexo                                                                  |Varredura             |
|**Descrição**   |O descompasso, em linguagem **factual e neutra**. Sem adjetivo de gravidade ou de magnitude.             |Varredura             |
|**Dispositivo** |Norma em descompasso, **com artigo** (ex.: “Lei 14.133/2021, art. 22, §3.º”). Obrigatório para IRREGULAR.|Varredura             |
|**Base factual**|`[consta dos autos]` ou `[depende de fato externo — especificar a premissa]`                             |Varredura             |
|**Situação**    |IRREGULAR / CONFORME / DEPENDE DE FATO (ver `teste_irregularidade.md`)                                   |**Só na consolidação**|

## Regra “só IRREGULAR com dispositivo”

Se não há **dispositivo vigente nomeado** em descompasso, não há irregularidade a afirmar. O item vira CONFORME (com nota, se relevante) ou DEPENDE DE FATO. O LLM infla justamente quando não precisa se comprometer com uma norma — forçar o campo “Dispositivo” corta isso na origem.

## Regra “Base factual”

Restritividade, direcionamento, suficiência de prazo, viabilidade — quase sempre **dependem de fato externo**. Nesses casos: `[depende de fato externo]` + a premissa, e a Situação será **DEPENDE DE FATO**. **Nunca** afirmar como fato (ex.: “exigência restritiva”) aquilo que depende de dado não constante dos autos (ex.: quantas empresas atendem).

## Modelo em branco

```
ID:            [____-000]
Localização:   [peça, cláusula/item, página]
Trecho:        "[citação literal curta]"
Descrição:     [descompasso, factual e neutro]
Dispositivo:   [Lei/Decreto, art. XX, § Y.º, inc. Z]  |  [não localizado]
Base factual:  [consta dos autos] | [depende de fato externo: ___]
--- consolidação ---
Situação:      [IRREGULAR | CONFORME | DEPENDE DE FATO]
```