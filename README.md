# Classificacao_de_Risco_Gestacional_com_Machine_Learning

Visão Geral do Projeto

Este projeto apresenta uma solução completa de Machine Learning para a classificação do risco gestacional. O objetivo principal é desenvolver um modelo preditivo robusto, capaz de classificar gestantes em três níveis de risco — baixo, médio e alto — com base em seus dados vitais (idade, pressão arterial, glicemia, etc.).

O foco estratégico do projeto é maximizar a identificação correta de pacientes de alto risco, fornecendo uma ferramenta de apoio à decisão para a priorização de cuidados médicos. O modelo campeão, Random Forest, alcançou um F1-Score (macro) de 91% em dados de teste, demonstrando alta eficácia.

Dataset

O conjunto de dados utilizado é o "Maternal Health Risk Data Set". Ele contém dados anônimos sobre os sinais vitais de gestantes.

Fonte: Maternal Health Risk Data Set

As variáveis utilizadas:

Age: Idade da gestante (em anos).

SystolicBP: Pressão Arterial Sistólica (em mm Hg) - Corresponde ao valor máximo da pressão arterial durante a contração do coração.

DiastolicBP: Pressão Arterial Diastólica (em mm Hg) - Corresponde ao valor mínimo da pressão arterial durante o relaxamento do coração.

BS: Nível de Glicose no Sangue (Glicemia) - Mede a concentração de açúcar no sangue.

BodyTemp: Temperatura Corporal.

HeartRate: Frequência Cardíaca (em batimentos por minuto - bpm).

RiskLevel: Nível de Risco Gestacional (Variável-Alvo) - A categoria de risco associada à saúde da gestante (low risk, mid risk, high risk).

Bibliotecas utilizadas

Manipulação e Análise de Dados
Pandas: Biblioteca fundamental para o projeto. Foi usada para carregar o dataset, manipular os dados em DataFrames, realizar a limpeza, criar novas colunas (engenharia de atributos) e organizar os resultados das análises.

NumPy: Utilizada para operações numéricas de alta performance, servindo como base para as estruturas de dados do Pandas e para os cálculos realizados pelo Scikit-learn.

Visualização de Dados
Matplotlib: A principal biblioteca para a criação de gráficos. Foi usada para gerar as figuras base para as visualizações, como o gráfico de barras de comparação de modelos e o gráfico de importância de features.

Seaborn: Construída sobre o Matplotlib, foi utilizada para criar visualizações estatísticas mais complexas e esteticamente aprimoradas, como a matriz de correlação (heatmap), os boxplots e os histogramas detalhados da análise exploratória.

Machine Learning e Modelagem
Scikit-learn (sklearn): A biblioteca central para todo o fluxo de Machine Learning. Seus módulos foram essenciais para:

model_selection: Dividir os dados nos conjuntos de treino, validação e teste de forma estratificada (train_test_split).

preprocessing: Padronizar as features numéricas para que tivessem a mesma escala (StandardScaler).

impute: Incluir uma etapa de tratamento de valores ausentes no pipeline (SimpleImputer) como boa prática.

pipeline e compose: Criar um fluxo de trabalho de pré-processamento robusto e reprodutível (Pipeline, ColumnTransformer), evitando o vazamento de dados.

linear_model e ensemble: Fornecer os algoritmos de classificação utilizados: LogisticRegression (baseline), RandomForestClassifier e GradientBoostingClassifier.

metrics: Avaliar o desempenho dos modelos através do classification_report, confusion_matrix, entre outras métricas.

inspection: Calcular a importância das features no modelo final com a técnica de permutation_importance.

Joblib: Utilizada especificamente para salvar o objeto do pipeline do modelo final treinado em um arquivo (.joblib), permitindo que ele seja carregado e reutilizado posteriormente sem a necessidade de um novo treinamento.

Apresentação Final dos Resultados e Conclusões do Projeto
O projeto teve como objetivo desenvolver um modelo de Machine Learning robusto para classificar o risco gestacional. Após as etapas de análise exploratória e pré-processamento dos dados, foram treinados e avaliados múltiplos algoritmos para selecionar a solução mais eficaz.

1. Resultados da Comparação de Modelos
   
Três modelos foram comparados utilizando o conjunto de validação para uma seleção justa e imparcial. O objetivo era encontrar o modelo que não apenas tivesse a melhor performance geral (medida pelo F1-Score macro), mas que também atendesse à meta de negócio de atingir um Recall de pelo menos 85% para a classe de alto risco (high risk).

Os resultados no conjunto de validação foram:

Modelo	F1-Score (macro)	Recall (high risk)
Random Forest	0.916	0.882
Gradient Boosting	0.893	0.941
Logistic Regression	0.655	0.588

Avaliação com o modelo Random Forest - Modelo com melhor adequaccao
 
O modelo Random Forest foi então submetido a uma avaliação final no conjunto de teste, que continha dados completamente novos para o modelo. Os resultados confirmaram sua alta performance e capacidade de generalização.

Relatório de Classificação Final (Conjunto de Teste):

Classe	Precisão	Recall	F1-Score
low risk	0.95	0.95	0.95
mid risk	0.86	0.82	0.84
high risk	0.90	0.93	0.91
Média Macro	0.90	0.90	0.90
Média Ponderada	0.91	0.91	0.91

Análise dos Resultados Finais:
O desempenho no conjunto de teste foi excelente. O modelo alcançou um F1-Score Ponderado de 91%, mostrando que é altamente eficaz. Mais importante, para a classe high risk, o modelo obteve um Recall de 93%, superando a meta de negócio e demonstrando que é extremamente confiável para sua principal função: identificar corretamente as gestantes de alto risco.

Com certeza. Com base em toda a análise realizada no notebook MVP_Risco_Materno_Combinado (1).ipynb, preparei um resumo completo que apresenta todos os resultados encontrados, junto com as conclusões do projeto.

Apresentação Final dos Resultados e Conclusões do Projeto
O projeto teve como objetivo desenvolver um modelo de Machine Learning robusto para classificar o risco gestacional. Após as etapas de análise exploratória e pré-processamento dos dados, foram treinados e avaliados múltiplos algoritmos para selecionar a solução mais eficaz.

1. Resultados da Comparação de Modelos
Três modelos foram comparados utilizando o conjunto de validação para uma seleção justa e imparcial. O objetivo era encontrar o modelo que não apenas tivesse a melhor performance geral (medida pelo F1-Score macro), mas que também atendesse à meta de negócio de atingir um Recall de pelo menos 85% para a classe de alto risco (high risk).

Os resultados no conjunto de validação foram:

Modelo	F1-Score (macro)	Recall (high risk)
Random Forest	0.916	0.882
Gradient Boosting	0.893	0.941
Logistic Regression	0.655	0.588


Conclusão da Seleção:

O modelo Random Forest foi escolhido como o mais adequado. Embora o Gradient Boosting tenha tido um recall ligeiramente maior para a classe high risk, o Random Forest apresentou um F1-Score geral significativamente superior, indicando um melhor equilíbrio entre precisão e recall em todas as classes, ao mesmo tempo em que cumpriu com sucesso a meta de recall de 88,2%.

2. Avaliação Final do Modelo Random Forest
O modelo Random Forest foi então submetido a uma avaliação final no conjunto de teste, que continha dados completamente novos para o modelo. Os resultados confirmaram sua alta performance e capacidade de generalização.

Relatório de Classificação Final (Conjunto de Teste):

Classe	Precisão	Recall	F1-Score
low risk	0.95	0.95	0.95
mid risk	0.86	0.82	0.84
high risk	0.90	0.93	0.91
Média Macro	0.90	0.90	0.90
Média Ponderada	0.91	0.91	0.91

Análise dos Resultados Finais:
O desempenho no conjunto de teste foi excelente. O modelo alcançou um F1-Score Ponderado de 91%, mostrando que é altamente eficaz. Mais importante, para a classe high risk, o modelo obteve um Recall de 93%, superando a meta de negócio e demonstrando que é extremamente confiável para sua principal função: identificar corretamente as gestantes de alto risco.

Análise dos Fatores de Risco

Para entender quais fatores mais influenciam as previsões do modelo, foi utilizada a técnica de Permutation Importance. Esta análise revelou os principais indicadores de risco gestacional, em ordem de importância:

BS (Nível de Glicose no Sangue): De longe, o fator mais decisivo para o modelo;

Age (Idade): A idade da gestante foi o segundo preditor mais influente;

SystolicBP (Pressão Arterial Sistólica): A pressão sistólica se mostrou um indicador crucial;

DiastolicBP (Pressão Arterial Diastólica): Também relevante, embora com menor impacto que a sistólica;

HeartRate (Frequência Cardíaca): Contribuiu de forma moderada para as previsões;

Conclusões Gerais do Projeto:

Sucesso na Criação de um Modelo Preditivo: O projeto foi bem-sucedido em desenvolver um modelo de Machine Learning (Random Forest) de alta performance, capaz de classificar o risco gestacional com 91% de acurácia geral (F1-Score).

Atendimento ao Objetivo de Negócio: A principal meta do projeto, que era criar um modelo que pudesse identificar com alta sensibilidade os casos de alto risco, foi plenamente alcançada, com um recall de 93% para essa classe no teste final.

Identificação de Preditores-Chave: O modelo confirmou que fatores clinicamente conhecidos, como glicemia, idade e pressão arterial, são os indicadores mais fortes de risco. Isso aumenta a confiança no modelo, pois suas decisões são baseadas em variáveis logicamente relevantes.

Validade da Metodologia: A utilização de um pipeline robusto com pré-processamento adequado, a divisão de dados em três conjuntos (treino, validação e teste) e a comparação de múltiplos algoritmos garantiram que o resultado final seja confiável, reprodutível e não superestimado. O projeto estabeleceu uma base sólida para futuras melhorias e para a potencial implantação da solução como uma ferramenta de apoio à decisão clínica.

