# 🛠️ Documentação Técnica - Painel BI & Assistente PLS ESMPU (v04)

Este documento descreve a arquitetura técnica, os modelos de dados, os algoritmos de consolidação taxonômica e os módulos de governança ambiental implementados no Painel de Business Intelligence e Assistente de Planos de Logística Sustentável (PLS) da **Escola Superior do Ministério Público da União (ESMPU)**.

---

## 🏗️ 1. Arquitetura do Projeto
O projeto segue uma arquitetura **Single Page Application (SPA)** 100% *client-side* (sem dependência de servidores proprietários ou licenças de BI, atendendo ao **Desafio 1.6** identificado no 12º Relatório de Acompanhamento).

### Estrutura de Arquivos:
- [index.html](file:///c:/Users/tiago.magalhaes/Downloads/ANTIGRAVIDADE_003_ESMPU/index.html): Estrutura semântica HTML5 distribuída em **10 telas modulares** (`Início`, `Eixos`, `Geográfico`, `Insights`, `Desafios & Soluções`, `Diagnóstico ESMPU [Em breve]`, `Indicadores`, `Monte seu PLS`, `Monitoramento` e `Relatórios`).
- [styles.css](file:///c:/Users/tiago.magalhaes/Downloads/ANTIGRAVIDADE_003_ESMPU/styles.css): Design System baseado em variáveis CSS (*Glassmorphism*), layout em Grid/Flexbox e 4 esquemas de cores (`Praia`, `Claro`, `Escuro`, `Alto Contraste`).
- [app.js](file:///c:/Users/tiago.magalhaes/Downloads/ANTIGRAVIDADE_003_ESMPU/app.js): Motor principal da aplicação. Gerencia estado global (`GlobalState`), sanitização taxonômica, cross-filtering, diagnóstico comparativo, assistente PLS em 3 etapas, monitoramento gravimétrico e exportação PDF/XLSX.
- [Iniciativas_Consolidadas_20260309_v03.xlsx](file:///c:/Users/tiago.magalhaes/Downloads/ANTIGRAVIDADE_003_ESMPU/Iniciativas_Consolidadas_20260309_v03.xlsx): Base consolidada de iniciativas contendo **257 ações mapeadas** (incluindo as **10 ações do PLS 2026–2028 da ESMPU** e as ações dos demais ramos do MPU e órgãos públicos).
- [indicadores_normalizado.xlsx](file:///c:/Users/tiago.magalhaes/Downloads/ANTIGRAVIDADE_003_ESMPU/indicadores_normalizado.xlsx): Catálogo relacional normalizado (`Fontes`, `Eixos`, `Indicadores`) com **50 indicadores classificados**, incluindo métricas gravimétricas contínuas em quilogramas (`kg`) para o eixo Resíduos Sólidos.
- [br-all.geo.json](file:///c:/Users/tiago.magalhaes/Downloads/ANTIGRAVIDADE_003_ESMPU/br-all.geo.json): Malha cartográfica das Unidades Federativas do Brasil para renderização via Apache ECharts.

---

## 🧠 2. Gerenciamento de Estado e Sanitização (`GlobalState` & `sanitizeRawData`)

### A. Sanitização Taxonômica Automática (`sanitizeRawData`)
Para eliminar fragmentações decorrentes de espaços duplos ou variações ortográficas nas planilhas originais (**Desafio 1.3 - Padronizar conceitos e nomenclaturas**), o pipeline de leitura executa:
1. Padronização das 17 categorias de **Ações Consolidadas** nos 3 eixos (`Energia Elétrica`, `Água` e `Resíduos`).
2. Verificação de integridade e injeção garantida das **10 ações do PLS 2026–2028 da ESMPU** (`Unidade: 'ESMPU'`, `Órgão: 'MPU'`, `Estado: 'DF'`).

### B. Filtros Cumulativos e Atalhos de Escopo
- `GlobalState.filters`: Filtra cumulativamente por `Eixo`, `Estado`, `Órgão` e `Unidade`.
- `GlobalState.specialFilters.UnidadeGroup`: Permite alternar rapidamente na Capa entre:
  - **`ESMPU (Unidade Piloto)`**: Isola as 10 ações do PLS da ESMPU.
  - **`MPU (Todos)`**: Filtra unidades do Ministério Público da União (`ESMPU`, `PGR`, `MPT`, `PRs`, `PRRs`, `PRMs`).
  - **`Outros Órgãos`**: Filtra os 13 órgãos externos da amostra comparativa (`STF`, `STJ`, `TST`, `STM`, `TCU`, `Senado`, `Câmara`, `TJs` e `MPEs`).

---

## 🚧 3. Módulo de Diagnóstico Institucional ESMPU (`screen-diagnostico` – Em Construção + Acervo Guardado)
- **Estado Padrão ("Em Construção — Aguardando Tratativas Finais do Piloto com a ESMPU")**: Exibe aviso institucional referenciando o Processo SEI nº `0.01.000.1.004154/2024-96`, linha do tempo de 4 marcos e sinalização de que o grupo aguarda a conclusão das tratativas operacionais e da escuta in loco junto à Comissão de Sustentabilidade da ESMPU.
- **Acervo Técnico Guardado (`#diag-saved-archive-container` / `toggleDiagSavedArchive()`)**: Preserva integralmente no sistema os resultados documentais preliminares da 11ª entrega, expansíveis sob demanda:
  1. **Gráficos Comparativos (Gráficos 01 a 04)**: Compara a distribuição percentual entre **Demais Órgãos ($n = 386$)** e **PLS ESMPU ($n = 10$)** por eixo e por categoria consolidada.
  2. **Matriz de Cobertura e Lacunas Temáticas (*Gap Analysis*)**: Avalia as 17 categorias consolidadas (6 contempladas e 11 lacunas temáticas), com botão `+ Suprir Lacuna`.
  3. **Tabela de Consolidação das 10 Ações Brutas vs. Consolidadas da ESMPU**.

---

## 🧭 3.1 Módulo de Mapeamento de Dificuldades & Soluções Práticas (`screen-desafios`)
Implementa em uma seção dedicada e transversal os achados do **12º Relatório de Acompanhamento** (análise dos PLS 2016 e 2026–2028 da ESMPU, PLS 2024–2026 do MPF e Relatório MASA 2025 do MPT):
1. **Os 6 Cartões de Desafios Críticos e 18 Protocolos Práticos (`DIAG_DESAFIOS_REL12`)**:
   - Filtra os desafios por etapa do ciclo (*Formulação & Padronização: 1.1 a 1.3* vs. *Articulação, Rotina & Ferramentas: 1.4 a 1.6*).
   - Para cada desafio, apresenta o diagnóstico da dificuldade, as fontes documentais, **3 soluções práticas aplicáveis** e um botão de ação direta que leva à tela correspondente da ferramenta, além de exportação do Guia de Soluções em PDF (`exportDesafiosPDF()`).
2. **Simulador Prático de Base de Cálculo & Público Flutuante (`runBaseCalculoSimulator`)**:
   - Resolve o Desafio 1.2 calculando em tempo real a **População Equivalente Ponderada** ($\text{Pop. Fixa} + \text{Público Flutuante} \times \text{Fator Presencial}$), o percentual de distorção evitado e os indicadores comparados por habitante equivalente e por metro quadrado ($m^2$).
3. **Roteiro Prático de Superação (`renderDesafiosChecklist`)**:
   - Checklist interativo de 12 itens de autoavaliação vinculado ao KPI de maturidade da unidade.

---

## 🛍️ 4. Assistente "Monte seu PLS" com Metadados de Governança (`screen-monte-pls`)
O fluxo em 3 etapas (`1. Eixos Estratégicos` → `2. Ações & Formas de Trabalho` → `3. Vincular Indicadores`) foi expandido para atender aos **Desafios 1.1, 1.2, 1.3 e 1.4**:
- Cada ação cadastrada armazena:
  - `nome`: Ação Consolidada (Taxonomia padronizada ou personalizada).
  - `descricao`: Forma de Trabalho Operacional ("Ação Bruta" adaptada à realidade da unidade).
  - `areaResponsavel`: Área gestora da execução/coleta (`Comissão de Sustentabilidade`, `Engenharia e Manutenção`, `Compras e Licitações`, `Contratos e Serviços Gerais`, `Comunicação Social`, `Gestão de Pessoas`, `TI`).
  - `periodicidade`: `Mensal`, `Trimestral`, `Semestral`, `Anual` ou `Contínua`.
  - `baseCalculo`: `Total Absoluto`, `Per Capita (Pop. Fixa + Flutuante)`, `Por Área Construída (m²)`, `Gravimétrico Contínuo (kg)` ou `Indicador de Processo / Entrega`.
  - `linhaBase`: Retrato histórico 2023–2025.
  - `meta`: Meta objetiva para o ciclo 2026–2028.
- **Templates Prontos da ESMPU (`loadPlsModelESMPU`)**:
  - **PLS ESMPU (Base)**: Carrega as ações originais do PLS 2026–2028 da ESMPU agrupadas nas categorias consolidadas.
  - **PLS Modelo ESMPU (Completo)**: Carrega o plano da ESMPU acrescido das recomendações da pesquisa para fechar todas as 11 lacunas temáticas e vincular os novos indicadores gravimétricos.

---

## 📋 5. Módulo de Coleta Padronizada & Monitoramento Gravimétrico (`screen-coleta`)
Desenvolvido para responder aos **Desafios 1.1, 1.2 e 1.5** e integrar-se ao portal `http://sustentabilidade.site`:
- Registra medições periódicas com **População de Referência (Fixa + Flutuante)** e **Área Construída ($m^2$)**.
- **Monitoramento Gravimétrico de Resíduos Sólidos (em kg)**: Registra separadamente *Recicláveis enviados a Cooperativas (kg)*, *Orgânicos para Compostagem (kg)* e *Rejeitos enviados a Aterro Sanitário (kg)*, calculando automaticamente o **Total Gerado (kg)**, a **Geração Per Capita (kg/hab)** e a **Taxa de Desvio de Aterro (%)**.
- Plota em tempo real o gráfico empilhado da série histórica gravimétrica e exporta a planilha completa em `.xlsx`.

---
**Desenvolvimento**: Grupo de Pesquisa *"Ministério Público da União Verde: liderando a transformação da gestão sustentável"* – ESMPU.
