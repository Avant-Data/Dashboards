<h3 align="center">Tabelas de Dados</h3><

---

<p align="center"> Como aplicar e utilizar uma tabela de dados dinâmicos usando formulários no dashboard.
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Começando](#starting)
- [Título](#title)
- [Estrutura inicial da tabela](#initial-structure)
- [Botões de exportação](#export_buttons)
- [Pesquisa](#search)
- [Aplicando DataTable](#DataTable)
- [Precauções](#precaution)
- [Código fonte](#font_code)
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>
![Exemplos de Cabeçalho](https://i.imgur.com/sra90Oh.png)

DataTable é uma biblioteca de criação e formatação de tabelas cuja biblioteca ja está inserida dentro do AvantData. As linhas da tabela são criadas dinamicamente com resultados gerados a partir de uma pesquisa.

Nesse modelo, a estrutura será montada em html com a composição da pesquisa e a montagem de dados em linguagem JavaScript e Jquery. Como exemplo, o modelo ja vem com uma criação dinâmica simples de uma tabela tendo como parâmetro incial dados do AvantAgent.

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```

## Começando <a name = "starting"></a>

Inicialmente, para montar uma tabela, é necessário criar um novo cartão do tipo “formulário” através do menu de contexto.

![Criando Cartão](https://i.imgur.com/Sx9hPLC.png)

Ao abrir a modal de edição, cole o código fonte no espaço de texto. Atente-se às dimensões desejadas. Esse modelo está com o padrão de altura em 800px e largura de “muito grande”.

## Título <a name = "title"></a>

A primeira parte do modelo é constituída pelo bloco onde está o Título da tabela. Trata-se somente de uma estrutura HTML, sendo possível alterar o texto, cores e etc. 

```html
<div class="p-3" style="background-color: #38a0a4">        
    <div class="mt-2">
        <h5 class="mt-2">
            <span class=" text-center p-1 font-weight-bold" 
            style="border-radius:10px;padding:3px; color:#38a0a4; background-color: white;">Título Tabela</span>
        </h5>            
    </div>        
</div>
```
Para alterar o texto, basta subtituir o fragmento onde está escrito "Título Tabela" dentro do elemento de 'span'.


Caso queira alterar as cores, é necessário mudar alguns atributos básicos de cor, entre eles o “background-color” ou “color”. Nessa linguagem as faixas de cores podem ser descritas de três formas: usando padrão RGB, padrão Hexadecimal ou nomeando cores básicas em inglês.

```
color=" blue ;"         --> Cores básicas
color=" #38a0a3 ;"      --> Formato Hexadecimal
color=" 255 250 250 ;"  --> Formato RGB
```
## Estrutura inicial da tabela <a name = "initial-structure"></a>

Logo após a montagem do título, é criada uma estrutura inicial para a montagem da tabela onde é contruído o esqueleto com os títulos de cada coluna. 

```html
<div id="divTable" class="mt-2 display">
    <table id="table" class="table table-striped table-bordered" style="width:100%">
        <thead id="tableHead" style="background-color: #38a0a4; color: white;">
            <tr class="text-center">
                                      
                <th>ID Agente</th>       <!-- Coluna 1 -->  
                <th>Agente HostName</th> <!-- Coluna 2 -->
                <th>ID Monitor</th>      <!-- Coluna 3 -->
                <th>Monitor Name</th>    <!-- Coluna 4 -->
                
            </tr>
        </thead>
        <tbody id="tableBody">
        </tbody>
        <tfoot id="tableFooter">                
        </tfoot>
    </table>        
</div>
```
Nesse modelo utilizamos uma tabela com quatro colunas, mas caso seja necessário adicionar ou remover alguma coluna, basta inserir ou remover um elemento 'th' dentro da tabela, com seu respectivo texto.

Vale observar que o elemento 'tbody' está vazio, visto que esse é o lugar onde serão adicionadas as linhas.
```
Obs: Importante notar que a tabela (elemento 'table') tem um 'id', essa informação será usada para se referir a essa tabela em vários momentos do restante do código.
```
## Botões de exportação <a name = "export_buttons"></a>

Botões de exportação ficam no final da tabela depois de já estar montada. Eles trazem as opções de de exportar a tabela em um arquivo CSV, exportar a tabela em um arquivo de Exel ou copiar todos os valores da tabela para a área de transferência do usuário.
Na estrutura do código fonte são necessárias 3 etapas para o funcionamento correto.

A primeira etapa fica na cabeça do código fonte, onde são feitas pré configurações:

``` html
<head>
    <!-- importações necessárias para utilização dos botões de exportar -->
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.36/pdfmake.min.js"></script>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.1.36/vfs_fonts.js"></script>
    <script type="text/javascript" src="https://cdn.datatables.net/v/bs5/jszip-2.5.0/dt-1.12.1/af-2.4.0/b-2.2.3/b-colvis-2.2.3/b-html5-2.2.3/b-print-2.2.3/cr-1.5.6/date-1.1.2/fc-4.1.0/fh-3.2.4/kt-2.7.0/r-2.3.0/rg-1.2.0/rr-1.2.8/sc-2.0.7/sb-1.3.4/sp-2.0.2/sl-1.4.0/sr-1.1.1/datatables.min.js"></script>
    <script type="text/javascript" src="https://cdn.datatables.net/buttons/2.2.3/js/buttons.print.min.js"></script>
    
    <!-- Estilização dos botões para ficarem no fim da tabela -->
    <style>
        .dt-buttons {
            display:none;
        }
        .btnUnder3:hover {
            box-shadow: 2px 2px 10px grey;
            background-color: #e96817;
            color:white;
        }
    </style>
</head>
```
A segunda parte é a criação da estrutua dos botões, logo após a criação do esqueleto da tabela:
```html
<div id="divBtnsExport" class="row pl-4" style="clear:both;" hidden="true">
    <button id="btnCopyExport3" class="col-1 btnUnder3" style="border:thin ; border-radius: 8px 0px 0px 8px;" onclick="takeExport('copy')">copiar</button>
    <button id="btnExelExport3" class="col-1 btnUnder3" style="border:thin ; border-radius: 0px 0px 0px 0px;" onclick="takeExport('excel')">excel</button>
    <button id="btnCsvExport3" class="col-1 btnUnder3" style="border:thin ; border-radius: 0px 8px 8px 0px;" onclick="takeExport('csv')">csv</button>        
</div>
```
A terceira etapa fica dentro da parte de JavaScript, dentro de uma função, que será executada ao clicar do usuário. Note que dentro de cada estrutura de click tem uma parte "...controls=table" esse 'table' <b>precisa</b> ser o 'id' da tabela.
```js
function takeExport(type) {
    if(type == 'copy') {
    $('.buttons-copy[aria-controls=table]').click()
    }
    if(type == 'csv') {
    $('.buttons-csv[aria-controls=table]').click()
    }
    if(type == 'excel') {
    $('.buttons-excel[aria-controls=table]').click()
    }
}
```
## Pesquisa <a name = "search"></a>

Para fazer a pesquisa, é utilizado uma função JavaScript, dentro dela é criado uma requisição Ajax que vai fazer uma busca em algum banco de dados e trazer uma respota. Dentro do Ajax, tem uma cláusula de sucesso, onde serão montadas as linhas da tabela com os dados do resultado da pesquisa.

Nesse modelo, utilizamos uma busca dentro de um dos índices mais usados do AvantData, o AvantAgent. Como os dados dos indices no nosso sistema é, por padrão, indexado dentro de um banco de dados não relacional, utilizamos a nossa [API](https://avantapi.avantsec.com.br/) para fazer uma busca atravez do Custom Search (rota da nosa api em que mandamos uma query de pesquisa para o ElasticSearch e ela retorna o resultado).

```js
$(document).ready(function () {
    getInitialTable()         
});          

function getInitialTable() {     
    // monta a query de pesquisa para o ElasticSearch utilizando o exemplo do AvantAgent
    let query = {
        index: "AvantAgent",
        size:50,
        body: {
            query: {
                query_string: {
                    query: `idAgent: *`
                }
            }
        }
    };
    
    $.ajax({
        url: '/avantapi/avantData/search/customSearch', // rota da api - Explicada na documentação da API
        method: 'POST', //método de busca - Explicada na documentação da API
        headers: {'cluster': 'AvantData'}, // configuração- Explicada na documentação da API
        data: JSON.stringify(query), // aqui é inviada a query da pesquisa 
        success: (response)=> {               
        
          if(response.hits != undefined && response.hits != null && response.hits != false && response.hits != '') {
              
            let resultadosTarefa = response.hits.hits;
            console.log(resultadosTarefa)
              
            for (idx in resultadosTarefa) {                   
                
                var linha = `<tr id="tableLine-${resultadosTarefa[idx]._id}">`
                                        
                    linha += `<td>${resultadosTarefa[idx]._source.idAgent}</td>`;       // Coluna 1
                    linha += `<td>${resultadosTarefa[idx]._source.agentHostName}</td>`; // Coluna 2
                    linha += `<td>${resultadosTarefa[idx]._source.idMonitor}</td>`;     // Coluna 3
                    linha += `<td>${resultadosTarefa[idx]._source.monitorName}</td>`;   // Coluna 4
                    
                linha += '</tr>';
                $('#tableBody').append(linha);
            }
          }           
        tableFormat() 
        },
        error: (error) => {               
            tableFormat()
        }
    });
}
```
Caso seja necessário, é possivel modificar o método de busca, para trazer dados de outros tipos de banco ou de outras rotas da api, sempre sequindo a documentação. Nesse caso, dentro da cláusula de sucesso, os dados são mapeados e distribuídos em uma variável 'linha' e assim criando cada ítem correspondente a coluna anteriormente estipulada na criação do esqueleto da tabela. Vale observar que logo apos a criação da 'linha' ela é acoplada no corpo da tabela, utilizando o 'id' com a estrutura '$('#tableBody').append(linha);'.

## Aplicando DataTable <a name = "DataTAble"></a>
## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar esse cabeçalho em outros paineis, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

O mesmo acontece com os nomes de cada 'function' JavaScript, cada nome deve ser único para cada cópia desse modelo em uma visualização, tanto na criação, quando na hora de executar.

## Código fonte <a name = "font_code"></a>
## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [MDBootstrap](https://mdbootstrap.com/) - Biblioteca de aparências e estilos 
- [DataTable](https://datatables.net/) - Biblioteca de montagem e formatação de tabelas. 