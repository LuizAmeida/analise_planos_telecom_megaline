# Análise de Planos de Telecom - Megaline

> Projeto de análise de dados de uma empresa de telecomunicações (Megaline) para determinar qual dos planos pré-pagos (Surf e Ultimate) gera mais receita, auxiliando o departamento comercial no ajuste do orçamento de publicidade.

---

## 🎯 Objetivo do Projeto

Realizar uma análise comparativa entre os planos pré-pagos **Surf** e **Ultimate** da operadora Megaline, com os seguintes objetivos:

- **Analisar o comportamento de consumo** dos usuários (chamadas, mensagens e internet)
- **Calcular a receita gerada** por cada plano
- **Determinar qual plano gera mais receita** para a empresa
- **Testar hipóteses estatísticas** sobre diferenças de receita entre planos e regiões
- **Fornecer recomendações** para o departamento comercial

---

## 📊 Resultados Obtidos

### 1. Comportamento de Chamadas

| Métrica | Plano Surf | Plano Ultimate |
|---------|------------|----------------|
| Média de minutos/mês | 428,7 min | 430,5 min |
| Mediana | 410 min | 432 min |
| Desvio padrão | 234,5 min | 240,5 min |
| Limite do plano | 500 min | 3.000 min |

**Conclusão:** Os usuários de ambos os planos consomem praticamente a mesma quantidade de minutos (~430 min/mês). O plano Ultimate é superdimensionado para chamadas, já que seu limite é 6x maior que o uso médio.

---

### 2. Comportamento de Mensagens

| Métrica | Plano Surf | Plano Ultimate |
|---------|------------|----------------|
| Média de mensagens/mês | 31,2 | 37,6 |
| Mediana | 24,0 | 30,0 |
| Desvio padrão | 33,6 | 34,8 |
| Limite do plano | 50 | 1.000 |

**Conclusão:** O uso de mensagens é baixo em ambos os planos. O SMS não é um fator significativo para geração de receita extra.

---

### 3. Comportamento de Internet (Dados)

| Métrica | Plano Surf | Plano Ultimate |
|---------|------------|----------------|
| Média de GB/mês | 16,2 GB | 16,8 GB |
| Mediana | 16,4 GB | 16,5 GB |
| Desvio padrão | 7,8 GB | 7,7 GB |
| Limite do plano | 15 GB | 30 GB |
| % que excedem o limite | **57,9%** | **5,7%** |

**Conclusão:** O consumo médio de internet é similar entre os planos (~16,5 GB/mês). Porém, **57,9% dos usuários do Surf excedem o limite** de 15 GB, gerando receita adicional com taxas extras. Já no Ultimate, apenas 5,7% excedem o limite.

---

### 4. Receita por Plano

| Métrica | Plano Surf | Plano Ultimate |
|---------|------------|----------------|
| **Receita média mensal** | **$60,71** | **$72,31** |
| Mediana | $40,36 | $70,00 |
| Desvio padrão | $55,39 | $11,40 |
| Mínimo | $20,00 | $70,00 |
| Máximo | $590,37 | $182,00 |
| Total acumulado | $95.491,18 | $52.066,00 |

**Conclusões:**
- O plano **Ultimate** gera **maior receita média por usuário** ($72,31 vs $60,71)
- O plano **Surf** tem alta variabilidade (desvio padrão de $55,39) devido às taxas extras de usuários que excedem limites
- O plano **Ultimate** oferece **receita estável e previsível** (desvio padrão de apenas $11,40)

---

### 5. Testes de Hipóteses

**Hipótese 1: Receita média - Surf vs Ultimate**
- **H₀:** As receitas médias são iguais
- **H₁:** As receitas médias são diferentes
- **p-value:** 2,86 × 10⁻⁸
- **Resultado:** **REJEITAMOS H₀** - Há diferença significativa entre as receitas médias

**Hipótese 2: Receita média - NY-NJ vs Outras Regiões**
- **H₀:** As receitas médias são iguais entre as regiões
- **H₁:** As receitas médias são diferentes entre as regiões
- **p-value:** 0,0436
- **Resultado:** **REJEITAMOS H₀** - Há diferença significativa entre as regiões

---

## 🛠️ Ferramentas Utilizadas

- **Python 3**
- **Bibliotecas:**
  - `pandas` — manipulação e análise de dados
  - `numpy` — operações matemáticas
  - `matplotlib` — visualização de dados (gráficos de barras, histogramas, boxplots)
  - `scipy.stats` — testes de hipótese (t-test)

---

## 📚 O que Aprendi

- **Leitura e integração de múltiplas tabelas:** uso de `pd.read_csv()` para carregar 5 tabelas relacionadas (users, calls, messages, internet, plans)
- **Limpeza e pré-processamento:**
  - Conversão de tipos de dados (object → datetime, float → int)
  - Tratamento de valores ausentes
  - Padronização de colunas (lowercase, remoção de espaços)
  - Criação de colunas derivadas (mês, região NY-NJ, GB)
- **Agregação de dados:** agrupamento por usuário e mês com `groupby()`
- **Cálculo de receita:** implementação de função para calcular receita mensal considerando:
  - Taxa fixa do plano
  - Minutos extras (arredondados para cima)
  - Mensagens extras
  - GB extras (arredondados para cima)
- **Análise exploratória:**
  - Estatísticas descritivas (média, mediana, desvio padrão, variância)
  - Visualizações (histogramas, boxplots, gráficos de linhas)
- **Testes de hipótese:** aplicação de t-test para comparar médias entre grupos
- **Interpretação de negócios:** tradução de dados em recomendações estratégicas

---

## 🚀 Como Executar o Projeto

```bash
# Clone o repositório
git clone https://github.com/LuizAlmeida/analise_planos_telecom_megaline

# Navegue até a pasta do projeto
cd analise_planos_telecom_megaline

# Execute o notebook (recomendado: Google Colab ou Jupyter Notebook)
# Ou execute o script Python diretamente
python analise_megaline.py
````


## Requisitos:
- Python 3.x instalado
- Jupyter Notebook (opcional) ou Google Colab (recomendado)
- Bibliotecas: pip install pandas numpy matplotlib scipy


## 🔍 Metodologia
O projeto seguiu uma abordagem estruturada em 5 etapas:


## Etapa 1: Carregamento e Preparação dos Dados
- Leitura das 5 tabelas do dataset Megaline
- Conversão de tipos de dados
- Tratamento de valores ausentes
- Padronização de colunas

## Etapa 2: Enriquecimento dos Dados
- Extração de mês das datas
- Criação de coluna is_ny_nj para identificar região NY-NJ
- Conversão de MB para GB

## Etapa 3: Agregação por Usuário/Mês
- Cálculo de chamadas, minutos, mensagens e dados por usuário/mês
- Junção das tabelas em um único DataFrame (merge_all)

## Etapa 4: Cálculo da Receita
- Implementação da função calculate_monthly_revenue()
- Aplicação das regras de negócio da Megaline:
- Minutos arredondados para cima
- GB arredondados para cima
- Cálculo de extras por excedente

## Etapa 5: Análise e Testes de Hipótese
- Estatísticas descritivas por plano
- Visualizações comparativas
- Teste t para comparar receitas entre planos
- Teste t para comparar receitas entre regiões


## 💡 Recomendações para o Departamento Comercial
1. Onde investir o orçamento de publicidade:
- O plano Ultimate deve receber maior investimento
- Justificativa: maior receita média ($72,31 vs $60,71) e maior previsibilidade financeira

2. Estratégias para aumentar receita:
- Plano Surf: Oferecer upgrade para Ultimate quando gasto extra recorrente ultrapassar a diferença de mensalidade
- Plano Ultimate: Focar comunicação em "paz de espírito" e ausência de cobranças surpresa

3. Estratégia regional:
- NY-NJ: Considerar campanhas específicas, pois o comportamento difere estatisticamente das demais regiões


## 📁 Estrutura do Projeto
````
📁 analise_planos_telecom_megaline/
├── 📁 datasets/                    # Dados utilizados
│   ├── megaline_users.csv
│   ├── megaline_calls.csv
│   ├── megaline_messages.csv
│   ├── megaline_internet.csv
│   └── megaline_plans.csv
├── 📁 notebooks/                   # Notebook Jupyter com análise completa
│   └── Projeto_Sprint_4.ipynb
├── 📁 scripts/                     # Scripts Python avulsos
├── README.md                       # Este arquivo
└── requirements.txt                # Dependências do projeto
````


## 📌 Contato
- [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/luizmarques84)
- [![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/LuizAlmeida)


## ⭐ Este projeto faz parte do meu Bootcamp em Análise de Dados na TripleTen.

````
📊 Resumo dos Insights para Investidores
- Métrica	Insight
- Plano mais rentável	Ultimate (receita média $72,31 vs $60,71 do Surf)
- Principal fonte de receita extra	Excedentes de internet no plano Surf (57,9% dos usuários)
- Previsibilidade	Ultimate tem receita estável (desvio padrão $11,40)
- Comportamento regional	NY-NJ tem receita diferente das demais regiões
- Mensagens	Baixo uso em ambos os planos (não gera receita significativa)
- Chamadas	Uso similar entre planos (~430 min/mês)
- Conclusão Estratégica: O plano Ultimate é o mais rentável e previsível. A estratégia deve focar na conversão de usuários pesados do Surf para o Ultimate, garantindo satisfação do cliente e estabilidade da receita.
````


````
---
## 🎯 RESUMO DO QUE FAZER

| Ação | Status |
|------|--------|
| Criar repositório `analise_planos_telecom_megaline` | ⬜ |
| Fazer upload do arquivo `.ipynb` | ⬜ |
| Adicionar README.md com o texto acima | ⬜ |
| Adicionar tópico `tripleten` | ⬜ |
| Fixar (pinned) no perfil | ⬜ |

---
````
