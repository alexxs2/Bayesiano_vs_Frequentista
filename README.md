[Parkinsons](https://archive.ics.uci.edu/dataset/174/parkinsons)

# Bayesiano vs. Frequentista: quem ganha na detecção de Parkinson?
🎯 Objetivo
Comparar a capacidade de modelos bayesianos e frequentistas para detectar Parkinson a partir de métricas de voz, em uma base desafiadora:

📉 195 observações,
⚠️ Muitos outliers,
🔀 Multicolinearidade severa (22 features altamente correlacionadas)

🔍 Metodologia 
1. Análise exploratória

📊 Boxplots para detectar outliers

📈 Gráfico de barras da distribuição de classes (75% “Sim”, 25% “Não”)

🔗 Matriz de correlação para destacar variáveis altamente correlacionadas

2. Pré‑processamento

⚖️ RobustScaler nas features, mitigando outliers

🧮 PCA para reduzir de 22 → 7 componentes (≥ 95% da variância), eliminando multicolinearidade

🔀 Separação em treino (70%) e teste (30%)

3. Modelagem Bayesiana
 
🧩 Dois modelos de mistura bayesiana para agrupamento, comparados via ELBO e posterior predictive checks

🏆 Selecionando o vencedor para gerar clusters

🔍 Cinco modelos de classificação bayesiana, com análise a priori/pôsteriori via PPC, escolhendo o melhor via ELBO e posterior predictive checks também

🏆  Escolhendo o modelo vencedor para validação no conjunto de teste

📊 Principais Métricas extraídas no teste: Acurácia, Sensitivity, Specificity, Precision, F1‑score, Prevalence e Balanced Accuracy

4. Modelagem Frequentista
   
🌲 Random Forest otimizado com Optuna

🦅 XGBoost também otimizado com Optuna

Extração das mesmas métricas no mesmo conjunto de teste

6. Comparação final
   
✅ Regressão Logística Bayesiana: acurácia de 89,8%, F1 93,5%, balanced accuracy 82,2%

✅ Random Forest: acurácia 91,5%, F1 94,6%, balanced accuracy 83,3%

✅ XGBoost: empata com Random Forest em todas as métricas-chave

💡 Principais aprendizados e resultados

O PCA foi muito importante para lidar com multicolinearidade severa da base.

A abordagem bayesiana oferece intervalos de credibilidade e robustez em pequenas amostras.

Os ensembles frequentistas capturam não linearidades e entregam leve vantagem em pontuais métricas de acurácia e F1.

Sensibilidade de 100% nos ensembles garantiu zero falsos negativos que é vital em diagnóstico médico.

[![Bayesiano vs Frequentista](https://colab.research.google.com/assets/colab-badge.svg "Bayesiano vs Frequentista")](https://colab.research.google.com/drive/1RGt11CPuKzxZs9aMgg0W8Vn51zU72svs?usp=sharing)
