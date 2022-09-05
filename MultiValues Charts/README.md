<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>

<h3 align="center">Gráficos de Valores Múltiplos</h3>
<h5 align="center">Linha, Área, Coluna e Barra</h5>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> (Descrição dos Gráficos)
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Começando](#starting)
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>

![Exemplos de Gráficos](https://i.imgur.com/iwWqfn7.png)

Um gráfico é uma representação visual de comparação entre elementos. Visualização de dois eixos (X e Y) indicando nome e valor de cada ítem. Ao passar o mouse sobre cada elemento, ele é ressaltado aparecendo uma pequena janela contendo o nome e valor do campo específico. Esse modelo pode ser usado para criar um gráfico dos tipos <i>Linha, Área, Barras e Colunas</i> com exatamente a mesma estrutura, diferenciando apenas o atributo "type" (tipo).

A diferença do<i> gráfico de valores múltiplos </i>e <i>[gráfico simples](https://github.com/Avant-Data/Dashboards/tree/master/Simple%20Charts)</i> está na quantidade de elementos por valor. Ou seja, o gráfico simples consegue apenas apresentar um ítem (eixo Y) por ítem (eixo X), enquanto o gráfico de valores múltiploes consegue apresentar varios valores (eixo X) por ítem (eixo Y).

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

O código fonte é composto por uma estrutura padrão, composta por uma pequena parte HTML, apenas uma divisão identificada por um atributo 'id'. Dentro desse elemento será criado o gráfico pela biblioteca, por isso essa divisão está vazia. Ao ser montado, o gráfico se adaptará a qualquer largura, porém está com a altura padrão de 495 pixels, para alterar esse valor, basta o usuário substituir o valor do campo 'height'.

```html
<div id="idDivValues" style="height:495px;">
    <!-- O gráfico será criado aqui -->
</div>
```
Logo após, o código fonte continua com a criação do JavaScript. Iniciando com uma função de criação do gráfico que inicia com a declaração de uma variável que vcontendo todas os parâmetros que vão ser apresentados em uma grande estrutura JSON.

Começando com o campo "chart" que vai indicar a customização de componentes gerais como título, subtítulo, nome do eixo X, tema de cores ("fusion", "ocean", "candy", "carbon", "umber", "zune" e "gammel"). O subcampo "numberPrefix" é opcional e vai acrescentar aos valores um texto prefixo ('R$' no caso).

O segundo campo "categories" é onde deve ser criado o eixo X. A lista contem varios campos "label" que contéma denominação de cada ítem do eixo X. Observa-se que após o atributo com valor "Sexta" existe uma diferente extrutura de objeto que monta uma <i>linha de de indicação</i> facultativa, ou seja, não conta como um ítem do eixo X, serve apenas como indicação de algum significado que não faz diferença alguma nos valores do gráfico, nesse caso serve para indicar o início do fim de semana, sendo uma parte completamente dispensável e podendo ser apagada sem nenhum impacto no código.

A terceira composição é feita dentro do campo "dataset" que é onde serão inseridas todas as litas de valores do eixo Y relacionadas ao eixo X pela órdem em que aparecem. Cada lista é indicada por uma "seriesname" que se trata do nome do contexto daquela lista, e todos os ítem são listados como valores do campo "value". Esse exempĺo é composto por duas listas: "Exemplo Gastos" e "Exemplo Lucro", mas a quantidade de eixos Y podem ser adicionadas a gosto do usuário seguindo a mesma estrutura. É importante ressaltar que a quantidade de ítens dessas listas precisam ser equivalentes com a quantidade de listas do eixo X (categories).

A quarta parte se trata das linhas de referência no campo "trendlines". São linhas que aparecerão como uma faixa de referência de algum valor predeterminado baseado no eixo Y. Também é um campo facultativo. Geralmente são usadas para traçar metas, médias, máximas ou alguma indicação.

```js
let dataValues = {
            "chart": {
                "caption": "Título",
                "subCaption": "Subtítulo",
                "xAxisName": "Dia",
                "theme": "fusion",
                "numberPrefix": "R$ "
            },
            "categories": [
                {                       // Bloco dos nomes dos ítens
                    "category": [
                        {
                            "label": "Segunda"
                        },
                        {
                            "label": "Terça"
                        },
                        {
                            "label": "Quarta"
                        },
                        {
                            "label": "Quinta"
                        },
                        {
                            "label": "Sexta"
                        },
                        {    // Linha vertical de indicação facultativa
                            "vline": "true",
                            "lineposition": "0",
                            "color": "#6baa01",
                            "labelHAlign": "center",
                            "labelPosition": "0",
                            "label": "FDS",
                            "dashed": "1"
                        },
                        {
                            "label": "Sábado"
                        },
                        {
                            "label": "Domingo"
                        }
                    ]
                }
            ],
            "dataset": [
                {                       // Bloco do primeiro grupo de Valores
                    "seriesname": "Exemplo Gastos",  
                    "data": [
                        {
                            "value": 200
                        },
                        {
                            "value": 350
                        },
                        {
                            "value": 500
                        },
                        {
                            "value": 100
                        },
                        {
                            "value": 140
                        },
                        {
                            "value": 630
                        },
                        {
                            "value": 540
                        }
                    ]
                },
                {                       // Bloco do segundo grupo de valores
                    "seriesname": "Exemplo Lucro",
                    "data": [
                        {
                            "value": 750
                        },
                        {
                            "value": 850
                        },
                        {
                            "value": 560
                        },
                        {
                            "value": 690
                        },
                        {
                            "value": 900
                        },
                        {
                            "value": 550
                        },
                        {
                            "value": 630
                        }
                    ]
                }
            ],
            "trendlines": [
                {                   // Bloco das linhas de referência
                    "line": [
                        {
                            "startvalue": 350,                  // Altura (Valor) eixo Y
                            "color": "#e96817;",                // Cor
                            "displayvalue": "Média{br}Gastos",  // Nome
                            "valueOnRight": "1",                // Valor à direita
                            "thickness": "2"                    // Grossura da linha
                        },
                        {
                            "startvalue": 705,                  // Altura (Valor) eixo Y
                            "color": "#38a0a4",                 // Cor
                            "displayvalue": "Media{br}Lucro",   // Nome
                            "valueOnRight": "1",                // Valor a direita
                            "thickness": "2"                    // Grossura da linha
                        }
                    ]
                }
            ]
        }
```

Depois é executada a biblioteca FusionCharts que vai configurar todas as informações adicionais e incorporar a lista ja criada. O valor do campo "renderAt" deve ser o 'id' do elemento HTML onde será inserido o gráfico. O campo "data" deve ser atribuido com o nome da variável onde está contida a lista. O campo "type" é onde o usuário vai escolher o formato do gráfico, sendo ele de área (msarea), barras (msbar2D), colunas (mscolumn2d) ou linha (msline).

```js
FusionCharts.ready(function(){
    var chartObj = new FusionCharts({
        type: 'msarea',       // tipo área: msarea   Tipo barra: msbar2D   Tipo linha: msline  Tipo colunas: mscolumn2d
        renderAt: 'idDivValues',
        width: '100%',
        height: '100%',
        dataFormat: 'json',
        dataSource: dataValues
    });
    chartObj.render();
});
```


## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [FusionCharts](https://github.com/fusioncharts) - Biblioteca de gráficos JavaScript que fornece gráficos interativos e responsivos