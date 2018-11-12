---
layout: post
title: Template Matching
comments: true
categories: [OpenCV, ComputerVision]
tags: [OpenCV, Matching]
---

Template Matching é um metodo para buscar a localização de uma pequena parcela de uma imagem (template) em um imagem maior.

Funções abordadas: cv2.matchTemplate()

## Template Matching

A forma de comparação do OpenCV simplismente compara a imagem do modelo deslizando sobre a imagem de entrada. O OpenCV implementa diversos algoritimos de comparação e retorna uma imagem em tons de cinza, em que cada pixel corresponde ao modelo.

- cv2.TM_CCOEFF
- cv2.TM_CCOEFF_NORMED
- cv2.TM_CCORR
- cv2.TM_CCORR_NORMED
- cv2.TM_SQDIFF
- cv2.TM_SQDIFF_NORMED

A assinatura do método é a seguinte:
matchTemplate(image, templ, method)

- image - imagem que será pesquisada
- templ - imagem do modelo
- method - um dos métodos acima

[Exemplo de código](https://docs.opencv.org/trunk/d4/dc6/tutorial_py_template_matching.html):

Imagem utilizada:
![CalcRGB](/images/lcd_rgb.png)

Template:

![LCDButton](/images/lcd_x.jpg)

```python
#Importação das bibliotecas
import cv2
import numpy as np
import matplotlib.pyplot as plt

#Imagem da calculadora
calc = cv2.imread('../lcd_calc.jpg')
calc = cv2.cvtColor(calc, cv2.COLOR_BGR2RGB)

#Imagem do botão
button= cv2.imread('../lcd_x.jpg')
button = cv2.cvtColor(button, cv2.COLOR_BGR2RGB)

#Lista de todos os metodos para comparação. Estão como uma lista de string. Iremos utilizar o eval para converter em método.
methods = ['cv2.TM_CCOEFF', 'cv2.TM_CCOEFF_NORMED', 'cv2.TM_CCORR','cv2.TM_CCORR_NORMED', 'cv2.TM_SQDIFF', 'cv2.TM_SQDIFF_NORMED']

for m in methods:
       #Cria uma cópia da imagem. Precisamos dela, pois iremos desenhar sobre a imagem.
       full_copy = calc.copy()

       #converte a string da lista para método.
       method = eval(m)

       #Realiza a busca com matchTemplate. Retorna e armazena em "res"
       res = cv2.matchTemplate(full_copy, button, method)

       #Encontra a localização para desenhar o quadrado.
       min_val, max_val, min_loc, max_loc = cv2.minMaxLoc(res)

       if method in [cv2.TM_SQDIFF, cv2.TM_SQDIFF_NORMED]:
           top_left = min_loc #(x,y)
       else:
           top_left = max_loc

       #Pega as propriedades da imagem inicial
       height, width, channels = button.shape

       #Define os quadrantes
       botton_right = (top_left[0]+ width, top_left[1]+height)

       #Desenha o quadrado
       cv2.rectangle(full_copy, top_left, botton_right, (255,0,0), 10)

       #Faz a plotagem
       plt.subplot(121)
       plt.imshow(res) #Imagem de cinza
       plt.title("Heatmap")

       plt.subplot(122)
       plt.imshow(full_copy) #Imagem com o quadrante
       plt.title("Resultado")

       plt.suptitle(m) #Adiciona o método como título

       plt.show() #Exibe o resultado
```

Plot dos resultados:

![TM_CCOEFF](/images/matching/TM_CCOEFF.png)

![TM_CCOEFF_NORMED](/images/matching/TM_CCOEFF_NORMED.png)

![TM_CCORR](/images/matching/TM_CCORR.png)

![TM_CCORR_NORMED](/images/matching/TM_CCORR_NORMED.png)

![TM_SQDIFF](/images/matching/TM_SQDIFF.png)

![TM_SQDIFF_NORMED](/images/matching/TM_SQDIFF_NORMED.png)

Só o método TM_CCORR não funcionou corretamente. Experimente com outras imagens. ;-)

Veja mais em:
[Documentação e reconhecimento de multiplo](https://docs.opencv.org/trunk/d4/dc6/tutorial_py_template_matching.html)
