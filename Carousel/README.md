<h3 align="center">Carousel</h3><

---

<p align="center"> Como aplicar e utilizar um carousel (slide de imagens) usando formulários no dashboard.
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Começando](#starting)
- [Estrutura](#structure)
- [Customizando imagens](#images)
- [Precauções](#precaution)
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>
![Exemplos de carousel](https://i.imgur.com/dLaUv2D.png)

Carousel é um slide de imagens que vão passando de acordo com um tempo determinado, com a opção de avançar ou retroceder manualmente com um clique nas laterais ou nos pontos de indicação inferior da ordem de cada ítem. Ao descansar o mouse sobre o carousel, ele para de girar, para que o usuário possa focar ou observar melhor o ítem que está sendo mostrado.

Nesse modelo, a estrutura será montada em HTML com <b>classes</b> de [Bootstrap](https://getbootstrap.com.br/docs/4.1/components/carousel/#:~:text=fosse%20um%20carrosel.-,Como%20funciona,controles%20anterior%2C%20pr%C3%B3ximo%20e%20indicadores.), que é uma biblioteca de estilos e visualizações que são fundamentais para o funcionamento do slide.

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```
## Começando <a name = "starting"></a>

Inicialmente, para montar um carousel, é necessário criar um novo cartão do tipo “formulário” através do menu de contexto.

![Criando Cartão](https://i.imgur.com/Sx9hPLC.png)

Ao abrir a modal de edição, cole o código fonte no espaço de texto. Atente-se às dimensões desejadas. Esse modelo está com o padrão de altura em 430px e largura de “muito grande”.

## Estrutura <a name = "structure"></a>

Esse modelo vem com padrão de 3 imagens (logo do AvantData com planos de fundo de cores diferentes), mas o usuário pode acrescentar ou remover essa quantidade, desde que siga o padrão do código fonte. 

Inicialmente temos a montagem da estrutura do "índice" de cada imagem, que são os pontos na parte de baixo do carousel, onde é possivel clicar. Cada um desses pontos está vinculado a uma imagem, dessa forma ao adicionar ou remover imagens, deve-se também acrescentar ou diminuir a quantidade de índices. Eles são endereçados a cada ítem do carousel com a estrutura 'data-slide-to="x"' onde 'x' representa o número de sequencia da imagem (sempre começando do 0).

Cada um deles também deve estar ligado ao 'id' da divisão geral, que no caso do modelo é 'carouselId'.

```html
<div id="carouselId" data-interval="3000" class="carousel slide " data-ride="carousel" style="height: 417px; width: 1030px;">
    
  <ol class="carousel-indicators">
    <li data-target="#carouselId" data-slide-to="0" class="active"></li>
  
    <li data-target="#carouselId" data-slide-to="1"></li>
  
    <li data-target="#carouselId" data-slide-to="2"></li>
  
  </ol>
  
  <div class="carousel-inner">
      
    <div class="carousel-item active">
      <img class="d-block w-100" src="https://i.imgur.com/nIe5gQ3.png" alt="Primeiro Slide" style="height: 417px; width: 1030px;">
    </div>
    
    <div class="carousel-item">
      <img class="d-block w-100" src="https://i.imgur.com/TLCoE7u.png" alt="Segundo Slide" style="height: 417px; width: 1030px;">
    </div>
    
    <div class="carousel-item">
      <img class="d-block w-100" src="https://i.imgur.com/cqgv6LH.png" alt="Terceiro Slide" style="height: 417px; width: 1030px;">
    </div>
    
  </div>
  
  <a class="carousel-control-prev" href="#carouselId" role="button" data-slide="prev">
    <span class="">Anterior</span>
  </a>
  <a class="carousel-control-next" href="#carouselId" role="button" data-slide="next">
    <span class="">Próximo</span>
  </a>
  
</div>
```

Cada imagem corresponde a um bloco com classe="carousel-item" (sendo que o primeiro dele deve deve conter um atributo 'active' para iniciar a volta). É necessário sempre corresponder a quantidade de imagens à quantidade de 'índices'.

![Quantidade de imagens](https://i.imgur.com/bUxol4z.png)

Ao final, são criadas as estruturas para passar para a próxima imagen ou retroceder para a anterior. É possível mudar os textos de 'Anterior' e 'Próximo' para qualquer outro, incluindo sinais ou símbolos, ou até mesmo deixando-os vazios (isso ainda vai permitir o usuário clicar nas bordas para ativar o efeito de avançar ou retroceder.)

```
Obs: Logo na primeira linha existe um atributo 'data-interval' que define a quantidade de tempo para cada ítem do carousel avançar, onde:
1 segundo = 1000
```

## Customizando imagens <a name = "images"></a>

Cada ítem do carousel, ja mensionado acima, contém uma tag HTNL de 'img'.
```html
<img class="d-block w-100" src="https://i.imgur.com/nIe5gQ3.png" alt="Primeiro Slide" style="height: 443px; width: 1100px;">
```
Dentro do atributo 'src' (source = fonte) é onde deve-se colocar o caminho de onde a imagem será adicionada. Pode-se colocar o caminho da URL da imagem. Pode-se também adicionar a formatação base64 que é uma codificação da imagem, transformando-a em um grande texto com caracteres diversos.

Após adicionar as imagens, o usuário deve-se atentar ao tamanho de cada uma delas, visto que pode ocorrer das dimensoes originais serem muito diversas entre si e assim ficarem distorcidas na versão final. Para isso existem campos de customização, para ajustar altura (height) e largura (width) de cada ítem e também do tamanho geral do carousel.

![Ajuste de tamanho](https://i.imgur.com/fqeSnCb.png)

Após a customização o carousel ja está pronto para ser executado. Essa etapa de ativação é feita dentro da tag HTML de 'script' e por isso é criada em linguagem JavaScript.
```js
$(document).ready(function () {
    $('.carousel').carousel()     
    
});
```
## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar em outros paineis, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

O mesmo acontece com os nomes de cada 'function' JavaScript, cada nome deve ser único para cada cópia desse modelo em uma visualização, tanto na criação, quando na hora de executar.
## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [Bootstrap](https://getbootstrap.com.br/) - Biblioteca de aparências e estilos