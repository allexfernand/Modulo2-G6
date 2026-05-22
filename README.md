# Vitaliza · Retenção Preditiva

Sistema desenvolvido para a entrega do Módulo 2, com foco em análise exploratória de dados, modelo preditivo de churn e interface simples de inferência.

## Links Da Entrega

- Site publicado: https://modulo2-g6.vercel.app/
- Repositório GitHub: https://github.com/allexfernand/Modulo2-G6
- Backend Render: https://modulo2-g6.onrender.com
- Documentação da API: https://modulo2-g6.onrender.com/docs
- Notebook EDA: https://modulo2-g6.vercel.app/notebooks/eda_churn.ipynb
- Relatório visual EDA: https://modulo2-g6.vercel.app/notebooks/eda_churn_visual.html

Observação: o backend no Render pode levar alguns segundos para responder no primeiro acesso, caso o serviço esteja hibernado.

## Objetivo Do Projeto

O projeto estima o risco de churn de clientes de uma academia e traduz os sinais do modelo em ações de retenção. A solução combina:

- Upload de CSV para treinamento dinâmico.
- Dashboard EDA com visualizações exploratórias.
- Modelo preditivo com RandomForest.
- Interface de inferência para calcular probabilidade de churn.
- Personas comportamentais com clusters K-Means para leitura de negócio.
- Notebook e relatório visual como evidências formais da análise.

## Como Acessar E Testar

1. Acesse o site publicado: https://modulo2-g6.vercel.app/
2. Entre na aba `Upload CSV`.
3. Envie o arquivo `gym_churn_us.csv`.
4. Aguarde o treinamento do modelo.
5. Consulte as métricas de treino e o Dashboard EDA.
6. Acesse a aba `Inferência` para informar dados de um cliente e calcular o risco de churn.
7. Acesse a aba `Personas` para visualizar os clusters comportamentais K-Means.
8. Acesse a aba `Documentação` para ver o resumo técnico, links do notebook e relatório visual.

## Estrutura Do Repositório

```text
Modulo2-G6/
├── backend/
│   ├── main.py              # API FastAPI com treino, EDA e inferência
│   ├── requirements.txt     # Dependências do backend
│   ├── runtime.txt          # Versão do Python para deploy
│   └── model.pkl            # Modelo base, quando disponível
├── frontend/
│   └── index.html           # Interface web publicada na Vercel
├── notebooks/
│   ├── eda_churn.ipynb      # Notebook formal da EDA e modelo
│   ├── eda_churn_visual.html
│   ├── eda_churn_report.html
│   └── gym_churn_us.csv     # Base usada na análise
├── eda_report.md            # Insights acionáveis da EDA
├── vercel.json              # Configuração de deploy do frontend
└── README.md
```

## Funcionalidades Principais

- `Upload CSV`: treina o modelo no backend a partir da base enviada.
- `Inferência`: calcula a probabilidade de churn para um cliente.
- `Dashboard EDA`: mostra métricas, distribuição de churn, correlações, coortes, sobrevivência e segmentos diagnósticos.
- `Personas`: apresenta os clusters K-Means com perfis comportamentais e ações recomendadas.
- `Documentação`: resume arquitetura, features, interpretação do modelo e links dos artefatos formais.

## Stack Técnica

- Frontend: HTML, CSS e JavaScript puro.
- Backend: FastAPI.
- Machine Learning: scikit-learn, RandomForestClassifier e K-Means na camada de negócio.
- Dados e EDA: pandas, numpy e matplotlib.
- Deploy frontend: Vercel.
- Deploy backend: Render.

## Endpoints Do Backend

- `GET /`: health check da API.
- `POST /train`: recebe CSV, limpa dados, treina o modelo e retorna métricas.
- `POST /predict`: recebe dados de cliente e retorna probabilidade de churn.
- `POST /eda`: recebe CSV e retorna dados agregados para o Dashboard EDA.
- `GET /docs`: documentação interativa da API.

## Métricas E Evidências

O notebook `notebooks/eda_churn.ipynb` salva os outputs principais, incluindo:

- Carga e limpeza da base.
- Visualizações obrigatórias da EDA.
- Features derivadas.
- Métricas do modelo, incluindo ROC-AUC e classification report.
- Segmentação comportamental K-Means.

Na última execução salva no notebook:

- ROC-AUC: `0.965`
- Acurácia: `0.917`
- Precisão classe churn: `0.865`
- Recall classe churn: `0.816`

## Features Utilizadas Pelo Modelo

- `Lifetime`: meses como cliente.
- `Avg_class_frequency_current_month`: frequência de aulas no mês atual.
- `Age`: idade do cliente.
- `Contract_period`: duração do contrato.
- `Month_to_end_contract`: meses até o fim do contrato.
- `Avg_class_frequency_total`: frequência histórica de aulas.
- `Avg_additional_charges_total`: gastos extras na academia.
- `Group_visits`: participação em aulas em grupo.
- `Promo_friends`: entrada por indicação.
- `Partner`: vínculo com empresa parceira.
- `Near_Location`: proximidade da academia.

## Personas K-Means

A camada de negócio resume quatro perfis comportamentais:

- Cluster 0, Lucas: recém-chegado em fuga, maior churn e necessidade de onboarding.
- Cluster 1, Beatriz: leal anual, alta retenção e potencial de indicação.
- Cluster 2, Rafael: engajado mensal, bom uso e oportunidade de migração para plano anual.
- Cluster 3, Camila: médio em trânsito, risco diferido e necessidade de intervenção preventiva.

## Execução Local

Backend:

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload
```

Frontend:

Abra `frontend/index.html` no navegador ou use um servidor estático local.

## Observações Para Avaliação

O site publicado é o principal ponto de demonstração. O GitHub contém o código-fonte completo, e os artefatos formais da análise estão disponíveis no notebook e no relatório visual vinculados na aba `Documentação`.
