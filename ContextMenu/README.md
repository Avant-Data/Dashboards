<p align="center">
  <a href="" rel="noopener">
 <img width=200px height=200px src="https://i.imgur.com/6wj0hh6.jpg" alt="Project logo"></a>
</p>

<h3 align="center">Menu de contexto</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> Como aplicar e utilizar um menu de contexto dentro dos formulários no dashboard.
    <br> 
</p>

## 📝 Conteúdo

- [Sobre](#about)
- [Começando](#getting_started)
- [Deployment](#deployment)
- [Usage](#usage)
- [Built Using](#built_using)
- [TODO](../TODO.md)
- [Contributing](../CONTRIBUTING.md)
- [Authors](#authors)
- [Acknowledgments](#acknowledgement)

## 🧐 Sobre <a name = "about"></a>

Um "Menu de contexto" é uma janela de opções que aparece quando o usuário clica com o botão direito do mouse. Ao opções que serão exibidas estão sempre ligadas com a região da tela em que foi clicada.

Nesse modelo, a estrutura do menu de contexto será montada utilizando uma função na linguagem JavaScript interagindo com o HTML onde será aplicado, que pode variar de usuário para usuário. 

Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.

![Exemplo de Menu de Contexto](https://i.imgur.com/gKq9buh.png)

## 🏁 Começando <a name = "getting_started"></a>

Ao baixar o código fonte, o usuário deve copiar toda a função 'contextMenuFomulário' e colar na janela de edição de formulário. É importante notar que essa função só funciona se estiver dentro de uma tag html de script.

Ao fazer isso é necessário executar a função, passando como argumento o id (entre aspas) do elemento  html que vai receber o menu. Uma forma de fazer isso é chamar a função quando o documento estiver pronto. No próprio código fonte já existe um exemplo dessa interação, como no exemplo abaixo.
![Exemplo de documento pronto](https://i.imgur.com/rPDu6Zp.png)

Obs: Caso ja tenha alguma função com esse mesmo nome, é necessário alterá-lo para que não haja conflito sobre qual função deve ser usada.




### Configurando opções

A estrutura de um menu de contexto é criada dentro de uma variável "var" em um formato JSON. Cada uma das opções é separada em um bloco dentro dessa estrutura com um padrão que deve ser mantido. Caso o menu tenha subopções, elas também são separadas em blocos dentro das opções.

Dessa forma é possível adicionar ou remover opções e suboções do menu de contexto adicionando ou removendo blocos. É possível também alterar o nome de cada opção substituindo o campo de 'texto'(grifados em vermelho)
![Blocos de opções](https://i.imgur.com/srvjU9H.png)

### Installing

A step by step series of examples that tell you how to get a development env running.

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo.

## 🔧 Running the tests <a name = "tests"></a>

Explain how to run the automated tests for this system.

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## 🎈 Usage <a name="usage"></a>

Add notes about how to use the system.

## 🚀 Deployment <a name = "deployment"></a>

Add additional notes about how to deploy this on a live system.

## ⛏️ Built Using <a name = "built_using"></a>

- [MongoDB](https://www.mongodb.com/) - Database
- [Express](https://expressjs.com/) - Server Framework
- [VueJs](https://vuejs.org/) - Web Framework
- [NodeJs](https://nodejs.org/en/) - Server Environment

## ✍️ Authors <a name = "authors"></a>

- [@kylelobo](https://github.com/kylelobo) - Idea & Initial work

See also the list of [contributors](https://github.com/kylelobo/The-Documentation-Compendium/contributors) who participated in this project.

## 🎉 Acknowledgements <a name = "acknowledgement"></a>

- Hat tip to anyone whose code was used
- Inspiration
- References