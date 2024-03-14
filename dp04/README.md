# Trabalhando com o serviço de índice de Pesquisa do Azure Cognitive Search

## Passo 1
### Aprovisionando os recursos necessários do Azure

Para realizar este laboratório, foi necessário aprovisionar, no [Portal do Azure](https://portal.azure.com/), os 3 serviços abaixo:

- ***Azure AI Search***: para gerenciará a indexação e a consulta;
- ***Azure AI Services***: para enriquecer os dados na fonte de dados com *insights* gerados por IA;
- ***Storage Account***: para armazenar os documentos brutos

> [!NOTE]
> Os 3 serviços precisaram ser aprovisionados no mesmo local (região), para permitir a integração entre eles

### 1.1 Aprovisionar o ***Azure AI Search***, na região ***East US***:

![](../img/dp04_01.jpg)

- Escolher **Create**;

![](../img/dp04_02.jpg)

- Clicar em **Review + create**;

![](../img/dp04_03.jpg)

- Clicar em **Create**;

![](../img/dp04_04.jpg)

- Aguardar até que o deploy esteja completo.

### 1.2 Aprovisionar o ***Azure AI Services***, na região ***East US***:

![](../img/dp04_05.jpg)

- Escolher **Create**;

![](../img/dp04_06.jpg)

- Clicar em **Review + create**;

![](../img/dp04_07.jpg)

- Clicar em **Create**;

![](../img/dp04_08.jpg)

- Aguardar até que o deploy esteja completo.

### 1.3 Aprovisionar o ***Storage Account***, na região ***East US***:

![](../img/dp04_09.jpg)

- Escolher **Create**;

![](../img/dp04_10.jpg)

- Clicar em **Review + create**;

![](../img/dp04_11.jpg)

- Clicar em **Create**;

![](../img/dp04_12.jpg)

- Aguardar até que o deploy esteja completo.

![](../img/dp04_13.jpg)

- Ao final teremos uma tela como esta mostrando os serviços necessários.