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

Ao abrir a modal de edição, cole o código fonte no espaço de texto. Atente-se às dimensões desejadas. Esse modelo está com o padrão de altura em 800px, e todos os cabeçalhos precisam ter a largura de “muito grande”.

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
## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar esse cabeçalho em outros paineis, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

## Código fonte <a name = "font_code"></a>
## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [MDBootstrap](https://mdbootstrap.com/) - Biblioteca de aparências e estilos 
- [DataTable](https://datatables.net/) - Biblioteca de montagem e formatação de tabelas. 