# ReSkill 360 – Ecossistema Inteligente de Requalificação Profissional

<img src="assets/reskill_intro.png" width="100%" />

## 🌍 Sobre o Projeto

Com o avanço da automação e da inteligência artificial, milhões de profissionais estão sendo substituídos por máquinas, e o Brasil ainda carece de uma estrutura eficiente para **requalificação rápida e acessível**.

O **ReSkill 360** surge como uma resposta a esse desafio: um ecossistema inteligente que une **tecnologia, educação e empregabilidade** para transformar trajetórias profissionais.

A plataforma utiliza **IA educacional** para:
- identificar lacunas de competências  
- recomendar trilhas personalizadas  
- sugerir cursos com base em dados reais do mercado  
- conectar profissionais a oportunidades de emprego  

A solução contribui diretamente para os ODS:
- **ODS 4** – Educação de Qualidade  
- **ODS 8** – Trabalho Decente  
- **ODS 10** – Redução das Desigualdades  

Mais do que uma plataforma, o ReSkill 360 é um movimento nacional de requalificação inteligente.

---

# 📱 Protótipo da Plataforma

<img src="assets/prototipo_reskill.png" width="100%" />

### Telas Demonstradas
- **Login / Cadastro**
- **Dashboard com trilha de aprendizagem**
- **Certificações e oportunidades de emprego**

---


## Visão Geral

Este projeto implementa, em Python, uma ferramenta para selecionar o **melhor conjunto de trilhas de capacitação para o Futuro do Trabalho** utilizando **Programação Dinâmica**.

O objetivo é **maximizar o impacto na empregabilidade** de um profissional, respeitando um **limite de horas disponíveis** para estudo.

A solução utiliza:

- `pandas` e **DataFrames**
- **Merge Sort recursivo com memoização** para ordenação
- **Mochila 0/1 recursiva com memoização** para seleção das trilhas
- Funções auxiliares **recursivas**
- **Geração de relatório final** com os resultados

---

## 1. Criação dos Dados (DataFrame)

A função `construir_dataframe_trilhas()` cria um `DataFrame` com **mais de 20 trilhas de capacitação**, cada uma contendo:

- `id`
- `nome`
- `area`
- `carga_horaria`
- `custo`
- `impacto_empregabilidade`
- `ods_principal`

Essas trilhas representam temas essenciais para o **Futuro do Trabalho**, incluindo:

- Inteligência Artificial  
- Ciência de Dados  
- Soft Skills  
- Gestão e Liderança  
- Inclusão e Diversidade  
- Sustentabilidade e ODS  

---

## 2. Ordenação com Merge Sort Recursivo + Memoização

Para ordenar as trilhas pelo impacto de empregabilidade, o código implementa **Merge Sort recursivo** com **memoização**.

- A função `merge_sort_ids()`:
  - Divide a lista de IDs em sublistas
  - Ordena recursivamente cada parte
  - Faz o *merge* das listas ordenadas
  - Usa memoização para evitar recalcular subproblemas repetidos

- A função `ordenar_trilhas_por_impacto(df, col="impacto_empregabilidade")`:
  - Usa os IDs ordenados pelo `merge_sort_ids`
  - Retorna o `DataFrame` reordenado com base na coluna de impacto

---

## 3. Mochila 0/1 Recursiva (Knapsack)

Para selecionar as trilhas ideais dentro de um **limite máximo de horas**, o código utiliza uma versão recursiva da **Mochila 0/1** com memoização.

- A função `mochila_recursiva(...)` considera, para cada trilha:
  - **Pegar a trilha** (se couber no limite de horas)
  - **Não pegar a trilha**

- A memoização armazena resultados intermediários e:
  - Evita recomputar combinações de índice + horas disponíveis
  - Aumenta eficiência da solução

- A função `selecionar_trilhas_otimas(df, max_horas)`:
  - Extrai os dados relevantes do `DataFrame`
  - Chama `mochila_recursiva(...)`
  - Retorna:
    - O **impacto total máximo**
    - A **lista de IDs** das trilhas escolhidas

---

## 4. Funções Auxiliares Recursivas

Além das funções principais, o projeto conta com funções auxiliares recursivas, também com memoização:

- `soma_metricas_recursiva(...)`  
  - Calcula somas como:
    - Total de horas
    - Impacto total das trilhas escolhidas

- `gerar_relatorio(df, ids_escolhidos)`  
  - Monta um **relatório completo**, incluindo:
    - Lista de trilhas selecionadas
    - Carga horária total
    - Impacto de empregabilidade total
    - **Resumo por área** (quantidade de trilhas, horas, impacto médio)
  - Facilita a interpretação e a tomada de decisão baseada em dados

---

## 5. Fluxo Completo da Execução

O fluxo geral do programa é:

1. **Gerar o DataFrame** com as trilhas (`construir_dataframe_trilhas()`)
2. **Ordenar as trilhas por impacto** (`ordenar_trilhas_por_impacto(...)`)
3. **Definir o limite de horas**, por exemplo: `max_horas = 40`
4. **Executar a mochila recursiva** para encontrar o melhor conjunto de trilhas  
   (`selecionar_trilhas_otimas(...)`)
5. **Gerar e imprimir o relatório completo** (`gerar_relatorio(...)`)

---

## Resumo Final

A solução aplica conceitos fundamentais de **Programação Dinâmica**:

- Recursão  
- Memoização  
- Divisão e conquista  
- Mochila 0/1

em um cenário realista ligado ao **Futuro do Trabalho** e ao contexto de **ReSkill / Global Solution**.

📋 Integrantes

👤 Paulo Poças – RM556080

👤 Guilherme Gomes – RM554606 

👤 André Luiz Fernandes De Queiroz - Rm554503
