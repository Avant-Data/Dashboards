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
- [Començando](#starting)
- [Estrutura](#structure)
  - [Título](#title)
  - [Texto e Número](#text_number)
  - [Select e Datalist](#select_datalist)
- [Precauções](#precaution)
- [Construído Utilizando](#built_using)
## Sobre <a name = "about"></a>

![Exemplos de Fomulário](https://i.imgur.com/3ibGybJ.png)

Formulário é um quadro com campos para serem preenchidos com informações situacionais, sempre com algum botão de 'submeter' as informações que foram inseridas para serem usadas em determinado contexto. Esse modelo é composto por seis campos (chamados inputs) cada qual com suas especificações, sendo elas texto, número, select, datalist, data e comentário. Essas opções de inputs são variadas justamente para o usuário conhecer essas diferênças e usar em seu formulário final aquelas que lhe convém, alterando, substituindo ou removendo as que não atendem a sua necessidade. Há três variedades de botão, com funções que são muito comuns no uso geral do AvantData.

Nesse modelo, a estrutura será montada em HTML com [Bootstrap](https://getbootstrap.com.br/docs/4.1/components/carousel/#:~:text=fosse%20um%20carrosel.-,Como%20funciona,controles%20anterior%2C%20pr%C3%B3ximo%20e%20indicadores.), que é uma biblioteca de estilos e visualizações. A execução dos botões em geral são feitas na linguagem JavaScript usando a biblioteca de [JQuery](https://jquery.com/).

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```
## Començando <a name = "starting"></a>

Inicialmente, para montar uma tabela, é necessário criar um novo cartão do tipo “formulário” através do menu de contexto.

![Criando Cartão](https://i.imgur.com/Sx9hPLC.png)

Ao abrir a modal de edição, cole o código fonte no espaço de texto. Atente-se às dimensões desejadas. Esse modelo está com o padrão de altura em 500px e largura de “grande”, mas fica a critério do usuário fazer ajustes nesses valores.

## Estrutura <a name = "structure"></a>

O código fonte sugerido traz um modelo genérico, com uma variedade de tipos de inputs e botões, justamente para trazer opções ao usuário final que poderá adaptar toda essa variedade para um contexto de uso individual. Uma das utilizações mais comuns é a criação de TOKENS e pivoteamento para um outro painel, exemplos que estão presentes nesse modelo.

A estrutura do código é dividida em blocos para facilitar o entendimento do que é feito em cada parte. Antes de começar a montagem do esqueleto do formulário, é criado um elemento de 'style' (estilo) que traz uma característica de 'hover' aos botões. Hover é a mudança de estilo ao passar o mouse por cima do elemento. Nesse caso, mudamos a cor de fundo de cada botão para um tom levemente mais claro que a cor padrão.

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

Consiste na parte mais simples e intuitiva do código fonte. É possivel alterar os valores de título e subtítulo substituindo respectivamente os textos dentro dos elementos 'h3' e 'h5'. O usuário pode acrescentar outra linha de texto para colocar outro elemento a ser mostrado desse bloco, utilizando as tags 'h6', 'h5', 'h4', 'h3', 'h2', ou 'h1', sendo a 'h1' a maior e a 'h6' a menor.
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

Nesse bloco são criados os dois próximos campos de input. Para alterar o nome de cada campo, basta substituir o texto dentro do elemento 'label' de cada umd deles. A grande diferença entre esses dois campos é que o campo select pode ser preenchido somente pelas opções, e o campo datalist tem um espaço de digitação, onde o usuário pode digitar o que quiser e conforme vai digitando, vai também filtrando as opções, além de poder escolher uma opçãod esde o início. Resumnindo, o campo do tipo datalist funciona como um cruzamento do input tipo texto e um select.

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

O campo do tipo Select pode ser preenchido apenas escolhendo alguma das opções. Vale observar que o ele não é um elemento do tipo 'input' e sim tem seu proprio elemento 'select', dentro dele varios elementos de opção (options) e cada uma com o texto que dará nome a opção. É preferível colocar sempre uma primeira opção com texto de "Selecione" e atributos 'disabled selected' isso vai criar uma opção que não pode ser ecolhida, mas o texto dela fica visível ao usuário antes de selecionar algum ítem.
Para adicionar ou removar opções, basta acrecentar ou apagar elementos de 'option' dentro do padrão, custozimando os nomes de cada uma.

O campo do tipo Datalist pode ser preenchido com texto, e conforme vai digitando, vai também filtrando as opções que tem. É formado por um 'input' que não tem um atributo 'type' e sim um 'list' que será preenchido com o 'id' do elemento 'datalist' logo abaixo. Dentro do elemento datalist vão ser adicionadas as 'options'. 

![select datalist](https://i.imgur.com/UKIwLuy.png)

### Data e Comentário <a name = "date_comment"></a>

Nesse bloco são criados os dois últimos campos de input desse modelo. Para definir o tipo do campo, deve-se observar o atributo 'type' dentro do elemento 'input'. Para alterar o nome de cada campo, basta substituir o texto dentro do elemento 'label' de cada umd deles.

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
O campo Data e Hora é um input com atributo 'type' com valor 'datetime-local'. Ele deve ser preenchido por valores válidos de data e hora. O navegador vai interpretar esse input e adicionar um botão de calendário na lateral do campo, onde o usuário pode escolher a data e hora atravez de cliques. Geralmente é usado para marcação de compromissos, datas de aniversário ou similares.

O campo Comentário não é feito atravez de um elemento 'input' e sim 'textarea'. Nele é possivel escrever qualquer tipo de texto, muito semelhante ao input tipo texto, a diferênça é que esse é utilizado para textos longos, como comentários com diversas linhas, relatórios, letras de músicas entre outros. A margem desse campo é alterável, sendo possivel arrastar para baixo e aumentar o tamanho desse elemento com o mouse.

![data e comentário](https://i.imgur.com/bm33dir.png)

## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar em mais de um painel, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

O mesmo acontece com os nomes de cada 'function' JavaScript, cada nome deve ser único para cada cópia desse modelo em uma visualização, tanto na criação, quando na hora de executar.
## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [Bootstrap](https://getbootstrap.com.br/) - Biblioteca de aparências e estilos
- [JQuery](https://jquery.com/) - Biblioteca para JavaScript que facilita a integração entre HTML e JavaScript.