---
layout: post
title: Desenhando com OpenCV
comments: true
categories: [OpenCV, ComputerVision]
tags: [OpenCV, Drawing, Desenhando]
---

Desenhar com o OpenCV é muito fácil. OpenCV fornece algumas funções de desenho que podem ser utilizadas em imagens com 1 ou 3 canais. Irei abordar o circulo e o retângulo.

Funções abordadas: cv2.Circle() cv2.rectangle()

## Desenhando com opencv

### Círculo

Para desenhar um círculo em uma imagem você basicamente precisa da posição x,y e o raio do círculo.

A assinatura do método é a seguinte:
cv.Circle(img, center, radius, color, thickness=1, lineType=8, shift=0)

- img – imgem que será utilizada como base.
- center – centro do círculo (x,y)
- radius – raio do círculo.
- color – cor (respeitando a ordem BGR ou RGB)
- thickness – espessura da linha. Um número negativo indica um círculo preenchido.
- lineType – Tipo de ["linha"](https://docs.opencv.org/2.4/modules/core/doc/drawing_functions.html#line)
- shift – Número de bits fracionários nas coordenadas do centro e no valor do raio (não sei explicar, rs).

Exemplo de código:

Imagem utilizada:
![CalcRGB](/images/lcd_rgb.png)

```python
#Importação das bibliotecas
import cv2
import matplotlib.pyplot as plt

#Carregando a imagem
img = cv2.imread("../DATA/lcd_calc.jpg")

#Desenhando
cv2.circle(img, center=(960,650), radius=70, color=(0,0,255), thickness=10)
#Utilizamos vermelho, respeitando os valores (B,G,R).

#Convertendo as cores
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

#Exibindo
plt.imshow(img)
```

Plot do resultado:
![CalcCircle](/images/lcd_circle.png)

### Retângulo

Para desenhar um retângulo em uma imagem você basicamente precisa da posição x,y de início (superior esquerdo) e x,y do fim do retângulo (inferior direito).

Assinatura do médoto:
cv2.rectangle(img, pt1, pt2, color[, thickness[, lineType[, shift]]])

- img - imagem base.
- pt1 - ponto inicial
- pt2 - ponto final
- cor - cor da linha
- thickness - espessura da linha, valore negativo indica um retângulo preenchido.

Exemplo de código:

```python
#Importação das bibliotecas
import cv2
import matplotlib.pyplot as plt

#Carregando a imagem
img = cv2.imread("../DATA/lcd_calc.jpg")

#Desenhando
cv2.rectangle(img, pt1=(400,400), pt2=(800,800), color=(255,0,0), thickness=cv2.FILLED, lineType=8, shift=0)
#Utilizei cv2.FILLED que é o enumerador -1 para um quadrado preenchido.

#Convertendo as cores
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

#Exibindo
plt.imshow(img)
```

Veja mais em:
[Documentação desenho básico](https://docs.opencv.org/3.4/d3/d96/tutorial_basic_geometric_drawing.html)
