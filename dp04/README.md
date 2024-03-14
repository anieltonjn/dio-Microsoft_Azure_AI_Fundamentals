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

## Passo 2
### Configuração do Storage

### 2.1 Permitindo acesso anônimo ao Blob:

> [!NOTE]
> Como nosso laboratório é apenas didático, para aprender os princípios da inteligência artificial com o Azure, precisamos permitir o acesso anônimo ao blob para simplificar e facilitar nossas implementações.

![](../img/dp04_14.jpg)

- No painel esquerdo rolar até o bloco **Settings** e clicar em **Configuration**;

![](../img/dp04_15.jpg)

- A opção **Allow Blob anonymous** deve ser habilitada depois é só clicar em **Save**;

### 2.2 Criando o Container:

- Retornar a página inicial do Recurso de **Storage account**
- No painel esquerdo rolar até o bloco **Data Storage** e clicar em **Containers**;

![](../img/dp04_16.jpg)

- Selecione **+ Container** Um painel a direita será aberto:

![](../img/dp04_17.jpg)

- Depois de preenchido conforme orientação da Documentação selecione **Create**

## Passo 3
### Carregando os arquivos que serão utilizados para o enriquecimento de nossa IA.

- Baixar os arquivos do *dataset* público:
- O *dataset* utilizado é público e está disponível [aqui](https://aka.ms/mslearn-coffee-reviews)
- Após o download e a descompactação dos dados realizar o *upload* 

![](../img/dp04_18.jpg)

- Clicar em **Upload**.

![](../img/dp04_19.jpg)

- No painel **Upload blob** aberto no lado direito, arrastar os arquivos para a área indicada.

![](../img/dp04_20.jpg)

- Clicar em **Upload**.

![](../img/dp04_21.jpg)

## Passo 4
### Indexar os arquivos que serão utilizados para o enriquecimento de nossa IA.

- Depois armazenar os documentos, utilizar o serviço ***Azure IA Search*** para extrair insights deles.

![](../img/dp04_22.jpg)

- Nas abas selecionar **Import data**, para iniciar o assistente de importação:

> ***Atenção***: Selecionei a opção ***choose an existing connection*** para a associar o *container* onde foram armazenadas as avaliações dos clientes

![](../img/dp04_23.jpg)

- Clicar em **Add coginitive skills**

> [!NOTE]
> Apesar de ser um passo Opcional resolvi fazer!!!

![](../img/dp04_24.jpg)

- Temos três Configurações a realizar nas opções oferecidas: *Attach AI Services*, *Add enrichments*, *Save enrichments to a knowledge store*

![](../img/dp04_25.jpg)

- Em *Attach AI Services* Selecionar o nosso recurso:

![](../img/dp04_26.jpg)

- Em *Add enrichments*, configurar conforme a imagem acima:

![](../img/dp04_27.jpg)

- Ainda em *Add enrichments*, selecionar os campos: Extract location names, Extract key phrases, Detect sentiment, Generate captions from images.

![](../img/dp04_28.jpg)

- Em *Save enrichments to a knowledge store*, selecione: Image projection, Documents, Pages, Key phrases, Entities, Image details, Image references.

> [!NOTE]
> Vai aparecer mensagens em vermelho solicitando **uma cadeia de conexão de conta de armazenamento** clicar em ***Choose an existing connection***.

![](../img/dp04_30.jpg)

- Depois em **Create**

![](../img/dp04_31.jpg)

- Selecione ele e volte para concluir!!

![](../img/dp04_32.jpg)

- No campo **Azure blob projections**, selecione: Document. Após isso clicar em **Next: Customise target index**

![](../img/dp04_33.jpg)

- Na primeira página que aparecer configurar **the Index name** para **coffee-index**, manter no campo **key** a opção **metadata_storage_path**, marcar a *checkbox* o campo **filterable** da linha **content**, por fim **Next: Create an indexer**.

![](../img/dp04_34.jpg)

- Clicar **Submit**.

![](../img/dp04_35.jpg)

- Aguardar a notificação que a importação foi bem sucedida.

## Passo 5
### Consultando o índice.

### 5.1 Dentro do serviço ***Azure AI Search***, selecionar a opção ***Search explorer***:

![](../img/dp04_36.jpg)

~~~Python
{
    "search": "*",
    "count": true
}    # Verifica se a indexação esta funcionando e mostra os documentos
~~~

![](../img/dp04_37.jpg)

~~~Python
{
    "search": "locations: 'Chicago'", # Aqui pedi para pesquisar os documento com a localidade = Chicago
    "count": true # Aqui pedi para contar em quantos documentos o pesquisa foi encontrada
}
~~~

![](../img/dp04_38.jpg)

~~~Python
{
    "search": "sentiment:'negative'", # Consulta as ocorrencias com sentimento negativo
    "count": true
}
~~~

![](../img/dp04_39.jpg)

## Observações finais:      

As ferramentas de inteligência artificial do Azure facilitam a consulta emdocumentos, pesquisas e depoimentos, agilizando ainda mais a consulta de satisfação de empresas sobre seus produtos e serviços.