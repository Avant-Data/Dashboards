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
- [Começando](#starting)
- [Peculiaridades](#peculiar)
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


## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [Vis Network](https://visjs.org/) - Biblioteca para criação de grafos de vínculos