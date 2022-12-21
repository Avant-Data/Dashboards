<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>

<h3 align="center">Formulários</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> Como aplicar e utilizar um formulário no dashboard.
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Começando](#starting)
- [Estrutura](#structure)
  - [Título](#title)
  - [Texto e Número](#text_number)
  - [Select e Datalist](#select_datalist)
  - [Data e Comentário](#date_comment)
  - [Botões](#buttons)
- [Funções](#functions)
    - [Pesquisa](#search)
    - [Token](#token)
    - [Limpar](#clean)
- [Precauções](#precaution)
- [Construído Utilizando](#built_using)
## Sobre <a name = "about"></a>

![Exemplos de Fomulário](https://i.imgur.com/3ibGybJ.png)

Formulário é um quadro com campos para serem preenchidos com informações situacionais, sempre com algum botão de 'submeter' as informações que foram inseridas para serem usadas em determinado contexto. Esse modelo é composto por seis campos (chamados inputs) cada qual com suas especificações, sendo elas texto, número, select, datalist, data e comentário. Essas opções de inputs são variadas justamente para o usuário conhecer essas diferênças e usar em seu formulário final aquelas que lhe convém, alterando, substituindo ou removendo as que não atendem a sua necessidade. Há três variedades de botão, com funções que são muito comuns no uso geral do AvantData.

Nesse modelo, a estrutura será montada em HTML com [Bootstrap](https://getbootstrap.com.br/docs/4.1/components/carousel/#:~:text=fosse%20um%20carrosel.-,Como%20funciona,controles%20anterior%2C%20pr%C3%B3ximo%20e%20indicadores.), que é uma biblioteca de estilos e visualizações. A execução dos botões em geral são feitas na linguagem JavaScript usando a biblioteca de [JQuery](https://jquery.com/).

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```
## Começando <a name = "starting"></a>

Inicialmente, para montar uma tabela, é necessário criar um novo cartão do tipo “formulário” através do menu de contexto.

![Criando Cartão](https://i.imgur.com/Sx9hPLC.png)

Ao abrir a modal de edição, cole o código fonte no espaço de texto. Atente-se às dimensões desejadas. Esse modelo está com o padrão de altura em 500px e largura de “grande”, mas fica a critério do usuário ajustar esses valores.

## Estrutura <a name = "structure"></a>

O código fonte sugerido traz um modelo genérico, com uma variedade de tipos de inputs e botões, justamente para trazer opções ao usuário final que poderá adaptar toda essa variedade para um contexto de uso individual. Uma das utilizações mais comuns é a criação de TOKENS e pivoteamento para um outro painel, exemplos que estão presentes nesse modelo.

A estrutura do código é dividida em blocos para facilitar o entendimento do que é feito em cada parte. Antes de começar a montagem do esqueleto do formulário, é criado um elemento de 'style' (estilo) que traz uma característica de 'hover' aos botões. 'Hover' é a mudança de estilo ao passar o mouse por cima do elemento. Nesse caso, mudamos a cor de fundo de cada botão para um tom levemente mais claro que a cor padrão.

```html
<head>
    <!-- estilização dos botões -->
    <style>
        .hover-g:hover {
            background-color: #dcd516 !important;
        }
        .hover-b:hover {
            background-color: #52c1c5 !important;
        }
        .hover-o:hover {
            background-color: #ff8c53 !important;
        }
    </style>
</head>
```
### Título <a name = "title"></a>

Consiste na parte mais simples e intuitiva do código fonte. É possível alterar os valores de título e subtítulo substituindo respectivamente os textos dentro dos elementos 'h3' e 'h5'. O usuário pode acrescentar outra linha de texto para colocar outro elemento a ser mostrado desse bloco, utilizando as tags 'h6', 'h5', 'h4', 'h3', 'h2', ou 'h1', sendo a 'h1' a maior e a 'h6' a menor.
```html
<!--Bloco do Título-->
<div class="p-2" style="background-color:#38a0a4; color: white;">
    <h3>Título</h3>
    <h5>Subtítulo</h5>
</div>
```

### Texto e Número <a name = "text_number"></a>

Nesse bloco são criados os dois primeiros campos de input. Para definir o tipo do campo, deve-se observar o atributo 'type' dentro do elemento 'input'. Para alterar o nome de cada campo, basta substituir o texto dentro do elemento 'label' de cada umd deles.

```html
<!-- Bloco de Texto e Número -->
<div class="row">
    
    <div class="col-6">
        <label >Texto</label>
        <input type="text" id="textInput"  class="form-control form-control-sm mb-3">
    </div>
    
    <div class="col-6">
        <label >Número</label>
        <input type="number" id="numberInput"  class="form-control form-control-sm mb-3">
    </div>
    
</div>
```

Quando for do tipo 'text', o usuário poderá digitar nesse campo qualquer coisa. Geralmente é usado para nomes, cidades, textos pequenos ou similares.

Quando for do tipo 'number', só será possivel digitar números. O campo vem com setas no canto para o usuário aumentar ou diminuir o valor. Geralmente é usado para idade, quantidade de algum produto ou similares.

![texto e numero](https://i.imgur.com/OX0PO1E.png)

### Select e Datalist <a name = "select_datalist"></a>

Nesse bloco são criados os dois próximos campos de input. Para alterar o nome de cada campo, basta substituir o texto dentro do elemento 'label' de cada umd deles. A grande diferença entre esses dois campos é que o campo select pode ser preenchido somente pelas opções, e o campo datalist tem um espaço de digitação, onde o usuário pode digitar o que quiser e conforme vai digitando, vai também filtrando as opções, além de poder escolher uma opção desde o início. Resumindo, o campo do tipo datalist funciona como um cruzamento do input tipo texto e um select.

```html   
   <div class="row"> 
                
    <div class="col-6">
        <label>Select</label>
        <select id="selectInput" class="browser-default custom-select custom-select-sm">
            <option disabled selected>Selecione</option>
            <option>Opção 1</option>
            <option>Opção 2</option>
            <option>Opção 3</option>
            <option>Opção 4</option>
        </select>                       
    </div>
        
    <div class="col-6">
        <label >Datalist</label>
        <input list="list" id="datalistInput" class="form-control form-control-sm mb-3">                       
        <datalist id="list">
            <option>Opção A</option>
            <option>Opção B</option>
            <option>Opção C</option>
            <option>Opção D</option>
        </datalist>
    </div>
    
</div>
```

O campo do tipo Select pode ser preenchido apenas escolhendo alguma das opções. Vale observar que ele não é um elemento do tipo 'input' e sim tem seu proprio elemento 'select', dentro dele vários elementos de opção (options). É preferível adicionar sempre uma primeira opção com texto de "Selecione" e atributos 'disabled selected' isso vai criar uma opção que não pode ser ecolhida, mas o texto dela fica visível ao usuário antes de selecionar algum ítem.
Para adicionar ou removar opções, basta acrecentar ou apagar elementos de 'option' dentro do padrão, customizando os nomes de cada uma.

O campo do tipo Datalist pode ser preenchido com texto, e conforme vai digitando, vai também filtrando as opções que tem. É formado por um 'input' que não tem um atributo 'type' e sim um 'list' que será preenchido com o 'id' do elemento 'datalist' logo abaixo. Dentro do elemento 'datalist' vão ser adicionadas as 'options'. 

![select datalist](https://i.imgur.com/UKIwLuy.png)

### Data e Comentário <a name = "date_comment"></a>

Nesse bloco são criados os dois últimos campos de input desse modelo. Para definir o tipo do campo, deve-se observar o atributo 'type' dentro do elemento 'input'. Para alterar o nome de cada campo, basta substituir o texto dentro do elemento 'label' de cada um deles.

```html
<!-- Bloco de Data e Comentário -->
<div class="row">

    <div class="col-6">
        <label >Data e hora</label>
        <input type="datetime-local" id="dateTimeInput" class="form-control form-control-sm mb-3">
    </div>
    
    <div class="col-6">
        <label >Comentário</label>
        <textarea id="commentInput" class="md-textarea form-control" rows="3" autocomplete="off"></textarea>
    </div>

</div>
```
O campo Data e Hora é um input com atributo 'type' com valor 'datetime-local'. Ele deve ser preenchido por valores válidos de data e hora. O navegador vai interpretar esse input e adicionar um botão de calendário na lateral do campo, onde o usuário pode escolher a data e hora por meio de cliques. Geralmente é usado para marcação de compromissos, datas de aniversário ou similares.

O campo Comentário não é feito atravez de um elemento 'input' e sim 'textarea'. Nele é possivel escrever qualquer tipo de texto, muito semelhante ao input tipo texto, a diferênça é que esse é utilizado para textos longos, como comentários com diversas linhas, relatórios, letras de músicas entre outros. A margem desse campo é alterável, sendo possível arrastar para baixo e aumentar o tamanho desse elemento com o mouse.

![data e comentário](https://i.imgur.com/bm33dir.png)

### Botões <a name = "buttons"></a>

O último bloco é composto pela montagem dos botões, cada um criado a partir de de um elemento HTML 'button'. Eles contém um atributo 'onclick' com o nome de uma função que está montada em JavaScript, isso significa que quando o usuário clicar em cada botão vai executar essa função e ativar o efeito dela. É possível alterar o nome dos botões substituindo o texto.

O usuário pode alterar a função do botão, mudando o valor do atributo 'onclick' para o nome da função desejada; pode acrescentar outro botão criando outro elemento 'button' seguindo o padrão dos já existentes ou excluir algum deles apenas apagando o elemento no código fonte.

```html
<!-- Bloco dos Botões  -->
<div class="row justify-content-md-center">
    
    <button class="col-2 hover-o mr-1 btn p-2" 
    style="background-color: #e96817; border-color: white; color:white;;border-style: solid; border-width: thin; border-radius: 5px;"
    onclick="clearForm()">Limpar</button>
    
    <button class="col-2 hover-b ml-1 mr-1 btn p-2" 
    style="background-color: #38a0a4; border-color: white; color:white;border-style: solid; border-width: thin; border-radius: 5px;" 
    onclick="applyGeral()">Token</button>
    
    <button class="col-2 hover-g ml-1 btn p-2" 
    style="background-color: #bab513; border-color: white; color:white;border-style: solid; border-width: thin; border-radius: 5px;" 
    onclick="applyGeral(true)">Pivotear</button>
    
</div>
```

No modelo de exemplo foram criados 3 botões. O primeiro (Limpar) ao ser clicado vai apagar todas as informações preenchidas nos inputs, vai apagar todos os tokens que foram criados e recarregar os gráficos daquele painel.

O segundo botão (Token) pega todas as informações que foram preenchidas e cria um token para cada uma delas. Token é uma informação armazenada no navegador. Para ver essa informações, é necessário inspecionar a página (F12) e vai aparecer uma tela de configurações. Na aba de 'Aplicação' (o nome das abas pode variar de acordo com o idioma ou com o navegador usado) terá uma opção de 'session storage' com o endereço do AvantData, ao clicar nesse endereço vai abrir uma área com chave (key) e valor (value), essas são as informações de token.<p name = "session_storage"></p>

O campo 'key' é o nome do token e o campo ' value' é a informação que ele armazena. Ao clicar no segundo botão do formulário, todas as informações que foram preenchidas nos inputs serão enviadas como 'value' dos tokens e as 'keys' ja foram previamente definidas na função JavaScript.

![tokens sinalizados](https://i.imgur.com/tRGoVgN.png)

 Nesse modelo, existe uma função '[getPanels()]()' (JavaScript) que é executada assim que o dashboard é carregado e vai pesquisar quais os paineis existem nessa visualização e criar uma opção para cada uma delas substituindo as opções do campo select com o nome de cada painel. Dessa forma, se existirem 3 paineis, serão criadas 3 opções no campo select com seus respectivos nomes. O terceiro botão (Pivotear) também vai criar os tokens exatamente como no botão mensionado anteriormente, porém também vai encaminhar o ususário para o painel escolhido pelo campo Select.

## Funções <a name = "functions"></a>

Esse modelo é traz três funções para o funcionamento geral e que podem ser customizadas de acordo com as necessidades do usuário. É válido ressaltar que esse exemplo não exclui a possibilidade de serem adiconadas outras funções, visto que o código está dentro da estrutura geral do AvantData, o que permite herdar diversas bibliotecas já usadas no sistema.

### Pesquisa <a name = "search"></a>

A primeira função utilizada é nominada 'getPanels', criada em linguagem JavaScript. A utilidade dela é buscar (atravez de uma pesquisa) todos os paineis da visualização atual e criar uma opção para cada um deles dentro do campo "select'

Para fazer a pesquisa, é utilizado uma função JavaScript, dentro dela é criado uma requisição Ajax que vai fazer uma busca em algum banco de dados e trazer uma respota. Dentro do Ajax, tem uma cláusula de sucesso, onde serão montadas as opções com os dados do resultado da pesquisa.

Nesse modelo, utilizamos uma busca atravez de uma rota [AvantAPI](https://avantapi.avantsec.com.br/) interna que serve justamente para se conectar a um banco de dados e enviar um texto de pesquisa sql.

```js
$(document).ready(function () {        
    getPanels()    
});

function getPanels() {
    var idVisualizacaoAtual = localStorage.getItem("visualizacao_atual")          
    
    var query = {
        "conector": "AvantData",
        "query": "SELECT nome FROM painel_dashboard WHERE visualizacao_pai = "+idVisualizacaoAtual+" AND autor = 'master' ORDER BY posicao;"
    }
    
    $.ajax({
        url: `/avantapi/sql/selectQuery`,
        method: 'POST',
        data: JSON.stringify(query),
        success: (resposta) => {
            console.log(resposta)
            $('#selectInput').html('')
            $('#selectInput').append(`
                    <option disabled selected>Select</option>
                `);
            resposta.forEach((painel) => {
                $('#selectInput').append(`
                    <option value="${painel.nome}">${painel.nome}</option>
                `);
            });
        }
    });
}
```

O usuário pode alterar essa pesquisa utilizando a busca que desejar, ficando atento ao formato em que o resultado vai chegar para poder navegar poe ele e usar os valores corretamente. 'Ajax' é um tipo de codificação para fazer uma requisição. Nele são passados dados de configuração para se conectar ao destino e fazer uma busca. Nesse caso, o resultado dessa busca está sendo transformado em 'opções' do campo 'Select' mas o usuário pode usar essa mesma estrutura para qualquer outra utilidade, desde inserir dados em algum banco, [montar tabelas](https://github.com/Avant-Data/Dashboards/tree/master/Datatable), adicionar [menus de contexto](https://github.com/Avant-Data/Dashboards/tree/master/ContextMenu) entre outros.

Importante notar que essa função aparece dentro de uma extrutura "$(document).ready()" que significa que assim que o navegar terminar de interpretar o código fonte, vai executar a função e ativar seu efeito.

![Opções select](https://i.imgur.com/c3E2WX5.png)

### Token <a name = "token"></a>

A segunda função utilizada é nominada 'applyGeral', criada em linguagem JavaScript. A utilidade dela é resgatar os dados que foram preenchidos pelo usuário em cada campo do formulário e criar um token para cada um. É iniciada com o clique nos botões 'Token' (onde vai apenas criar os tokens) e 'Pivotear' (onde vai reencaminhar o usúario para o paniel escolhido pela opção 'Select')

```js
function applyGeral(go = false) {
    //Faz verificações de campos vazios
    console.log($('#selectInput').val())
    if(go == true) {
        if( $('#selectInput').val() == '' || $('#selectInput').val() == undefined || $('#selectInput').val() == 'Select' || $('#selectInput').val() == null ) {
            toastr.warning('Campo Select é obrigatório.', 'Atenção', { positionClass: "toast-bottom-right", closeButton: "true" });
            return
        }
    }
    if( $('#textInput').val() == '' || $('#textInput').val() == undefined || $('#textInput').val() == null ) {
        toastr.warning('Campo Texto é obrigatório.', 'Atenção', { positionClass: "toast-bottom-right", closeButton: "true" });
        return
    }
    
    //armazena valores dos inputs em variáveis dentro de um JSON (dados)
    let dados = {}
    dados.tokenTEXT = $('#textInput').val()            // corresponde ao id do input de texto
    dados.tokenNUMBER = $('#numberInput').val()        // corresponde ao id do input de número
    dados.tokenSELECT = $('#selectInput').val()        // corresponde ao id do input select
    dados.tokenDATALIST = $('#datalistInput').val()    // corresponde ao id do input datalist
    dados.tokenDATE = $('#dateTimeInput').val()        // corresponde ao id do input de data e hora
    dados.tokenCOMMENT = $('#commentInput').val()      // corresponde ao id do input de comentário/textArea
    
    //manda criar tokens baseado no JSON enviado
    applyDashboard(dados);
    
    //se o usuário clicou no botão 'pivotear', ele vai ser encaminhado ao painel escolhido
    if(go == true) {
        goToPanel($('#selectInput').val());	
    }
}
```

Observa-se que existem algumas cláusulas "toastr" dentro do código. Essa é a forma de códificar uma caixa de mensagem que será exibida em determinadas condições. A caixa da mensagem pode ser de aviso (warning) que terá uma cor laranja, erro (error) que será vermelha, informacional (info) que será azul ou sucesso (success) que será verde.

Os tokens ficam armazenados na aba atual do navegador e podem ser resgatados mesmo que o usuário mude o painel ou abra outra visualização do dashboard. É uma forma eficiente de passar dados entre os paineis sem precisar refazer pesquisas e também aplicar dados de um formulário a cartões tipo gráfico (os gráficos possuem em sua criação a opção de resgatar valores de token). Ao pivotear (reencaminhar o usuário para outro painel), os gráficos daquele painel vão se atualizar e caso algum deles faça alguma busca por token, os dados serão atualizados.

Para resgatar os valores de um token utiliza-se o padrão conforme o exemplo abaixo, onde 'token_key' é o nome da chave do íten do [session storage](#session_storage).

```js
sessionStorage.getItem('token_key');
```

### Limpar <a name = "clean"></a>

 segunda função utilizada é nominada 'clearForm', criada em linguagem JavaScript. A utilidade dela é apagar os dados dos campos que foram preenchidos, apagar todos os tokens e recarregar os gráficos que possam estar presentes nesse painel. É iniciada com o clique no botão 'Limpar'.

## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar em mais de um painel, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

O mesmo acontece com os nomes de cada 'function' JavaScript, cada nome deve ser único para cada cópia desse modelo em uma visualização, tanto na criação, quando na hora de executar.

## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [Bootstrap](https://getbootstrap.com.br/) - Biblioteca de aparências e estilos
- [JQuery](https://jquery.com/) - Biblioteca para JavaScript que facilita a integração entre HTML e JavaScript.