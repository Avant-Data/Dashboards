<p align="center">
  <a href="" rel="noopener">
 <img width=250px height=82px src="https://i.imgur.com/zHVh1RJ.png" alt="Project logo"></a>
</p>

<h3 align="center">Sankey</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

---

<p align="center"> Diagramas de Sankey para visualização do fluxo de dados
    <br> 
</p>

## Índice

- [Sobre](#about)
- [Exemplo](#example)

## Sobre <a name = "about"></a>

Um diagrama Sankey é uma visualização usada para descrever um fluxo de um conjunto de valores para outro. Sankeys são melhor usados ​​quando você deseja mostrar um mapeamento de muitos para muitos entre dois domínios ou vários caminhos por meio de um conjunto de estágios. Podem ser construídos a partir de qualquer conjunto de dados que se tenha nós sendo ligados a outros nós e uma quantidade para representar o fluxo

## Exemplo <a name = "use"></a>

Para utilização nos painéis do AvantData, um diagrama Sankey pode ser facilmente desenvolvido com o [FusionCharts](https://www.fusioncharts.com/dev/chart-guide/standard-charts/sankey-diagram) e algum conjunto de dados.

Exemplificando um caso em qual valores são transmitido de:
- `A ⮕ M`
- `B ⮕ M`
- `B ⮕ Z`
- `M ⮕ X`
- `M ⮕ Z`

O seguinte Sankey pode ser produzido

![Exemplo de Sankey](https://i.imgur.com/V4obmBE.png)

E para criação do Sankey demonstrado, basta escrever o código dentro dos dashboards em um formulário HTML:
```js
<div id="containerSankey">Sankey vai renderizar aqui</div>

<script>
FusionCharts.ready(function() {
  var topStores = new FusionCharts({
    type: "sankey",
    renderAt: "containerSankey",
    id: "sankeyExample",
    width: "650",
    height: "400",
    dataFormat: "json",
    dataSource: {
      chart: {
        caption: "AvantData - Exemplo de Sankey",
        legendPosition: "bottom",
        linkcolor: 'blend',
        theme: "fusion"
      },
      nodes: [{
          label: "A"
        },
        {
          label: "B"
        },
        {
          label: "M"
        },
        {
          label: "X"
        },
        {
          label: "Z"
        }
      ],
      links: [{
          from: "A",
          to: "M",
          value: 713241
        },
        {
          from: "B",
          to: "M",
          value: 649851
        },
        {
          from: "M",
          to: "X",
          value: 532847
        },
        {
          from: "M",
          to: "Z",
          value: 725473
        },
        {
        from: "B",
          to: "Z",
          value: 156532
        }
      ]
    }
  }).render();
});
</script>

```
No exemplo de código, os tipos de dados são carregados pelo formato `json`, do qual existem dois conjuntos de campos, os `nodes` que representam o início e o final de cada fluxo, e os `links` que presentam o caminho entre dois nós. Os nodes precisam conter a identificação de cada nó, enquanto os links contém o ínicio, o final e o valor de cada caminho.

## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData
- [FusionCharts](https://github.com/fusioncharts) - Biblioteca de gráficos JavaScript que fornece gráficos interativos e responsivos