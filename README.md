# Agrupamento Socioeconômico de Municípios Brasileiros (IDHM 2010)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1doC4r3Ke8UNkRfjJhE7rXYpKOVH3MmCp?authuser=2#scrollTo=191c4878)

Este projeto aplica técnicas de Aprendizado de Máquina Não Supervisionado (Clusterização) para identificar e agrupar os municípios brasileiros com base em similaridades socioeconômicas, utilizando dados do Atlas do Desenvolvimento Humano no Brasil (2013).

O objetivo é ir além das macro-desigualdades óbvias do país, descobrindo perfis estruturais e demográficos subjacentes que definem diferentes níveis de vulnerabilidade e desenvolvimento local.

## 🛠️ Tecnologias e Ferramentas
* **Linguagem:** Python
* **Bibliotecas:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
* **Técnicas de ML:** K-Means, Análise de Componentes Principais (PCA)
* **Métricas de Validação:** Método do Cotovelo (Diferenças Finitas), Índice de Silhueta

## 📊 Pipeline de Análise

1. **Pré-processamento e Limpeza:** 
   Extração dos dados brutos referentes ao ano de 2010 (Kaggle API) e remoção de mais de 150 atributos redundantes, pesos estatísticos ou dependentes puramente do tamanho populacional absoluto.
2. **Redução de Dimensionalidade (PCA):** 
   Aplicação de PCA nos dados padronizados (StandardScaler) para tratar a alta correlação entre os indicadores. O dataset foi reduzido a **23 Componentes Principais**, preservando 90% da variância original.
3. **Validação do K-Means:** 
   O hiperparâmetro `k` (número de clusters) foi otimizado utilizando o Método do Cotovelo com cálculo automático de derivadas (1ª e 2ª ordem) e o Índice de Silhueta, apontando para configurações ideais entre `k=2`, `k=3` e `k=4`.
4. **Modelagem e Interpretação via Lift:**
   Análise do *Lift* (variação percentual da média do cluster em relação à média global do Brasil) para interpretar as características definidoras de cada grupo.

## 💡 Principais Insights e Perfis Identificados

Ao variar o hiperparâmetro $k$, o algoritmo revelou diferentes camadas da estrutura socioeconômica brasileira:

* **k=2 (Macro-desigualdade Clássica):** Separação binária nítida entre polos urbanos desenvolvidos (alta infraestrutura e serviços) e municípios com alta vulnerabilidade (extrema pobreza e falta de saneamento).
* **k=3 (O Brasil Intermediário):** Quebra a polarização revelando um terceiro grupo: cidades com infraestrutura de sobrevivência estruturada, mas que sofrem de estagnação econômica e dependem fortemente do emprego no setor público.
* **k=4 (Extremos Isolados):** Permite isolar anomalias demográficas, identificando um pequeno cluster de extrema indigência isolada e gargalos críticos na educação básica, separando-os da pobreza estagnada geral.

## 🚀 Como Executar

Você pode visualizar e rodar o projeto diretamente no navegador clicando no botão **Open in Colab** no topo da página. 

Caso queira rodar localmente:
1. Clone o repositório:
   ```bash
   git clone [https://github.com/seu-usuario/nome-do-repositorio.git](https://github.com/seu-usuario/nome-do-repositorio.git)
   ```
2. Instale as dependências:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn kagglehub
   ```
3. Execute o notebook `trabalho02_idhm_2010.ipynb` na sua IDE de preferência.
