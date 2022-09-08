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
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>



Grafo é uma representação gráfica de valores ligados uns aos outros através de ralações, criando pontos e linhas para moldar uma visualização. Os pontos são chamados de <i>nós</i>, as linhas de <i>relações</i>. O AvantData disponibiliza toda a configuração e ultilização dessa ferramenta dentro do módulo AvantGraph, mas podem também ser criados dentro do dashboard.

Nesse modelo,a  estrutura e a visualização são criadas através de uma biblioteca JavaScript para criação dinâmica de  grafos chamada Vis Network.No código fonte, trazemos a opção de preencher o gráfico dinamicamente, atravez de uma pesquisa.

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```

## Peculiaridades <a name = "peculiar"></a>

Esse tipo de gráfico traz interações especiais que os diferenciam dos demais. Em sua configuração pode ser habilitada a interação com mouse que imita as regras da física no mundo real, dessa forma o usuário pode arrastar nós e linhas criando animações elásticas e vibrantes. Ao clicar em um nó ou relação, esse elemento é ressaltado. Ao descansar o mouse sobre algum elemente, uma janela aparece trazendo o título específico dele.

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

A estrutura básica para criação de um grafo é feita dentro de uma função JavaScript. É necesário criar uma variável em formato de JSON  que deverá conter dois pricipais campos: 'nodes' e 'edges'.

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

Depois da criação da variável com as listas de nós e relações, é a hora de indicar o 'id' da estrutura html que receberá o gráfico, isso é feito dentro da variável 'container'. Logo após é chamada a biblioteca

## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [Vis Network](https://visjs.org/) - Biblioteca para criação de grafos de vínculos