# 📘 Manual do Usuário - Painel BI & Assistente PLS ESMPU (v04)

Bem-vindo ao guia oficial do Painel de Business Intelligence e Assistente de Elaboração de Planos de Logística Sustentável (PLS), desenvolvido no âmbito do Programa de Bolsas de Pesquisa Científica da **Escola Superior do Ministério Público da União (ESMPU)** (*"Ministério Público da União Verde: liderando a transformação da gestão sustentável"*).

---

## 🚀 1. Visão Geral
O sistema integra o diagnóstico empírico de sustentabilidade (nos eixos **Água**, **Energia Elétrica** e **Resíduos Sólidos**), a comparação interinstitucional da **ESMPU (Unidade Piloto)** com demais órgãos públicos, o catálogo normalizado de **50 indicadores** e o módulo interativo **"Monte seu PLS"**.

---

## 🗺️ 2. Navegação pelas 9 Abas do Painel

### 🏠 1. Início (Capa)
* **Atalhos de Unidade / Escopo**: Filtre todo o painel com 1 clique entre **`ESMPU (Unidade Piloto)`**, **`MPU (Todos)`** ou **`Outros Órgãos`**.
* **KPIs Dinâmicos**: Total de Iniciativas, Eixos de Atuação, Estados Avaliados e Unidades/Órgãos.
* **Resumo Visual**: Gráfico de Rosca por Eixo e Barras Empilhadas dos Top 5 Estados.

### 📊 2. Eixos
* **Volume Detalhado**: Comparação horizontal entre Energia Elétrica, Água e Resíduos Sólidos.
* **Nuvem de Termos**: Palavras-chave mais recorrentes nas ações brutas e consolidadas.

### 📍 3. Geográfico
* **Mapa Interativo do Brasil**: Clique em qualquer UF para filtrar o painel e abrir o **Painel de Detalhes Selecionados** agrupado por eixo.
* **Ranking de Unidades**: Top 10 unidades com maior número de iniciativas.

### 💡 4. Insights Estratégicos
* **Cards de Destaque**: Mostra a Unidade Líder no filtro atual, UF de maior concentração, atalho direto para a **Unidade Piloto (ESMPU)** e Eixo Predominante.
* **Análise de Pareto por Unidade/Instituição**: Ranking completo de todas as instituições (com a barra da **ESMPU** destacada em coral/vermelho).
* **Matriz de Calor (Eixo vs. Unidade)**: Cruzamento de intensidade de iniciativas por instituição e eixo temático.

### 🔬 5. Diagnóstico ESMPU (Novo!)
Consolida visualmente os achados dos **Relatórios de Acompanhamento 10, 11 e 12**:
* **Gráficos Comparativos (01 a 04)**: Compara a distribuição percentual da **ESMPU ($n = 10$)** frente aos **Demais Órgãos ($n = 386$)** na composição geral por eixo e dentro de *Resíduos Sólidos*, *Água* e *Energia Elétrica*.
* **Matriz de Cobertura e Lacunas Temáticas (*Gap Analysis*)**: Lista todas as 17 categorias consolidadas da taxonomia da pesquisa, indicando quais já são contempladas pelo PLS 2026–2028 da ESMPU e quais constituem as **11 lacunas temáticas** (monitoramento sistemático, coleta seletiva interna, logística reversa, águas pluviais, reúso etc.).
  * **Botão `+ Suprir Lacuna`**: Envia qualquer lacuna diretamente para o assistente *Monte seu PLS* já preenchida com recomendação operacional, área responsável, periodicidade e indicadores vinculados!
* **Tabela de Consolidação ESMPU & Os 6 Desafios de Governança**: Exibe as 10 ações brutas do item *"7. Plano de Ações e Metas"* do PLS da ESMPU convertidas em ações consolidadas, além dos 6 desafios de elaboração de PLS e as soluções entregues pela pesquisa.

### 🎯 6. Indicadores
* **Catálogo de 50 Indicadores Classificados**: Inclui os indicadores do PLS MPDFT e os novos **indicadores científicos gravimétricos da Equipe de Pesquisa** (geração total em kg, geração per capita em kg/pessoa, compostagem em kg, aterro sanitário em kg, taxa de desvio de aterro em %, consumo hídrico per capita e águas pluviais).
* **Filtros Combinados**: Filtre por **Eixo**, **Fonte** (`PLS MPDFT 2022` ou `Equipe`), **Categoria** (`gravimétrico / monitoramento`, `eficiência`, `gestão de contrato`, `redução na fonte`, `logística reversa` etc.) e busca textual.

### 🛍️ 7. Monte seu PLS (Assistente & Modelo ESMPU)
Construa ou atualize um Plano de Logística Sustentável completo em 3 etapas:
1. **Botões de Carregamento Rápido (Templates ESMPU)**:
   * **`PLS ESMPU (Base)`**: Carrega as ações originais do PLS 2026–2028 da ESMPU.
   * **`PLS Modelo ESMPU (Completo)`**: Carrega o plano da ESMPU acrescido das ações recomendadas pela pesquisa para cobrir todas as 11 lacunas temáticas e seus respectivos indicadores gravimétricos e de monitoramento.
2. **Metadados de Governança (Etapa 2)**: Ao cadastrar cada ação, defina a **Ação Consolidada** (taxonomia padronizada), a **Forma de Trabalho Operacional (Ação Bruta)**, a **Área Responsável** (*Comissão de Sustentabilidade, Engenharia, Compras, Contratos, Comunicação, Gestão de Pessoas, TI*), a **Periodicidade**, a **Base de Cálculo** (*Total, Per Capita, por $m^2$, Gravimétrico em kg*), a **Linha de Base (2023–2025)** e a **Meta (2026–2028)**.
3. **Exportação Executiva**: Exporte o plano estruturado em **PDF** (formatado para impressão/anexo SEI) ou **Excel (XLSX)**, ou salve/carregue a sessão em arquivo `.json`.

### 📋 8. Monitoramento & Coleta Padronizada (Novo!)
Módulo operacional integrado ao portal `http://sustentabilidade.site` para transformar o monitoramento em rotina:
* Registre medições mensais/anuais informando a **População de Referência (Fixa + Flutuante)** e a **Área Construída ($m^2$)**.
* **Pesagem Gravimétrica de Resíduos (kg)**: Registre os quilogramas destinados a *Cooperativas (Recicláveis)*, *Compostagem (Orgânicos)* e *Aterro Sanitário (Rejeitos)*. O painel calcula automaticamente o total gerado, os indicadores *per capita* e a **Taxa de Desvio de Aterro (%)**, atualizando o gráfico empilhado da série histórica e permitindo exportação para Excel.

### 🗄️ 9. Relatórios (Base de Dados)
* Tabela auditável com busca global, filtros independentes por coluna e gerador de relatórios filtrados ou completos em **PDF** e **XLSX**.

---
*Grupo de Pesquisa "Ministério Público da União Verde" – ESMPU (2026).*
