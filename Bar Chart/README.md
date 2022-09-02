<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>

<h3 align="center">Gráfico</h3>
<h5 align="center">Área, Barras, Colunas e Linhas</h5>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> Como aplicar e utilizar um gráfico de área, barras, colunas e linhas utilizando formulários no dashboard.
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Começando](#starting)
- [Estrutura](#structure)
- [Pesquisa](#search)
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>

![Exemplos de Gráfico de barras](https://i.imgur.com/EkGRGMo.png)

Um gráfico é uma representação visual de comparação entre elementos.Visualização de dois eixos (X e Y) indicando nome e valor de cada ítem. Ao passar o mouse sobre cada elemento, ele é ressaltado aparecendo uma pequena janela contendo o nome e valor do campo específico.

Nesse modelo, a estrutura e a visualização são criadas através de uma biblioteca JavaScript para criação dinâmica de gráficos chamada Fusion Charts. No código fonte, trazemos a opção de preencher o gráfico dinamicamente, atravez de uma pesquisa.

Esse modelo é específico para usuários que queiram montar utilizando a estrutura em formulário, visto que esses tipos de gráfico podem ser facilmente gerados usando a criação dinâmica de gráficos no menu de contexto, ao invéz de criar um novo 'formulário', escolhendo "cartão'.

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```

## Começando <a name = "starting"></a>

Inicialmente, é necessário criar um novo cartão do tipo “formulário” através do menu de contexto.

![Criando Cartão](https://i.imgur.com/Sx9hPLC.png)

Ao abrir a modal de edição, cole o código fonte no espaço de texto. Atente-se às dimensões desejadas. Esse modelo está com o padrão de altura em 500px e pode ser escolhida qualquer largura.

## Estrutura <a name = "structure"></a>

O código fonte é composto por uma estrutura padrão, composta por uma pequena parte HTML, apenas uma divisão identificada por um atributo 'id'. Dentro desse elemento será criado o gráfico pela biblioteca, por isso essa divisão está vazia. Ao ser montado, o gráfico de barras se adaptará a qualquer largura, porém está com a altura padrão de 495 pixels, para alterar esse valor, basta o usuário substituir o valor do campo 'height'.

```html
<div id="idChart" class="" style="height: 495px; margin: 0 auto;">
    <!-- O gráfico será criado aqui -->
</div>
```

Logo após o código fonte continua com a criação do JavaScript. Iniciando com uma função da criação do gráfico. Inicialmente é criada a lista (array) que vai conter todos os ítens que serão exibidos em barra. Cada ítem (separados por vírgula) deve conter dois campos, "label" que é um campo de texto onde deve ser inserido o nome do elemento e "value" que é um valor numérico referente ao componente.

Em seguida, é feita uma ordenação dessa lista, colocando no topo aqueles com o maior valor. Depois essa lista é cortada, deixando apenas os 15 primeiros valores. Caso o usuário queira aumentar a quantidade máxima de valores exibidos no gráfico, basta substituir o valor de '0 a 15' para de '0 a x'. Entretanto, caso não queira nenhum valor máximo, basta colocar duas barras "//" antes do comando "arrSelecao = array.slice(0, 15);".

```js
let arrayItens = [
    {
        label: "Elemento A",
        value: 9
    },{
        label: "Elemento B",
        value: 8
    },{
        label: "Elemento C",
        value: 7
    },{
        label: "Elemento D",
        value: 6
    },{
        label: "Elemento E",
        value: 5
    },{
        label: "Elemento F",
        value: 4
    },{
        label: "Elemento G",
        value: 3
    }
]
//Organiza os ítens do gráfico do maior 'value' para o menor
arrayItens.sort(function(a, b) {
  return b.value - a.value;
});
//Define a quantidade máxima de ítens exibidos no gráfico, nesse caso: 15
arrSelecao = array.slice(0, 15);
```
Depois é executada a biblioteca FusionCharts que vai configurar todas as informações adicionais e incorporar a lista ja criada. O valor do campo "renderAt" deve ser o 'id' do elemento HTML onde será inserido o gráfico. O campo "data" deve ser atribuido com o nome da variável onde está contida a lista.

Para customisação, é possível alterar o Título, Subtítulo e Nome do eixo Y substituindo respectivamente os valores dos campos "caption", "subCaption" e "yAxisName". Por padrão, a biblioteca monta o gráfico usando um tema de cores chamado 'fusion', o usuário pode alterar para algum outro tema aceito pela biblioteca que são:" fusion", "ocean", "candy", "carbon", "umber", "zune" e "gammel".


```js
FusionCharts.ready(function(){
    var chartObj = new FusionCharts({
        type: 'bar2d',
        renderAt: 'idChart',
        width: '100%',
        height: '100%',
        dataFormat: 'json',
        dataSource: {
            "chart": {
                "theme": "fusion", 
                "caption": "Título",
                "subCaption": "Subtítulo",
                "yAxisName": "Linha inferior"                       
            },
            "data": arrayItens
        }
    });
    chartObj.render();
});
```

No modelo apresentado, a lista (array) é feita dinamicamente por uma pesquisa e transmitido para a função que vai criar o gráfico.

## Pesquisa <a name = "search"></a>

Nesse exemplo a ideia do gráfico é comparar os usuários de uma rede com a quantidade de logs gerados e indexados no AvantData atravez do AvantAgent.

Para fazer a pesquisa, é utilizada uma função JavaScript, dentro dela é criada uma requisição (fetch) que vai fazer uma busca em algum banco de dados e trazer uma respota. Depois a resposta será mapeada para percorrer todos os usuários e a quantidade de ítens de cada, e criar um ítem da lista para cada usuário. Ao terminar, é executada a função de construção do gráfico passando como parâmetro a lista ja formatada.

```JavaScript
function searchData() {        
        // query de pesquisa
        const queryDet = {
            method: 'POST',
            headers: {'cluster': 'AvantData'},
            body: JSON.stringify({
                index: 'AvantAgent',
                size: 0,
                body: {
                    query: {
                        query_string: {
                            query: `agentHostName: *`
                        }
                    },
                    aggs: {
                        aggsItens: {
                            terms: {
                                "field": `agentHostName.keyword`,
                                "size": 5000
                            }
                        }
                    }
                }
            })
        };
        // Faz a pesquisa
        return fetch('/avantapi/avantData/search/customSearch', queryDet)
            .then(responseList => responseList.json())
            .then(responseList => {
               
                let arrayChart =[]
                if(responseList.aggregations) {
                    if(responseList.aggregations.aggsItens) {                        
                        let buckets = responseList.aggregations.aggsItens.buckets
                        
                        // Para cada dado da pesquisa, cria um item para a lista que será enviada para o chart
                        // utilizando 'label' e 'value'
                        for(i in buckets) {
                            arrayChart.push({
                                label: buckets[i].key,
                                value: buckets[i].doc_count
                            })
                        }
                    }
                }
                return arrayChart
            })
            .then(arrayChart =>{
                // Executa a função que cria o gráfico transmitindo a lista pronta
                createChart(arrayChart)
            })
    }
```

Nesse modelo, utilizamos uma busca dentro de um dos índices mais usados do AvantData, o AvantAgent. Como os dados dos índices no nosso sistema é, por padrão, indexado dentro de um banco de dados não relacional, utilizamos a [AvantAPI](https://avantapi.avantsec.com.br/) para fazer uma busca atravez do Custom Search (rota da nosa API em que mandamos uma query de pesquisa para o ElasticSearch e ela retorna o resultado).


## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [FusionCharts](https://github.com/fusioncharts) - Biblioteca de gráficos JavaScript que fornece gráficos interativos e responsivos