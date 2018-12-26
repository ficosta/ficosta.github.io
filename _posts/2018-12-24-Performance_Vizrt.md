---
layout: post
title: Performance Vizrt
comments: true
categories: [Vizrt, troubleshooting]
tags: [troubleshooting, vizrt, Performance]
---

Essa é uma tradução dos itens da página 277 do manual [Viz Artist 3.11](http://docs.vizrt.com/viz-artist-guide-3.11.pdf#page=277)

## Propriedades da barra de performance.

- **VER (Vertices):** Mostra o número de vetores na cena.
- **TET (AllocTexSize):** Mostra o total de memória de textura alocada.
- **TEC (TexSize):** Mostra o total de memória de textura em uso.
- **ANI (Animation):** Mostra quantos microsegundos os diretores e os canais de animação estão utilizando. Esse indicador é reprensentado com a barra amarela.
- **MAT (Matrix):** Tempo utilizado para tranformar cada container em coordenadas. Esse indicador possui a cor ciano na barra.
- **Z&C (Z-Sort):** Refere-se ao Z-sort e Culling, e classifica todos os contêineres para o desenho de transparência correto e determina se os contêineres estão visíveis na visualização atual da câmera. Este indicador está ligado à barra rosa.
- **VID (Video):** Mostra quantos microssegundos de entrada de vídeo (mídia de vídeo ao vivo) e saída de vídeo. Entradas de vídeo desentrelaçadas levam mais tempo do que o progressivo e o entrelaçado.
  A única maneira de melhorar esse valor é usar uma placa de vídeo mais rápida. Este indicador está ligado à barra vermelha.
- **REN (Rendering):** Mostra quantos microsegundos leva para renderizar todos os elementos.
  Uma placa mais rápida irá melhorar esse valor. Esse indicador está ligado à barra azul.
- **PLU (plug-in):** Mostra quantos microsegundos todos os plugins ativos gastam em cada ciclo de render. Este indicador está ligado à barra laranja.
- **SCR (Script):** Mostra o tempo consumido em microsegundos de todos os scripts ativos. Este indicador está ligado à barra verde escuro.
- **CUR (Current):** Mostra quantos quadros por segundo a cena renderizará no modo On Air.
  O número deve estar acima de 50 (PAL) ou 60 (NTSC), de acordo com a taxa especificada na guia _Formato de saída_.
- **MAX (Maximum):** Mostra quantos frames/s a cena pode renderizar sem esperar pelo retorno vertical. Quanto maior o valor máximo, mais desempenho resta. Se o valor máximo for reduzido para abaixo de 50 ou 60, a cena não será renderizada em tempo real.
- **Blue bar:** Mostra o numero de frames/s usados
- **Green bar:** Mostra o numero de frames/s disponíveis.
  A taxa de atualização da barra de performance pode ser modificada na guia _User Interface_ dentro de _Config_.

Veja mais em [Youtube](https://youtu.be/z7Iu4OsoUq0).

Qualquer dúvida, me escreva!
