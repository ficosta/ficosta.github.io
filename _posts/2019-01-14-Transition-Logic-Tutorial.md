---
layout: post
title: Transition Logic Tutorial
comments: true
categories: [Vizrt, Tutorial, Transition Logic]
tags: [Transition Logic, Tutorial, Vizrt, Documentação]
---

Fala galera! Algum tempo atrás, uns 3 anos eu fiz um mini guia dos stop points para facilitar a criação de cenas mais complexas. Bora conferir!

## Transition Logic Guide

A documentação atual do Artist é bem completa e melhora a cada versão. Em meados de 2014 quando instalamos o 3.6.3 no nosso ambiente, surgiu a necessidade de uma cena complexa de master para a transição do logo da Band:

- Out
- Marca d'água
- Vivo
- Marca d'água + estrelas copa
- Vivo + estrelas copa
- Marca d'água + contagem regressiva
- Vivo + contagem regressiva

Logo a complexidade seria de 7 animações e 22 stop points, isso infelizmente não estava na documentação.

Comecei listando os stops necessários, nomeando com letras.
O - A - B - C - D - E - F

E criei um circulo ligando eles:
![TL_guide1](/images/vizrt/tl_1.jpg)

Melhorei ligando todos a todos:
![TL_guide2](/images/vizrt/tl_2.jpg)

Pronto só seguir uma linha e anotar os pontos:
![TL_Line](/images/vizrt/tl_line.png)

Como eu já tinha feito o maior, resolvi fazer todos os outros:
![TL_All](/images/vizrt/tl_all.png)

Faça o download do PDF:

[![Download](/images/pdf-icon.png)](/download/TL_Guide.pdf)

Veja sobre isso na documentação:
[Viz Artist 3.11](http://docs.vizrt.com/viz-artist-guide-3.11.pdf#page=1031)

Bom é isso. Qualquer dúvida, me escrevam. ;-)
