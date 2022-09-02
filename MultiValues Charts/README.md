<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>

<h3 align="center">Gráficos de Valores Múltiplos</h3>
<h5 align="center">Linha, Área, Coluna e Barra</h5>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> (Descrição dos Gráficos)
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Construído Utilizando](#built_using)

## Sobre <a name = "about"></a>

![Exemplos de Gráficos](https://i.imgur.com/iwWqfn7.png)

Um gráfico é uma representação visual de comparação entre elementos.Visualização de dois eixos (X e Y) indicando nome e valor de cada ítem. Ao passar o mouse sobre cada elemento, ele é ressaltado aparecendo uma pequena janela contendo o nome e valor do campo específico. Esse modelo pode ser usado para criar um gráfico dos tipos <i>Linha, Área, Barras e Colunas</i> com exatamente a mesma estrutura, diferenciando apenas o atributo "type" (tipo).

A diferença do<i> gráfico de valores múltiplos </i>e <i>[gráfico simples](https://github.com/Avant-Data/Dashboards/tree/master/Simple%20Charts)</i> está na quantidade de elementos por valor. Ou seja, o gráfico simples consegue apenas apresentar um ítem (eixo Y) por ítem (eixo X), enquanto o gráfico de valores múltiploes consegue apresentar varios valores (eixo X) por ítem (eixo Y).

Nesse modelo, a estrutura e a visualização são criadas através de uma biblioteca JavaScript para criação dinâmica de gráficos chamada Fusion Charts. No código fonte, trazemos a opção de preencher o gráfico dinamicamente, atravez de uma pesquisa.

Esse modelo é específico para usuários que queiram montar utilizando a estrutura em formulário, visto que esses tipos de gráfico podem ser facilmente gerados usando a criação dinâmica de gráficos no menu de contexto, ao invéz de criar um novo 'formulário', escolhendo "cartão'.

```
Obs: Esse modelo é criado para ser usado nos cartões de formulário no Dashboard do AvantData, visto que depende de bibliotecas ja instaladas no programa.
```

## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData