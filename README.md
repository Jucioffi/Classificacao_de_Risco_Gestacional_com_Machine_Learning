# Classificacao_de_Risco_Gestacional_com_Machine_Learning

Visão Geral do Projeto

Apresentar uma solução de Machine Learning para classificar gestantes em três níveis de risco — baixo, médio e alto — a partir de dados vitais (idade, pressão arterial, glicemia, etc.).

O objetivo do projeto foi maximizar a identificação correta de pacientes de alto risco, oferecendo uma ferramenta de apoio à decisão clínica. seguindo os critérios:

1. Desenvolvimento de modelo preditivo para risco gestacional;

2. Avaliação de múltiplos algoritmos (Logistic Regression, Random Forest, Gradient Boosting);

3. Foco em sensibilidade (Recall) da classe de alto risco;

4. Uso de técnicas de pré-processamento, padronização e balanceamento (SMOTE).

# Dataset

O conjunto de dados utilizado é o "Maternal Health Risk Data Set". Ele contém dados anônimos sobre os sinais vitais de gestantes.

Fonte: Maternal Health Risk Data Set: https://github.com/Jucioffi/Classificacao_de_Risco_Gestacional_com_Machine_Learning/blob/main/Maternal%20Health%20Risk%20DataSet.xlsx

Variáveis

* Age: Idade da gestante (anos);

* SystolicBP: Pressão arterial sistólica (mm Hg);

* DiastolicBP: Pressão arterial diastólica (mm Hg);

* BS: Glicemia (nível de glicose no sangue);

* BodyTemp: Temperatura corporal (°C);

* HeartRate: Frequência cardíaca (bpm);

* RiskLevel: Variável alvo (baixo, médio, alto risco).

# Bibliotecas utilizadas

Pandas: Biblioteca fundamental para o projeto. Foi usada para carregar o dataset, manipular os dados em DataFrames, realizar a limpeza, criar novas colunas (engenharia de atributos) e organizar os resultados das análises.

NumPy: Utilizada para operações numéricas de alta performance, servindo como base para as estruturas de dados do Pandas e para os cálculos realizados pelo Scikit-learn.

Matplotlib: A principal biblioteca para a criação de gráficos. Foi usada para gerar as figuras base para as visualizações, como o gráfico de barras de comparação de modelos e o gráfico de importância de features.

Seaborn: Construída sobre o Matplotlib, foi utilizada para criar visualizações estatísticas mais complexas e esteticamente aprimoradas, como a matriz de correlação (heatmap), os boxplots e os histogramas detalhados da análise exploratória.

Scikit-learn (sklearn): A biblioteca central para todo o fluxo de Machine Learning. As principais funções foram:

* model_selection: divisão treino/validação/teste;

* preprocessing: padronização (StandardScaler);

* impute: tratamento de valores ausentes (SimpleImputer);

* pipeline / compose: pipelines reprodutíveis;

* linear_model e ensemble: Logistic Regression, RandomForestClassifier, GradientBoostingClassifier;

* metrics: avaliação de desempenho;

* inspection: permutation importance;

* Imbalanced-learn (SMOTE): balanceamento de classes;

* Joblib: salvamento do modelo final.

# Comparação de Modelos
   
Três modelos foram comparados utilizando o conjunto de validação para uma seleção justa e imparcial. O objetivo era encontrar o modelo que não apenas tivesse a melhor performance geral (medida pelo F1-Score macro), mas que também atendesse à meta de negócio de atingir um Recall de pelo menos 85% para a classe de alto risco (high risk).

Os resultados no conjunto:

Modelo	F1-Score (macro)	Recall (high risk);

<img width="671" height="150" alt="image" src="https://github.com/user-attachments/assets/2744ea2f-5f0f-4601-93e8-54ed7453b99f" />

O modelo Random Forest foi então submetido a uma avaliação final no conjunto de teste, que continha dados completamente novos para o modelo. Os resultados confirmaram sua alta performance e capacidade de generalização.

# Classificação do Conjunto de Testes:

<img width="618" height="233" alt="image" src="https://github.com/user-attachments/assets/d941e83d-838c-4f5f-86fe-2b2e5c42dce9" />

O modelo final alcançou F1-Score Ponderado de 91%, indicando excelente desempenho geral.

O Recall para a classe High Risk foi de 93%, superando a meta de negócio de 85% e garantindo alta sensibilidade na identificação de gestantes de alto risco.

As métricas para a classe Low Risk mostram desempenho consistente e equilibrado, enquanto a classe Mid Risk apresentou valores levemente inferiores, indicando espaço para melhorias com novos atributos ou maior volume de dados.

# Análise dos Resultados:

O desempenho no conjunto de teste foi excelente. O modelo alcançou um F1-Score Ponderado de 91%, mostrando que é altamente eficaz. Mais importante, para a classe high risk, o modelo obteve um Recall de 93%, superando a meta de negócio e demonstrando que é extremamente confiável para sua principal função: identificar corretamente as gestantes de alto risco.

Resultados da Comparação de Modelos
Três modelos foram comparados utilizando o conjunto de validação para uma seleção justa e imparcial. O objetivo era encontrar o modelo que não apenas tivesse a melhor performance geral (medida pelo F1-Score macro), mas que também atendesse à meta de negócio de atingir um Recall de pelo menos 85% para a classe de alto risco (high risk).

Os resultados no conjunto de validação foram:

<img width="589" height="155" alt="image" src="https://github.com/user-attachments/assets/5c939c40-64c5-4c5b-a5ec-ca6e23c6453e" />

# Conclusões:

O modelo Random Forest foi escolhido como o mais adequado. Embora o Gradient Boosting tenha tido um recall ligeiramente maior para a classe high risk, o Random Forest apresentou um F1-Score geral significativamente superior, indicando um melhor equilíbrio entre precisão e recall em todas as classes, ao mesmo tempo em que cumpriu com sucesso a meta de recall de 88,2%.

Avaliação Final do Modelo Random Forest
O modelo Random Forest foi então submetido a uma avaliação final no conjunto de teste, que continha dados completamente novos para o modelo. Os resultados confirmaram sua alta performance e capacidade de generalização.

Relatório de Classificação Final (Conjunto de Teste):

<img width="590" height="227" alt="image" src="https://github.com/user-attachments/assets/6e691740-7e7c-4f68-9996-77787d9d0be9" />


O desempenho no conjunto de teste foi excelente. O modelo alcançou um F1-Score Ponderado de 91%, mostrando que é altamente eficaz. Mais importante, para a classe high risk, o modelo obteve um Recall de 93%, superando a meta de negócio e demonstrando que é extremamente confiável para sua principal função: identificar corretamente as gestantes de alto risco.

Sucesso na Criação de um Modelo Preditivo: O projeto foi bem-sucedido em desenvolver um modelo de Machine Learning (Random Forest) de alta performance, capaz de classificar o risco gestacional com 91% de acurácia geral (F1-Score).

Atendimento ao Objetivo de Negócio: A principal meta do projeto, que era criar um modelo que pudesse identificar com alta sensibilidade os casos de alto risco, foi plenamente alcançada, com um recall de 93% para essa classe no teste final.

Identificação de Preditores-Chave: O modelo confirmou que fatores clinicamente conhecidos, como glicemia, idade e pressão arterial, são os indicadores mais fortes de risco. Isso aumenta a confiança no modelo, pois suas decisões são baseadas em variáveis logicamente relevantes.

Validade da Metodologia: A utilização de um pipeline robusto com pré-processamento adequado, a divisão de dados em três conjuntos (treino, validação e teste) e a comparação de múltiplos algoritmos garantiram que o resultado final seja confiável, reprodutível e não superestimado. O projeto estabeleceu uma base sólida para futuras melhorias e para a potencial implantação da solução como uma ferramenta de apoio à decisão clínica.

