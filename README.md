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




### Dados de input utilizados para o teste (Pontos de extremidade)

[input.json](https://github.com/CarlaAlves887/machine-learning-azure-ml/blob/main/input.json)

