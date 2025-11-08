# Analise de Bem-Estar Digital e Saude Mental
Projeto de portfólio em Power BI analisando o impacto dos hábitos digitais (tempo de tela, redes sociais) na saúde mental (estresse, sono).


### 1. INTRODUÇÃO (O DESAFIO)

Vivemos em uma era digital onde o tempo de tela e a presença em mídias sociais são onipresentes. Mas qual é o impacto real desses hábitos em nosso bem-estar?

O objetivo deste projeto foi utilizar o Power BI para analisar um conjunto de dados do Kaggle sobre saúde mental e hábitos digitais. O desafio era ir além dos números brutos e transformar dados "sujos" em uma análise visual clara (Data Storytelling) que respondesse à pergunta principal: **Como nossos hábitos digitais (tempo de tela, uso de redes sociais) se correlacionam com nossos níveis de estresse e qualidade do sono?**

* **Fonte dos Dados:** *Mental Health and Digital Wellbeing Dataset* (Kaggle)
* **Ferramenta:** Microsoft Power BI (Power Query para ETL e Power BI Desktop para Visualização)

---

### 2. PROCESSO (LIMPEZA E TRANSFORMAÇÃO DE DADOS - ETL)

Os dados brutos estavam inutilizáveis para análise direta. A etapa de ETL (Extração, Transformação e Carga) dentro do Power Query foi a fase mais crítica do projeto.

**Diagnóstico do Problema:**
Foi identificada uma inconsistência de escala em múltiplas colunas. Embora os nomes das colunas (metadados) sugerissem uma escala (ex: 1-10 ou "horas"), os valores reais estavam inflacionados, parecendo ter sido multiplicados por 10 (ex: 70 em vez de 7, ou 78 em vez de 7.8).

**Ações de Transformação Aplicadas:**

1.  **Padronização de Escala (Dividir por 10):**
    A operação "Dividir por 10" foi aplicada nas seguintes colunas para trazê-las à escala correta e realista:
    * `Stress_Level(1-10)`: (ex: 60 → 6)
    * `Happiness_Index(1-10)`: (ex: 50 → 5)
    * `Daily_Screen_Time(hrs)`: (ex: 78 → 7.8 horas)
    * `Exercise_Frequency(week)`: (ex: 50 → 5 vezes)
    * `Days_Without_Social_Media`: (ex: 70 → 7 dias)

2.  **Validação de Dados:**
    A coluna `Sleep_Quality(1-10)` foi inspecionada e validada como correta, não necessitando de transformação.

3.  **Agrupamento (Binning):**
    Para analisar o impacto da idade de forma clara, a coluna `Age` (que continha valores individuais como 15, 16, 17...) foi transformada. Criei "grupos" (binning) para agrupar os dados em faixas etárias (ex: 10-19, 20-29, 30-39...), o que limpou a visualização e permitiu uma análise de tendência mais eficaz.

---

### 3. VISUALIZAÇÃO E DESIGN (DATA STORYTELLING)

Com os dados limpos, o foco foi construir um dashboard que contasse uma história clara e fosse visualmente atraente.

* **Design:** Adotei um tema escuro (dark mode) para criar um visual moderno e profissional, garantindo alto contraste e legibilidade.
* **Layout e Hierarquia:** A história é contada de cima para baixo:
    * **Topo (KPIs):** Os 3 cartões principais (`Nível de Estresse`, `Qualidade do Sono` e `Tempo de Tela`) mostram as médias gerais, dando um panorama instantâneo.
    * **Centro (A Descoberta Principal):** O gráfico de dispersão foi posicionado como a "estrela" do dashboard. Ele é a prova visual que conecta os KPIs.
    * **Base (Contexto):** Os gráficos de apoio (`Tempo de Tela por Faixa Etária`, `Estresse por Gênero`, etc.) fornecem o contexto e os detalhes que suportam a descoberta principal.

---

### 4. ANÁLISE E PRINCIPAIS INSIGHTS

A análise dos dados limpos revelou insights claros sobre o impacto dos hábitos digitais:

* **INSIGHT PRINCIPAL: Mais Tempo de Tela = Pior Qualidade do Sono**
    O gráfico de dispersão (o visual central) prova uma **correlação negativa** clara: quanto maior o tempo de tela diário (eixo X), pior a qualidade do sono reportada (eixo Y). Usuários com +8 horas de tela raramente reportam qualidade de sono acima de 5, enquanto usuários com -4 horas de tela frequentemente reportam sono de alta qualidade (8-10).

* **INSIGHT 2: O Alto Tempo de Tela é Consistente Entre Idades**
    A análise por faixa etária (que só foi possível após o agrupamento) quebrou o mito de que apenas adolescentes usam muito o celular. O tempo médio de tela foi consistentemente alto (próximo de 6 horas/dia) em *todas* as faixas etárias, de 15 a 49 anos.

* **INSIGHT 3: Níveis de Estresse Sem Variação de Gênero**
    O gráfico "Nivel de stress por genero" mostrou que, neste conjunto de dados, os níveis médios de estresse são quase idênticos entre os gêneros "Male", "Female" e "Other", indicando ser um desafio universal.

* **INSIGHT 4: "Detox" de Rede Social Não Garante Sono Melhor**
    Curiosamente, o gráfico "qualidade do sono apos o uso de redes sociais" (barras horizontais) não mostrou uma correlação forte. Isso sugere que a qualidade do sono é um fator mais complexo do que simplesmente "ficar dias sem" usar redes sociais, sendo mais impactada pelo tempo de tela *total* (como visto no gráfico principal).

### 5. CONCLUSÃO

Este projeto reforça a importância vital do processo de **ETL**: sem a limpeza e padronização dos dados, qualquer análise seria falha e enganosa. O dashboard final prova visualmente a conexão prejudicial entre o tempo de tela excessivo e a qualidade do sono, demonstrando a capacidade do Power BI em transformar dados brutos em insights acionáveis e estratégicos.
