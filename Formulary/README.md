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
<!-- - [Customizando imagens](#images) -->
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
## Precauções <a name = "precaution"></a>

O modelo disponibilizado pelo código fonte conta com alguns elementos HTML com atributo "id" e por isso, para usar em mais de um painel, é necessário alterar todos os atributos "id" e todos os lugares onde ele é utilizado.

Os atributos "id" são uma identidade ÚNICA de cada elemento, caso contrário ele pode ter problemas para funcionar gerando conflitos na leitura do código pelo navegador.

O mesmo acontece com os nomes de cada 'function' JavaScript, cada nome deve ser único para cada cópia desse modelo em uma visualização, tanto na criação, quando na hora de executar.
## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [Bootstrap](https://getbootstrap.com.br/) - Biblioteca de aparências e estilos
- [JQuery](https://jquery.com/) - Biblioteca para JavaScript que facilita a integração entre HTML e JavaScript.