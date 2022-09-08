<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>


<h3 align="center">Menu de contexto</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> Como aplicar e utilizar um menu de contexto dentro dos formulários no dashboard.
    <br> 
</p>

## Conteúdo

- [Sobre](#about)
- [Começando](#getting_started)
- [Utilização](#usage)
- [Construído Utilizando](#built_using)


##  Sobre <a name = "about"></a>

Um "Menu de contexto" é uma janela de opções que aparece quando o usuário clica com o botão direito do mouse. Ao opções que serão exibidas estão sempre ligadas com a região da tela em que foi clicada.

Nesse modelo, a estrutura do menu de contexto será montada utilizando uma função na linguagem JavaScript interagindo com o HTML onde será aplicado, que pode variar de usuário para usuário. 
```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```

![Exemplo de Menu de Contexto](https://i.imgur.com/gKq9buh.png)

## Começando <a name = "getting_started"></a>

Ao baixar o código fonte, o usuário deve copiar toda a função 'contextMenuFomulário' e colar na janela de edição de formulário. É importante notar que essa função só funciona se estiver dentro de uma tag html de script.

Ao fazer isso é necessário executar a função, passando como argumento o id (entre aspas) do elemento  html que vai receber o menu. Uma forma de fazer isso é chamar a função quando o documento estiver pronto. No próprio código fonte já existe um exemplo dessa interação, como no exemplo abaixo.

```js
$(document).ready(() => {
  contextMenuFormulario('id-do-elemento-html-que-vai-receber-o-menu')
})
```

```
Obs: Caso ja tenha alguma função com esse mesmo nome, é necessário alterá-lo para que não haja conflito sobre qual função deve ser usada.
```



### Configurando opções

A estrutura de um menu de contexto é criada dentro de uma variável "var" em um formato JSON. Cada uma das opções é separada em um bloco dentro dessa estrutura com um padrão que deve ser mantido. Caso o menu tenha subopções, elas também são separadas em blocos dentro das opções.

Dessa forma é possível adicionar ou remover opções e suboções do menu de contexto adicionando ou removendo blocos sempre seguindo o padrão estrutural. É possível também alterar o nome de cada opção substituindo o campo de 'texto'(grifados em vermelho)
![Blocos de opções](https://i.imgur.com/srvjU9H.png)

Para alterar o ícone que aparece ao lado de cada opção, é necessário alterar o atributo "class" do campo 'icon' em cada bloco. Será disponibilizado um arquivo com várias classes diferentes que poderão ser utilizadas para customizar o menu.
```
Obs: Ao fazer qualquer alteração, é necessário prestar atenção para não deixar nenhuma chave, parêntese ou colchete aberto ou desalinhado, pois eles são os separadores de cada bloco, e portanto fundamentais.
```

##  Utilização <a name="usage"></a>

O campo de uso dos menus de contexto são infinitos, se limitando somente a criatividade e a capacidade do usuário. A mecânica de adicionar opções permite ativar comandos através de poucos cliques.

Comumente usados no AvantData para deletar ítens ou carregar tabelas, importar ou exportar  arquivos, editar dados, limpar campos de formulário, enviar requisições API e muito mais. 


##  Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [MDBootstrap](https://mdbootstrap.com/) - Biblioteca de aparências e estilos 

