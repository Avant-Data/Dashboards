<h3 align="center">Carousel</h3><

---

<p align="center"> Como aplicar e utilizar um carousel (slide de imagens) usando formulários no dashboard.
    <br> 
</p>

## Índice

- [Sobre](#about)

## Sobre <a name = "about"></a>
<div id="carouselId" class="carousel slide " data-ride="carousel" style="height: 443px; width: 1100px;">    
    <ol class="carousel-indicators">
      <li data-target="#carouselId" data-slide-to="0" class="active"></li>
      <li data-target="#carouselId" data-slide-to="1"></li>
      <li data-target="#carouselId" data-slide-to="2"></li>
    </ol>    
    <div class="carousel-inner">        
      <div class="carousel-item active">
        <img class="d-block w-100" src="https://i.imgur.com/nIe5gQ3.png" alt="Primeiro Slide" style="height: 443px; width: 1100px;">
      </div>      
      <div class="carousel-item">
        <img class="d-block w-100" src="https://i.imgur.com/TLCoE7u.png" alt="Segundo Slide" style="height: 443px; width: 1100px;">
      </div>      
      <div class="carousel-item">
        <img class="d-block w-100" src="https://i.imgur.com/cqgv6LH.png" alt="Terceiro Slide" style="height: 443px; width: 1100px;">
      </div>      
    </div>    
    <a class="carousel-control-prev" href="#carouselId" role="button" data-slide="prev">
      <span class="">Anterior</span>
    </a>
    <a class="carousel-control-next" href="#carouselId" role="button" data-slide="next">
      <span class="">Próximo</span>
    </a>    
</div>
<script>
    $(document).ready(function () {
        $('.carousel').carousel({
            interval: 3000
        })            
    });    
</script>
...

## Construído Utilizando <a name = "built_using"></a>

- [AvantData](https://www.avantdata.com.br/) - Plataforma de análise, correlacionamento e gestão de dados em redes corporativas
- [AvantApi](https://avantapi.avantsec.com.br/) - Família de endpoints RESTFUL API para customização de ações no AvantData