# Trabalhando com Machine Learning


## Passo 1

- Criar uma conta free na [Azure](https://azure.microsoft.com/pt-br/free).
- O cadastro é criado quando clicar nesse botão "Experimentar gratuitamente".

![](../img/dp01_01.jpg)

## Passo 2

- Entrar na plataforma do [Portal Azure](https://portal.azure.com).
- Pesquisar por "Azure Machine Learning" nesse campo de pesquisa selecionar Azure Machine Learning.

![](../img/dp01_02.jpg)

## Passo 3
- Apertar em "Criar", para criar um Novo workspace.

![](../img/dp01_03.jpg)

## Passo 4

- Criar um novo "resource group", criar um "nome", a "região", e Apertar em "Examinar + criar".

![](../img/dp01_01.jpg)

- Esperar até que a validação ser aprovada, e então Apertar em "criar".

![](../img/dp01_05.jpg)

## Passo 5

- A implantação está em andamento e pode ser acompanhada na tela que será aberta automaticamente.

![](../img/dp01_06.jpg)

- Esta é a tela de finalização do deploy. Agora podemos Apertar em "ir para o recurso".

![](../img/dp01_07.jpg)

- Na tela do recurso, apertar em "Iniciar estúdio".

![](../img/dp01_08.jpg)

## Passo 6

- O diretório do workspace é então aberto.
- Posso visualizar todos os workspaces existentes, Apertando em "Todos os Espaços de Trabalho".

![](../img/dp01_09.jpg)

-  Aperte No workspace que você criou.

![](../img/dp01_10.jpg)

## Passo 7

- O workspace escolhido é aberto.

![](../img/dp01_11.jpg)

- Selecione no ambiente ML automatizado e depois em criar um Novo trabalho de ML automatizado.


![](../img/dp01_12.jpg)

## Passo 8

- Preencher os dados do job com as informações (fornecidas pela documentação da Microsoft).

- 8.1 -> Preenchimento das informações básicas. Quando Terminar de Preencher Aperte em Avançar.

![](../img/dp01_13.jpg)

- 8.2 -> Escolha do tipo de tarefa (Regressão) e Aperte em criar.

![](../img/dp01_14.jpg)

- 8.3 -> Preencha as informações e Aperte em Avançar.
  
![](../img/dp01_15.jpg)

- 8.4 -> Escolha a fonte dos dados e Aperte em Avançar.

![](../img/dp01_16.jpg)

- 8.5 -> Escreva a url e Aperte em Avançar. A url passa por uma verificação e validação.

![](../img/dp01_17.jpg)

- 8.6 -> Os dados devem estar com as seguintes configurações e quando terminar de preencher apertar em Avançar.

![](../img/dp01_18.jpg)

- 8.7 -> Ele traz uma visualização do Esquema. Não é necessário alterar nenhuma informação e Aperte em Avançar.

![](../img/dp01_19.jpg)

- 8.8 -> Por fim, ele traz todas informações para Examinar, e Aperte em "criar", para criar o Base de Dados.

![](../img/dp01_20.jpg)

- 8.9 -> Para avançar, selecione a Base de Dados, e Aperte em "Avançar".

![](../img/dp01_21.jpg)

- 8.10 -> Configurações da tarefa.

- Tipo de tarefa: Regressão, Conjunto de dados: aluguel de bicicletas, Coluna de destino: Aluguéis (inteiro)

![](../img/dp01_22.jpg)

- Configurações adicionais: Métrica primária: raiz do erro quadrático médio normalizado, Explique o melhor modelo: Não selecionado, Usar todos os modelos suportados: Desmarcado, Modelos permitidos: Selecione apenas RandomForest e LightGBM

![](../img/dp01_23.jpg)

- Limites: Expanda esta seção, Máximo de testes: 3, Máximo de testes simultâneos: 3, Máximo de nós: 3, Limite de pontuação da métrica: 0.085, Tempo limite: 15, Tempo limite de iteração: 15, Habilitar rescisão antecipada: selecionado
- Validação e teste: Tipo de validação: divisão de validação de treinamento, Porcentagem de dados de validação: 10, Conjunto de dados de teste: Nenhum

![](../img/dp01_24.jpg)

- 8.11 -> Não é preciso escrever nenhuma informação diferente na tela Computação.

![](../img/dp01_25.jpg)

- 8.12 -> As informações são trazidas e pode enviar o trabalho de treinamento.

![](../img/dp01_26.jpg)

## Passo 9
- O modelo inicia o treinamento até a finalização.

![](../img/dp01_27.jpg)

## Passo 10
- Validar métricas.
- 10.1 -> Acessar as informações do modelo conforme imagem abaixo.

![](../img/dp01_28.jpg)

- 10.2 -> Acessar o trabalho.

![](../img/dp01_29.jpg)

## Passo 11

- Avaliar o melhor modelo: Quando o trabalho automatizado de aprendizado de máquina for concluído, você poderá revisar o melhor modelo treinado.
- Selecione o texto em Nome do algoritmo do melhor modelo para visualizar seus detalhes

![](../img/dp01_30.jpg)

- Selecione a guia Métricas e selecione os gráficos
residuais e predito_true se eles ainda não estiveremselecionados.

![](../img/dp01_31.jpg)

- Revise os gráficos que mostram o desempenho do modelo. O gráfico de resíduos mostra os resíduos
como um histograma. O gráfico predito_true compara os valores previstos com os valores verdadeiros.

![](../img/dp01_32.jpg)

## Passo 12
- Implantar e Testar do Modelo.
- 12.1 -> De volta à página do modelo, escolhemos a opção de Implantar Serviço Web.

![](../img/dp01_33.jpg)

- 12.2 -> Preencher com as informações fornecidas na documentação e Apertar em "Implantar".

![](../img/dp01_34.jpg)

- 12.3 -> Após receber a notificação de que a Implantação foi concluída, no menu esquerdo, vamos Apertar na aba Pontos de extremidade e depois no ponto recém criado.

![](../img/dp01_35.jpg)

- 12.4 -> Na tela de Pontos de extremidade, confirma o status "Succeeded" do Implantar, e Apertamos na aba "Testar"

![](../img/dp01_36.jpg)

- 12.5 -> Para o teste, utilizei o json abaixo:

  
 ```
 {
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }

```

![](../img/dp01_37.jpg)

- 12.6 -> Resultado do Teste.

 ```
{
  "Results": [
    350.6746367646949
  ]
}

```

![](../img/dp01_38.jpg)