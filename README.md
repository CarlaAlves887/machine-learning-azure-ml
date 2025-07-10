# Trabalhar com Machine Learning na prática o Azure ML

Para a resolução deste projeto segui o tutorial do laboratório 01 [Explore Automated Machine Learning in Azure Machine Learning](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html), seguindo os passos abaixo:

# 1. Criar um espaço de trabalho do Azure Machine Learning

Selecionar `+ Create a resource`option

![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem1.png)

Na barra de pesquisa, procurar por `Machine Learning` e selecionar a opção `Azure Machine Learning`

![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem2.png)

Criar o novo `Azure Machine Learning` resoure com as seguintes configurações:
- **Subscription**: Selecionar a sua subscrição do azure.
- **Resource group**: Criar ou selecionar um resource group.
- **Name**: Defina um nome exclusivo para o seu worspace.
- **Region**: Selecionar East US.
- **Storage account**: Um novo storage account será criado por defeito para o seu workspace.
- **Key vault**: Um novo key vault será criado por defeito para o seu workspace.
- **Application insights**: Um novo application insights será criado por defeito para o seu workspace.
- **Container registry**: None (um será criado automaticamente na primeira vez que você implementar um modelo num container).

Selecionar `Review + Create` e aguarde uns minutos até que o deployment termine com sucesso

![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem3.png)

## Iniciar o Machine Learning Studio

Após o deployment terminar, selecione a opção `Launch studio` no seu Azure Machine Learning workspace, para abrir o Azure Machine Learning Studio.

![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem4.png)

# 2. Usar Machine Learning automatizado para treinar um modelo

No [Azure Machine Learning studio](https://ml.azure.com/), no menu lateral à esquerda selecionar a opção `ML automatizado`.

![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem5.png)

Criar uma nova tarefa ML automatizada com as seguintes configurações, clicando na opção `Nova tarefa de ML Automatizada`:

**Definições básicas:**

- **Nome da tarefa:** O campo `Nome da tarefa` já deve estar preenchido com um nome exclusivo. Mantenha-o como está
- **Nome da nova experimentação:** `mslearn-bike-rental`
- **Descrição:** Machine learning automatizado para previsão de aluguer de bicicletas
- **Etiquetas:** *nenhuma*

![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem6.png)

**Tipo de tarefa e dados:**

- **Selecionar tipo de tarefa:** Regression
- **Selecionar dados:** Crie um novo conjunto de dados com as seguintes configurações:

  - **Tipo de dados:**
    - **Nome:** `bike-rentals`
    - **Descrição:** `Historic bike rental data`
    - **Tipo:** Tabela (mltable)
   ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem7.png)

  - **Origem de dados:**
    - Selecionar **De ficheiros locais**
      ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem8.png)

  - **Tipo de armazenamento de destino:**
    - **Tipo do arquivo de dados:** Armazenamento de Blobs do Azure
    - **Nome:** `workspaceblobstore`
      ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem9.png)

  - **Seleção de MLtable:**
    - **Carregar pasta:** *Download e unzip a pasta que contém os dois arquivos que você precisa de enviar*  
      [https://aka.ms/bike-rentals](https://aka.ms/bike-rentals)
      ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem10.png)

> Selecionar **Criar**. Após a criação do conjunto de dados, selecione o conjunto de dados **bike-rentals** para continuar a enviar a tarefa de ML automatizado.
> ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem11.png)

**Definições de Tarefa**:

- **Tipo de tarefa:** Regressão
- **Dados:** `bike-rentals`
- **Coluna de destino:** `rentals` (integer)

- **Configuração adicional:**
  - **Métrica principal:** `NormalizedRootMeanSquaredError`
  - **Explicar o melhor modelo:** *Não selecionado*
  - **Ativar empilhamento de conjuntos:** *Não selecionado*
  - **Utilizar todos os modelos suportados:** *Não selecionado.* *Você restringirá a tarefa para testar apenas alguns algoritmos específicos.*
  - **Modelos permitidos:** *selecione apenas `RandomForest` e `LightGBM` — normalmente, você tentaria o máximo possível, mas cada modelo adicionado aumenta o tempo de execução do trabalho.*
    ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem12.png)
 
- **Limites:** Expandir esta seção
  - **Número máximo de avaliações:** `3`
  - **Máximo de avaliações simultâneas:** `3`
  - **Máximo de nós:** `3`
  - **Limiar de pontuação de métrica:** `0.085` (para o caso do modelo atingir uma pontuação métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termine.)
  - **Tempo limite da experimentação (minutos):** `15`
  - **Tempo limite de iteração (minutos) :** `15`
  - **Ativar cessação antecipada:** *Selecionado*
    ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem13.png)

- **Validar e testar:**
  - **Tipo de validação:** Divisão de validação de preparação
  - **Percentagem de validação dos dados:** 10
  - **Dados de teste:** Nenhum
    ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem14.png)

**Computação**:

- **Selecionar tipo de computação:** Sem servidor
- **Tipo de máquina virtual:** CPU
- **Camada de máquina virtual:** Dedicado
- **Tamanho da máquina virtual:** Standard_DS3_V2
- **Número de instâncias:** 1
  ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem15.png)

Envie a tarefa de treino clicando em `Submeter tarefa de preparação`. Ela será iniciada automaticamente.
Aguarde a conclusão do trabalho.

![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem16.png)

# 3. Análise o melhor modelo

Quanddo o trabalho de Machine Learning automatizado estiver concluído, você poderá rever o melhor modelo de treino.

1. Na tab `Descrição geral` do trabalho de Machine Learning automatizado, observe o resumo do melhor modelo. Selecione a descrição do campo `Nome do algoritmo` para ver os detalhes do melhor modelo.
   ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem17.png)

2. Na tab `Métricas` do trabalho de Machine Learning automatizado e observe os gráficos de `predicted_true` e `residuals`.
   ![](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/Imagem18.png)

# 4. Implantar e testar o modelo



### Dados de input utilizados para o teste (Pontos de extremidade)

[input.json](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/input.json)

