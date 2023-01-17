<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
<h3 valign="center">Cabeçalho</h3>

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
- [Usando Token](#token_use)
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

## Usando Token <a name = "token_use"></a>

Um dos usos mais comuns dos cabeçalhos no dashboard é poder gerar pequenas configurações que servirão de parâmetro para os gráficos. Chamamos isso de <i>token</i>. Esse modelo é composto a partir de alguns campos de input e um botão abaixo do corpo padrão do cabeçalho.

![Tipos de cores](https://i.imgur.com/4JSM8uY.png)

Nesse modelo, juntamente com o código fonte <b><i>header_token.html</i></b> nessa lista de arquivos, traz um exemplo com campos de datas. A ideia é trazer um cabeçalho onde o usuário vai inserir uma data inicial e uma final e ao clicar no botão, vai salvar essas informações em <i>tokens</i>, os gráficos abaixo desse painel vão estar configurados para filtrar as datas desses <i>tokens</i>. Assim o usuário poderá customizar o intervalo de tempo utilizando o cabeçalho sem precisar abrir uma nova configuração de gráficos.

```
OBS: Aqui utilizamos a ideia de enviar campos de data como token, mas a mesma lógica pode ser usada para criar tokens de vários outros formatos para criar outros tipos de filtros.
```
Para a confecção do sistemas de <i>token</i>, no código será necessário adicionar alguns campos em <i>HTML</i> e também uma pequena e simples composição em <i>JavaScript</i>.

Abaixo está o bloco em HTML que será adicionado, que por sua vez é dividido em outros 3 blocos. O primeiro e o segundo são composições que montam os campos input onde o usuário vai inserir as data ( type="datetime-local" ). O terceiro bloco é a composição que monta o botão de nome 'Token' que ao ser clicado vai executar uma função que está montada em JavaScrip ( onclick="makeTokens()" )

```html
<div class="ml-3 mr-3 " style="background-color: white; margin-top: -7px ">
    <div class="md-form md-outline float-left input-group " style="width: 600px; margin-top: 10px; ">
            
        <!-- bloco do campo de data inicial -->
        <div class="input-group-prepend">
            <span class="input-group-text" 
            style="border-radius: 10px 0px 0px 10px; border-color: #38a0a4 !important; border-width: medium; background-color:#38a0a4; color: white; height: 34px !important ;font-size: 1.0em;">Inicial</span>
        </div>
        <input type="datetime-local" id="inicialDate" class="form-control bg-white mr-1"
            aria-describedby="inputTasksFormScanInputGroup" placeholder="Data Inicial"
            style="border-radius: 0px 10px 10px 0px; border-color: #38a0a4 !important; border-width: medium; height: 34px !important;color:black ;font-size: 1.0em;">


        <!-- bloco do campo de data final -->
        <div class="input-group-prepend">
            <span class="input-group-text" 
            style="border-radius: 10px 0px 0px 10px; border-color: #38a0a4 !important; border-width: medium; height: 34px !important;background-color:#38a0a4; color: white;font-size: 1.0em;">Final</span>
        </div>
        <input type="datetime-local" id="finalDate" class="form-control bg-white"
        aria-describedby="inputTasksFormScanInputGroup" placeholder="Data Inicial"
        style="border-radius: 0px 10px 10px 0px; border-color: #38a0a4 !important; border-width: medium; height: 34px !important;color:black ;font-size: 1.0em;">
        
        <!-- bloco do botão-->
        <a onclick="makeTokens()"><span class="input-group-text font-weight-bold text-white  text-center"
            id="inputTasksFormScanInputGroup"
            style="border-radius: 10px; height: 34px !important ;font-size: 1.2em; padding-top: -10px; background-color: #e96817;">Token</span></a>
        
    </div>    
</div>
```
Como essa opção conta com funções em JavaScript, qualquer código que seja feito nessa linguagem deve <b>obrigatotiamente</b> estar montado dentro das tags \<script> \</script>, caso contrário vai acarretar em erros profundos na execução de todo esse projeto.

A função 'makeTokens()' que será executada, inicia resgatando os valores inseridos nos campos de data e verificando se algum dos campos está vazio, e caso estejam, vai interromper a execução e enviar um aviso que os campos são obrigatórios.
Campos de data costumam estar em diversos formatos, por isso nesse modelo trouxemos dentro dessa função 3 opções de formatos que são comumente usados para fazer pesquisas em bancos de dados.

Em seguida é criada uma variavel 'dado' que é do tipo objeto. A partir dela são criados os nomes e os valores (chave -> valor) que serão transformados em <i>tokens</i>. Por exemplo, 'dado.Aniversario' dará origem a um <i>token</i> cuja chave é 'Aniversário', dessa forma dizer que 'dado.Aniversario = 11/11/2000' dará origem ao <i>token</i> de chave 'Aniversário' cujo valor é '11/11/2000'. 

No caso do código fonte, os <i>tokens</i> estão sendo cirados com os nomes "dataInicial" e "dataFinal", mas podem ser alterados da forma que o usuário achar melhor, inclusive acrescentar ou deletar algumas dessas opções. Já os valores estão sendo dados com variáveis ja anteriormente criadas. Por padrão o AvantData utiliza o formato <i>epoch</i> para criar um filtro de campo chamado <i>GenerateTime</i>, por isso é utilizado o formato <i>epoch</i> como valor da variável, que será o valor do <i>token</i>.

A variável 'dados' e todas as suas configurações de chave e valor serão enviadas para a função nativa do AvantData de nome 'applyDashboard(dados)' que vai criar os <i>tokens</i> no navegador e recarregar os gráficos.

```js
function makeTokens() {
    //Criação das variaveis que buscam os valores inseridos nos campos de data. Formato: 2023-01-15T17:27
    let dateInputInicial = $('#inicialDate').val()
    let dateInputFinal = $('#finalDate').val()
    
    //Verifica se os campos de data estão vazios
    if(dateInputInicial == '' || dateInputInicial == undefined || dateInputFinal == '' || dateInputFinal == undefined) {
        toastr.warning('Os campos são obrigatórios', 'Aviso', { positionClass: "toast-bottom-right",closeButton: "true"});
        return
    }

    //Criação de variáveis que resgata os valores de data escolhidos e edita num formato legível. Ex:2023/01/15 17:27:00
    let dateformatInicial = formatDate(dateInputInicial)
    let dateformatFinal = formatDate(dateInputFinal)        
    
    //Criação de variáveis que resgata os valores de data escolhidos e edita num formato epoch. Ex:1673814420000
    let epochDateInicial = new Date(dateInputInicial).valueOf() 
    let epochDateFinal = new Date(dateInputFinal).valueOf()        
    
    // Criação de variável do tipo objeto onde os nomes das chaves serão os nomes das chaves do token. 
    // Ex: 'dado.teste = 10' vai gerar um token com nome 'teste' cujo valor é '10'
    let dados = {}
    dados.dataInicial = epochDateInicial
    dados.dataFinal = epochDateFinal

    //Função nativa do AvantData que cria os tokens baseados no objeto enviado e recarrega os gráficos
    applyDashboard(dados);
}
```
Um dos formatos de data utiliza a função 'formatDate(date)' para formatar os valores de data inseridos para um formato humanamente legível. Essa função está presente no código fonte.

```js
function formatDate(date) {
    let dateTemp = date.split('T')[0];
    let hourTemp = date.split('T')[1];

    if (hourTemp.length < 6) {
        hourTemp = hourTemp + ":00";
    }

    tmp = dateTemp.split('-');
    return tmp[0] + "/" + tmp[1] + "/" + tmp[2] + " " + hourTemp;
}
```
Para utilizar os tokens nos gráficos de criação rápida, é necessário fazer algumas configurações na hora de criar cada um deles. Na montagem da pesquisa existe um campo de filtros->Intervalo de pesquisa, por padrão o AvantData utiliza o campo GenerateTime como indicador de tempo, mas a depender do dado utilizado podem existir outros que o usuário prefira, cada qual com um formato de data específico. Ao clicar com o botão direito do mouse sobre o campo vai aparecer um menu de contexto com a opção 'Editar Campo'.


![Tipos de cores](https://i.imgur.com/NCp8q0E.png)

Ao clicar nessa opção, vai abrir uma modal com vários atalhos de tempos comuns a serem pesquisados, mas para utilizar os <i>tokens</i> o que interessa é parte inferior "Variável". Nesse bloco existem dois campos que se altocompletam com as opções de todos os <i>tokens</i> disponívels para ajustar as data de início e fim da busca. O usuário deve escolhê-los pelo nome e clicar no botão 'TOKEN' abaixo. Com isso o gráfico sempre vai buscar os valores indicados variavelmente pelos <i>tokens</i> com aqueles nomes.
![Tipos de cores](https://i.imgur.com/bc28qjr.png)


## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar em outros paineis, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

O mesmo acontece com os nomes de cada 'function' JavaScript, cada nome deve ser único para cada cópia desse modelo em uma visualização, tanto na criação, quando na hora de executar.


## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [MDBootstrap](https://mdbootstrap.com/) - Biblioteca de aparências e estilos 