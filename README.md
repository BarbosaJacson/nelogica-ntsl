# Algoritmos de Execução e Indicadores Quantitativos (NTSL)

## 📈 Trajetória e Motivação
Minha jornada no mercado financeiro começou em **2013**. Desde os primeiros anos operando, ficou evidente que o maior desafio para a consistência não estava apenas na leitura gráfica, mas no controle da carga emocional durante a tomada de decisão.

A busca por disciplina operacional me levou naturalmente à programação e à automação de processos: iniciei desenvolvendo alarmes simples e regras de coloração para auxiliar na leitura objetiva do preço e, com a evolução técnica, passei a construir robôs completos de execução automatizada. Este repositório reúne parte dessa evolução aplicada à linguagem **NTSL (Nelogica Trading System Language)**.

## 🤝 Código Aberto e Propósito Educacional
Os algoritmos aqui disponíveis são de **código aberto** para a comunidade de traders e desenvolvedores que desejam estudar lógica de programação aplicada ao mercado financeiro, compreender regras de negócio em NTSL, realizar backtests e adaptar parâmetros aos seus próprios estudos.

> ⚠️ **Aviso de Responsabilidade (Disclaimer):** Como autor destes códigos, **não recomendo** a utilização de nenhuma estratégia deste repositório em conta real sem antes realizar a devida parametrização para o ativo desejado e conduzir testes rigorosos (incluindo simulações *tick a tick* e Replay de Mercado) na plataforma Profit da Nelogica. Resultados passados em testes históricos não garantem rentabilidade futura.

---

## 📂 Estrutura do Repositório

- \/estrategias\: Robôs de execução com regras completas de entrada, condução de trade e gestão de risco.
- \/indicadores\: Indicadores customizados e filtros de sinal.
- \/docs\: Documentação de parâmetros e resultados de validação.

---

## ⚙️ Estratégias Disponíveis

### 1. \wdo_scalp_MM.ntsl\ — Pullback com Realismo de Fila (Mini Dólar)
A nomenclatura **MM (Máximas e Mínimas)** reflete a mecânica central de posicionamento e gatilho do algoritmo: a estratégia opera tomando como referência as **mínimas dos últimos candles** e as **máximas dos candles seguintes** para identificar pontos de inflexão e rompimento em movimentos de pullback.

* **Referência de Máximas e Mínimas (MM):** Monitora extremos recentes (\HighestHigh\ e \LowestLow\) para ancorar níveis de entrada e saída.
* **Filtro de Tendência e Volatilidade:** Combina Média Móvel Exponencial (\PeriodoMedia\) com múltiplos de *True Range* (\FatorTR\) para delimitar o túnel de volatilidade.
* **Realismo de Fila (Backtest):** Aplica deslocamento de preço (\Offset\) nas ordens limite para simular a perda de prioridade no livro de ofertas durante testes históricos.

---

### 2. \MM_D_2026.ntsl\ — Pullback em Canal de Volatilidade com Step-Stop Dinâmico
Evolução da lógica de **Máximas e Mínimas (MM)** voltada para operações posicionadas por capital financeiro e gestão de risco progressiva.

* **Dimensionamento Dinâmico de Lote:** Calcula automaticamente o tamanho da posição com base no capital alocado (\Capital\) dividido pelo preço de referência (\MinPeriodo\ / \MaxPeriodo\).
* **Filtro de Permanência no Canal:** Exige que o preço permaneça dentro da zona delimitada pela MME e pelo múltiplo de *True Range* durante \PeriodosConfirmacao\ candles consecutivos antes de habilitar ordens.
* **Stop Progressivo via Progressão Geométrica:** Substitui escadas estáticas de stop por um cálculo exponencial dinâmico (\StopInicial * Power(FatorReducao, BarrasDecorridas)\), apertando o risco a cada barra decorrida até o limite de \MaxDegrausStop\, combinado com saída máxima por tempo (\MaxBarrasTrade\).

---

## 🛠️ Stack & Ferramentas
- **Linguagem:** NTSL (baseada em Object Pascal / Delphi)
- **Plataforma:** Nelogica Profit Pro
- **Versionamento:** Git & GitHub
