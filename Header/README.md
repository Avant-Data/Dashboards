<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>
<h3 align="center">Cabeçalho</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> Como aplicar e utilizar um cabeçalho para uma visualização no dashboard.
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Começando](#starting)
- [Customizando](#editing)
- [Posicionamento](#position)
- [Precauções](#precaution)
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>

![Exemplos de Cabeçalho](https://i.imgur.com/0VIjzr1.png)

Um cabeçalho é uma visualização inicial dentro de um painel do dashboard. Ele traz um contexto sobre o que está sendo posto em gráficos.

Nesse modelo, a estrutura será montada em html, utilizando classes de uma biblioteca Bootstrap

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```
## Começando <a name = "starting"></a>

Nesse tutorial, juntamente com o código fonte, utilizaremos o modelo azul. Inicialmente, para montar um cabeçalho, é necessário criar um novo cartão do tipo “formulário” através do menu de contexto.
![Criando Cartão](https://i.imgur.com/Sx9hPLC.png)

Ao abrir a modal de edição, cole o código HTML fonte no espaço de texto. Atente-se às dimensões do cabeçalho. Esse modelo está com o padrão de altura em 190, e todos os cabeçalhos precisam ter a largura de “muito grande”.

![Dimensões](https://i.imgur.com/M1eJx88.png)

## Customizando <a name = "editing"></a>

Para alterar o valor dos campos de “Tarefa”, “Título” e “Subtítulo”, basta substituir o texto dos campos conforme a imagem a seguir.

![Editando texto](https://i.imgur.com/mY0OKIt.png)

Para mudar a imagem de logo, localizada a esquerda, é necessário alterar o atributo “src” da tag HTML “img”. É necessário que a imagem esteja em formato base64 para ser acoplada ao código. 

O formato base64 é uma codificação da imagem, transformando-a em um grande texto com caracteres diversos. Note que o código fonte baixado já está com a imagem do logo da AvantData branco por padrão já em formato base64.

Ao alterar a imagem, caso ela fique com proporções erradas ou distorcidas, é possível alterar a largura e altura da imagem, aumentando ou diminuindo a quantidade de pixels (px), conforme imagem a seguir.

![Dimensões imagem](https://i.imgur.com/zeBeVFW.png)

### Alterando Cores

Caso queira alterar as cores do cabeçalho, é necessário mudar alguns atributos básicos de cor, entre eles o “background-color”, “color” ou “border-color”. Na linguagem HTML as faixas de cores podem ser descritas de três formas: usando padrão RGB, padrão Hexadecimal ou nomeando cores básicas em inglês.

```
color=" blue ;"         --> Cores básicas
color=" #38a0a3 ;"      --> Formato Hexadecimal
color=" 255 250 250 ;"  --> Formato RGB
```

É importante saber qual elemento do código correspone a qual descrição de cor e como isso será traduzido na visualização final. Vale ressaltar que os textos também tem suas cores estabelecidas.

![Tipos de cores](https://i.imgur.com/hROzDxH.png)


## Posicionamento <a name = "position"></a>

Existe a possibilidade de criar um cabeçalho em um painel onde já tenha gráficos. É padrão do AvantData colocar os cartões do dashboard na órdem em que eles foram criados, dessa forma o cabeçalho pode ser jogado para o final do painel. Para trazê-lo ao ínicio, existe um botão de movimentação no canto superior direito de cada painel, permitindo que o usuário reordene os cartões (gráficos, mapas, formulários e etc) na posição que quiser, sendo necessário salvar essa mudança com o mesmo botão.

![Tipos de cores](https://i.imgur.com/K2dbbzI.png)

## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte não conta com nenhum elemento HTML com atributo "id" e por isso, pode-se usar esse cabeçalho em quantos paineis quiser, mesmo dentro de uma mesma visualização.

Entretanto, caso o usuário precise adicionar um atributo "id", ele deve ser ÚNICO para cada elemento, em cada cabeçalho da mesma visualização, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.


## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [MDBootstrap](https://mdbootstrap.com/) - Biblioteca de aparências e estilos 