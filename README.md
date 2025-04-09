💳 Previsão de Inadimplência com MLP e Random Forest

Este projeto tem como objetivo prever inadimplência de clientes com base em dados de crédito, comparando dois modelos de machine learning: uma Rede Neural Multicamadas (MLP) e uma Floresta Aleatória (Random Forest).


📁 Estrutura do Projeto

credit-default-prediction/


│
├── credit_default_mlp_vs_rf.ipynb  # Notebook principal com análise e modelagem
├── credit.csv                      # Dataset original
├── README.md                       # Este arquivo
└── requirements.txt                # Dependências do projeto


🧠 Objetivo
Avaliar e comparar o desempenho de uma Rede Neural (MLP) e de um modelo Random Forest na tarefa de classificação binária (inadimplente vs adimplente), com foco especial no recall da classe 1, crucial para aplicações bancárias.



📊 Conjunto de dados

Fonte: Dados sintéticos de crédito

Amostras: 30.000 clientes

Variável alvo: target (0 = adimplente, 1 = inadimplente)

Principais variáveis:

LIMIT_BAL: limite de crédito

AGE: idade

PAY_0, PAY_2, ...: histórico de pagamento

BILL_AMT1 a BILL_AMT6: valores de faturas

PAY_AMT1a PAY_AMT6: valores pagos

🧼 Pré-processamento

Correção de dados inconsistentes

Normalização comMinMaxScaler

Balanceamento com SMOTE (classe 1 estava sub-representada)

Divisão treino/teste com train_test_split (70/30)

📌 Modelos Utilizados

🔹 1. MLP (Rede Neural)

Camadas: 64 → 32 → 2

Ativações: ReLU e Softmax

Regularização: Dropout + EarlyStopping

Otimizador: Adam

Métrica-chave: Recall da classe 1

🔹 2. Random Forest

Estimadores: 100 árvores

Critério: Gini

Interpretação: Feature importance nativa

AUC: calculado com roc_auc_score

📈 Resultados Comparativos

Métrica	MLP	Floresta aleatória

Acurácia	70,5%	84,6% ✅

Precisão (	76,3	87,3% ✅

Recordar (1)	59,7	81,1% ✅

Pontuação F1 (1)	67,0%	84,1% ✅

AUC	~0,78	0,92 ✅

Nota: A Random Forest apresentou recall acima de 80% para a classe 1 (inadimplentes), superando significativamente o modelo MLP, o que é vital para minimizar perdas financeiras em instituições bancárias.

📌 Variáveis Mais Relevantes (Random Forest)


1. PAY_0         (status de pagamento recente) 🔥
2. LIMIT_BAL     (limite de crédito)
3. AGE           (idade)
4. BILL_AMT1-6   (valores de faturas)
5. PAY_AMT1-6    (valores pagos)
6. PAY_2         (status de pagamento anterior)
7. 
O histórico recente de pagamento (especialmente PAY_0) foi o fator mais determinante na previsão de inadimplência.

🔍 Conclusões

✅Random Forest superou o modelo MLP em todas as métricas relevantes.

✅ Interpretação de variáveis torna o modelo Random Forest mais confiável e auditável para uso em sistemas financeiros.

⚠️ MLP ainda apresentou recall abaixo de 60% para inadimplentes, o que representa um risco maior na prática.

▶️ Como Rodar


git clone https://github.com/seuusuario/credit-default-prediction.git

cd credit-default-prediction
Instale as dependências:


pip install -r requirements.txt

Execute o notebook:


jupyter notebook credit_default_mlp_vs_rf.ipynb

🛠️ Tecnologias Usadas
Python 3.11

Pandas, NumPy, Seaborn, Matplotlib

Scikit-aprendizagem

Aprendizagem desequilibrada (SMOTE)

TensorFlow / Keras

📚
Este projeto é open-source para fins educacionais e de pesquisa. Sinta-se livre para utilizar, modificar e contribuir.

