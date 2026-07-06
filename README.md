# Detecção de Intrusões em Rede (NIDS) com PCA e Machine Learning

Este projeto apresenta um estudo de caso focado na otimização de um Sistema de Detecção de Intrusão em Rede (NIDS) utilizando o dataset **UNSW-NB15**. O objetivo principal foi reduzir a alta dimensionalidade dos dados de tráfego de rede e avaliar o impacto dessa redução no desempenho e tempo de execução de diferentes algoritmos de Machine Learning.

## 🚀 Metodologia e Pipeline
* **Pré-processamento:** Tratamento de valores ausentes (`SimpleImputer`), codificação categórica (`LabelEncoder`) e padronização de escala (`StandardScaler`).
* **Redução de Dimensionalidade:** Aplicação de **PCA** reduzindo o espaço de recursos de 43 atributos para **20 componentes principais**, retendo **93,60% da variância explicada**.
* **Modelagem:** Avaliação comparativa de múltiplos algoritmos buscando balanceamento entre F1-Score Macro (crucial para classes minoritárias/ataques raros) e tempo de processamento.

## 📊 Resultados Obtidos

| Modelo | Acurácia Global | F1-Score (Macro) | Tempo de Execução |
| :--- | :---: | :---: | :---: |
| Regressão Logística | - | 32.95% | 27.54 min |
| Árvore de Decisão | 76.19% | 46.77% | **2.40 min** |
| Random Forest | **79.21%** | 48.83% | 14.00 min |
| **XGBoost (Campeão)** | 79.05% | **50.53%** | 6.88 min |

> 📌 **Paradoxo da Acurácia:** Embora o *Random Forest* tenha obtido a maior acurácia bruta, o *XGBoost* provou-se superior para o cenário de cibersegurança por apresentar o melhor F1-Score Macro, detectando com maior eficácia ataques raros (como Worms e Backdoors).

## 📂 Estrutura do Repositório
* `/notebooks`: Contém o script original do experimento desenvolvido em Python.
