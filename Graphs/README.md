<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>

<h3 align="center">Grafos</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> Como aplicar e utilizar um grafo de vínculos utilizando formulários no dashboard.
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Peculiaridades](#peculiar)
- [Começando](#starting)
- [Estrutura](#structure)
- [Pesquisa](#search)
- [Aparência](#style)
- [Precauções](#precaution)
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>

![Exemplo movimentação](https://i.imgur.com/shblPGd.png)

Grafo é uma representação gráfica de valores ligados uns aos outros através de ralações, criando pontos e linhas para moldar uma visualização. Os pontos são chamados de <i>nós</i>, as linhas de <i>relações</i>. O AvantData disponibiliza toda a configuração e ultilização dessa ferramenta dentro do módulo AvantGraph, mas podem também ser criados dentro do dashboard.

Nesse modelo,a  estrutura e a visualização são criadas através de uma biblioteca JavaScript para criação dinâmica de  grafos chamada Vis Network. No código fonte, trazemos a opção de preencher o gráfico dinamicamente, atravez de uma pesquisa.

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```

## Peculiaridades <a name = "peculiar"></a>

Esse tipo de gráfico traz interações especiais que os diferenciam dos demais. Em sua configuração pode ser habilitada a interação com mouse que imita as regras da física no mundo real, dessa forma o usuário pode arrastar nós e linhas criando animações elásticas e vibrantes. Ao clicar em um nó ou relação, esse elemento é ressaltado. Ao descansar o mouse sobre algum elemente, uma janela aparece trazendo o título específico dele. Ao rolar o scroll do mouse sobre o gráfico é ajusatado o zoon.

<!-- ![Exemplo movimentação](https://i.imgur.com/27hq4hG.mp4) -->

## Começando <a name = "starting"></a>

Inicialmente, é necessário criar um novo cartão do tipo “formulário” através do menu de contexto.
Ao abrir a modal de edição, cole o código fonte no espaço de texto. Atente-se às dimensões desejadas. Esse modelo está com o padrão de altura em 500px e pode ser escolhida qualquer largura.

![Criando Cartão](https://i.imgur.com/Sx9hPLC.png)

Esse modelo também pode usar as opções de configução de cores e visualização na tela de AvantGraph -Aparências, para isso é necessário ter alguma opção salva no catálogo para ser usada, preferencialmente alguma que seja o <i>modelo padrão</i>.

Nessa configuração é possível alterar cores de cada nó, assim como formato e tamanho, borda emuitas opções. Também trazendo muitas opções para modificar as relações, mudar como as interações são feitas ou reconfigurar as regras de física do modelo.

![Criando Cartão](https://i.imgur.com/i6Cy9Df.png)

## Estrutura <a name = "structure"></a>

O código fonte é composto por uma pequena parte em HTML. Logo nó início é feita a importação dos arquivos da biblioteca usados para fazer funcionar todo o gráfico. Depois  é criado o título e subtítulo, e depois, em outro bloco, é criado uma divisão que receberá o grafo.

```html
<head> <!--Bloco da importação da biblioteca -->
    <script defer type="text/javascript" src="/AvantdataNovo/public/js/visJs/vis-network.min.js"></script>
</head>

<!-- Bloco do título -->
<div class="p-3" style=" font-family: 'Bahnschrift', sans-serif;background-color: #38a0a4; color: white;">    
    <h4>Título</h4>
    <h6>Subtítulo</h6>
</div>

<!-- Bloco do grafo -->
<div id="divGraphStands" style="height: 495px;">
    <!-- O grafo será inserido aqui-->
</div>
```
Caso queira alterar as cores, é necessário mudar alguns atributos básicos de cor, entre eles o “background-color” ou “color”. Nessa linguagem as faixas de cores podem ser descritas de três formas: usando padrão RGB, padrão Hexadecimal ou nomeando cores básicas em inglês.

```
color=" blue ;"         --> Cores básicas
color=" #38a0a3 ;"      --> Formato Hexadecimal
color=" 255 250 250 ;"  --> Formato RGB
```

A estrutura básica para criação de um grafo é feita dentro de uma função JavaScript. É necesário criar uma variável em formato de JSON  que deverá conter dois pricipais campos: 'nodes' e 'edges'.<a name = "node_relation"></a>

'Nodes' vai conter uma lista com todos os nós. Cada ítem dessa lista precisa conter subcampos:

  * id = Será a identificação daquele nó. Precisa ser um valor único, podendo ser texto ou numérico.
  * label = Será o nome daquele nó que aparecerá como rótulo no momento da visualização.
  * title = Será o texto que vai aparecer ao descansar o mouse por cima do nó.
  * attributes = Caso o nó precise de alguma especificação ou outros atributos severão ser adicionados dentro desse campo, caso não tenha nenhum, ainda precisa estar presente com um valor de '{}'.

'Edges' vai conter as informações das relações, ou seja, as ligações entre os nós. Também está em uma estrutura de lista e cada ítem precisa conter subcampos:

  * from = Será a indicação do <b>nó de origem</b> daquela relação, devendo se referir ao nó atravéz do respectivo campo 'id'.
  * to = Será a indicação do <b>nó destino</b> daquela relação, devendo se referir ao nó atravéz do respectivo campo 'id'.
  * label = Será o nome daquela relação que aparecerá como rótulo no momento da visualização.
  * title = Será o texto que vai aparecer ao descansar o mouse por cima da relação.

Dessa forma toda relação tem um nó de origem e um de destino, funcionando como um fluxo. Os nós podem conter qualquer quantidade de relações, tanto como origens quanto destino. Ressalta-se que é possível um nó não se relacionar com nenhum outro,e ainda assim será mostrado na representação gráfica, <b>entretanto o um nó não pode se relacionar consigo mesmo</b>.
- `Nó 1 ⮕ Nó 2`  ------>  Válido
- `Nó 1 ⮕ Nó 1`  ------>  Inválido

```js
var data = {
              //Bloco da lista de Nós                
    nodes: [
        { "id": '1', "label": "Nó A", "attributes": { "attr!": "Ex1", "attr2": "Ex2" }, "title": "Nó central" },
        { "id": '2', "label": "Nó B", "attributes": {}, "title": "Título nó B" },
        { "id": '3', "label": "Nó C", "attributes": {}, "title": "Título nó C" },
        { "id": '4', "label": "Nó D", "attributes": {}, "title": "Título nó D" },
        { "id": '5', "label": "Nó E", "attributes": {}, "title": "Título nó E" },
        { "id": '6', "label": "Nó F", "attributes": {}, "title": "Título nó F" },
        { "id": '7', "label": "Nó G", "attributes": {}, "title": "Título nó G" },
        { "id": '8', "label": "Nó H", "attributes": {}, "title": "Título nó H" },
    ],
              //Bloco da lista de Relações
    edges: [
        { "from": '1', "to": 2, "label": "Link 1", "title": "Título link A" },
        { "from": '1', "to": 3, "label": "Link 2", "title": "Título link A" },
        { "from": '1', "to": 4, "label": "Link 3", "title": "Título link A" },
        { "from": '1', "to": 5, "label": "Link 4", "title": "Título link A" },
        { "from": '1', "to": 6, "label": "Link 5", "title": "Título link A" },
        { "from": '2', "to": 7, "label": "Link 6", "title": "Título link A" },
        { "from": '2', "to": 8, "label": "Link 7", "title": "Título link A" },
    ]
}     
var container = document.getElementById('divGraphStands');
network = new vis.Network(container, data, options);
```
Ressaltando que no código fonte, as listas são criadas dinamicamente atravéz de uma pesquisa.

Depois da criação da variável com as listas de nós e relações, é a hora de indicar o 'id' da estrutura html que receberá o gráfico, isso é feito dentro da variável 'container'. Logo após é executada a biblioteca 'vis.Network()' e dentro dela são enviados alguns parâmetros que <b>obrigatóriamente</b> precisam estar nessa órdem:
  * Primeiro: Deve ser a identificação do elemento HTML onde o grafo será criado, nesse caso com o nome da variável 'container'.
  * Segundo: Deve ser a estrutura JSON que traz as listas de nós e relações, nesse caso com o nome da variável 'data'.
  * Terceiro: Deve ser a estrutura JSON com a aparência que formatará o gráfo, em caso de não ter uma aparência selecionada, ainda deve ser enviada como '{}'. Nesse caso enviaremos uma variável 'options' que será o resultado da busca das aparências explicada logo a frente.

## Pesquisa <a name = "search"></a>

Esse modelo tem o objetivo de trazer um exemplo de uma apresentação de grafo com dados dinâmicos, isto é, dados que são pesquisados no momento do carregamento do código.

O AvantScan é um módulo do AvantData que vaz varreduras procurando por vulnerabilidades em uma rede e indexa todos os resultados. Um desses dados é chamado de "CVE", que são códigos de vulnerabilidades conhecidas pela comunidade. A NIST (National Institute of Standards and Technology) documenta e espeficifica essas 'CVEs' que podem ser consultadas pela API deles.

> A ideia dessa pesquisa exemplo é cruzar os dados no NIST com as CVEs indexadas pelo AvantScan e apresentar uma ligação de quais dados são correlacionados.

No código fonte isso é feita em uma função JavaScript chamada 'searchScan()'. No início é criada uma mensagem 'toastr' que aparecerá para informar o usuário que a pesquisa está sendo feita e então declaradas as variáveis que serão usadas e preenchidas no decorrer do código.

```js
toastr.info('Aguarde enquanto os dados são carregados.', 'Aviso', { positionClass: "toast-bottom-right",closeButton: "true"});
  
let nodesApiExterna = []    //todos as cves da api externa
let nodesIndexados = []     //todas as cves indexadas        
let AllNodes = []           //onde serão inseridos todos os nós para criação do gráfico
let relation = []           //onde serão inseridos todos os links
let moderation = []         // variável de apoio 
```

Depois é feita uma consulta pela API da NIST buscando os dados das vulnerabilidades encontrados numa CPE (conjunto de vulnerabilidades de um contexto). A pesquisa é feita usando AJAX e vai armazenar todas as CVEs encontradas em uma das variáveis criandas anteriormente.

```js
// busca todas as CVEs da api externa do NIST (National Institute of Standards and Technology)
$.ajax({
    url: urlSearch,
    method: 'GET',
    async: false,
    success: (responseCPE) => {              
        
        let cpeResultList = responseCPE.result.cpes
        for (i in cpeResultList) {
            let cveList = cpeResultList[i].vulnerabilities
            for (j in cveList) {
                
                if(nodesApiExterna.includes(cveList[j]) == false) {
                    nodesApiExterna.push(cveList[j])
                }
            }
        }
    },
    error: (err) => {
        console.log(err)
    }
})  
```
Depois é feita uma consulta atravéz da [AvantAPI]((#built_using)) buscando os dados indexados do AvantScan, também feita com uma estrutura AJAX. As CVEs encontradas são armazenadas em outra variável.

```js
let queryDetailCVE = {
    index: "avantscan_results",
    size: 5000,
    body: {
        query: {
            query_string: {
                query: `nvt.refs.ref: *`
            }
        }
    }
};

// Busca as CVEs indexadas no AvantData nos índices avantscan_results
$.ajax({
    url: '/avantapi/avantData/search/customSearch',
    method: 'POST',
    async: false,
    headers: {
        'cluster': 'AvantData'
    },
    data: JSON.stringify(queryDetailCVE),
    success: (responseCVE) => {

        if (responseCVE.hits.hits) {
            let arrayHits = responseCVE.hits.hits
            arrayHits.forEach((result)=>{ 
                let arrayRef = result._source.nvt.refs.ref
                if(Array.isArray(arrayRef)) {
                    for(i in arrayRef) {
                        if(arrayRef[i].type == "cve") {
                            if (nodesIndexados.includes(arrayRef[i].id) == false) {
                                nodesIndexados.push(arrayRef[i].id) 
                            }
                        }
                    }
                    
                } else {
                    if(arrayRef.type == "cve") {
                        if (nodesIndexados.includes(arrayRef.id) == false) {
                            nodesIndexados.push(arrayRef.id) 
                        }
                    }
                }
            })
        }  
    },
    error: (err) => {
        console.log(err)
    }
})
```

A última parte da função é composta pera comparação entre as variáveis que contem os dois grupos de CVEs encontradas nas duas pesquisas, quando elas são equivalentes são criados itens de 'nó' e 'relações'. Uma das variáveis será usada para montar a lista dos 'nós' do grafo, outra será usada para formar a lista das 'relações' seguindo a [estrutura](#node_relation) ja mensionada anteriormente. 

Quando a comparção finaliza, as listas de nós e relações são enviadas para outra função que vai buscar as aparências para customizar o grafo e, enfim, montar o grafo.

```js
//Compara as CVEs das duas fontes e cria as litas de nós e relações
for (t in nodesIndexados) {
    if(nodesApiExterna.includes(nodesIndexados[t]) == true) {
        moderation.push(nodesIndexados[t])
        
        AllNodes.push({ 
            "id": `${nodesIndexados[t]}`,
            "label": `${nodesIndexados[t]}`,
            "title": `${nodesIndexados[t]}`, 
            "attributes": {}
        })
        
        relation.push({
            "from": `${nodesIndexados[t]}`,
            "to": 'Vulneráveis',
            "label": "Link",
            "title": "" 
        })
        relation.push({
            "from": `${nodesIndexados[t]}`,
            "to": 'Indexado',
            "label": "Link",
            "title": "" 
        })
        
        if(moderation.includes('Vulneráveis') == false) {
            moderation.push('Vulneráveis')
            AllNodes.push({
                "id": 'Vulneráveis',
                "label": 'Vulneráveis',
                "title": 'Vulneráveis', 
                "attributes": {}
            })
        }
        if(moderation.includes('Indexado') == false) {
            moderation.push('Indexado')
            AllNodes.push({ 
                "id": 'Indexado',
                "label": 'Indexado',
                "title": 'Indexado', 
                "attributes": {}
            })
        }
    }
}          
// Envia as listas de nós e relações para a função que vai buscar a aparência para montar o grapho
getAppearanceConfig(AllNodes, relation) 
```

## Aparência<a name = "style"></a>

A imagem a seguir representa diferentes visualizações do mesmo resultado das pesquisas feitas em um ambiente de testes com dados indexados do AvantScan e representam um pequeno exemplo da variedade de formas e cores que podem ser criadas.

![Grafo padrão](https://i.imgur.com/QpwxOWB.png)

A função ja inicia recebendo dois parâmetros, que são as listas de nós (nodes) e relações (relations). Logo a seguir busca as aparências com o AJAX. O campo 'url' pode ser preenchido com duas rotas diferentes da API, uma delas para buscar a aparência definida como padrão, ja a outra para trazer uma lista com todas as aparências já criadas, ao alterar a rota definida, deve-se também alterar a váriavel 'key' que buscará o valor correto do índice da resposta, alterando qual ítem da lista de aparências deseja buscar.

Após escolher a aparência a variável 'optionsGraph' vai montar e armazenar a estrutura JSON com as informações da aparência escolhida e logo após será executada a função 'createGraph()' enviando o id HTML, a lista de nós, a lista de relações e as opções de aparências escolhidas.


```js
function getAppearanceConfig(nodes, relations) {
      
    $.ajax({
        // url: `/avantapi/2.0/graph/appearance/${usuarioLocal}`,              // Buscar todas as aparências 
        url: `/avantapi/2.0/graph/appearance/default/${usuarioLocal}`,   // Buscar a aparência padrão
        type: 'GET',
        async: false,
        success: (resposta) => {            
            
            let key = resposta[0] // caso tenha buscado a aparência padrão 

            // let key = resposta[3] // Ao buscar todas as aparências deve-se escolher qual delas será usada, o número dela deve estar dentro dos colchetes. Ex: '[3]'            
            
            // Cria a lista de opções que foram buscadas 
            let optionsGraph = {
                interaction: JSON.parse(key['interaction']),
                nodes: JSON.parse(key['nodes']),
                edges: JSON.parse(key['edges']),
                manipulation: JSON.parse(key['manipulation']),
                layout: JSON.parse(key['layout']),
                physics: JSON.parse(key['physics'])
            }
            
            // Executa a função de criação de gráfico enviando o id HTML, a lista de nós, a lista de relações e as opções de aparências escolhidas.
            createGraph('divGraphStands', nodes, relations, optionsGraph)            
        },
        error: (error) => {
            console.log(error)
        }
    })    
}
```

```
Obs: Observe que as rotas utilizam uma variável 'usuarioLocal' que foi configurada no topo da linguagem JavaScrip:

$(document).ready(function () {
    Rotas.getUserName((usuario) => {
        usuarioLocal = JSON.parse(usuario)
    })
    
    searchScan()
}); 
```
## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar em outros paineis, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

O mesmo acontece com os nomes de cada 'function' JavaScript, cada nome deve ser único para cada cópia desse modelo em uma visualização, tanto na criação, quando na hora de executar.

## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [Vis Network](https://visjs.org/) - Biblioteca para criação de grafos de vínculos
- [NIST](https://nvd.nist.gov/) - <i>National Institute of Standards and Technology</i> que documenta e criteriza vulnerabilidades.