---
layout: post
title: Thresholding com OpenCV
comments: true
categories: [OpenCV, ComputerVision]
tags: [OpenCV, Threshold]
---

No post de hoje iremos falar sobre a função threshold do OpenCV. Ela possui diversas aplicações, remoção de ruido, remoção de variações de iluminação de uma imagem e claro, normalizar uma imagem em apenas 2 cores.

Funções abordadas: cv2.threshold() e cv2.adaptiveThreshold()

## Simples Threshold

De forma direta, essa método aplica um determinado valor a um pixel se o valor for acima do definido ou outro se o valor for menor.
O OpenCV implementa diferentes tipos de limiarização "thresholding".

- cv2.THRESH_BINARY
- cv2.THRESH_BINARY_INV
- cv2.THRESH_TRUNC
- cv2.THRESH_TOZERO
- cv2.THRESH_TOZERO_INV

A assinatura do método é a seguinte:
cv.threshold(src, thresh, maxval, type[, dst])

- src - array de origem (imagem)
- thresh - valor do limiar
- maxval - valor máximo (usado com THRESH_BINARY e THRESH_BINARY_INV)
- type - tipos apresentados acima.

Exemplo código:

Imagem RGB:

![CalcRGB](/images/lcd_rgb.png)

```python
import cv2
img = cv2.imread("../DATA/giraffes.jpg", 0)
ret, th1 = cv2.threshold(img, 127, 255, cv2.THRESH_BINARY)
plt.imshow(th1, cmap='gray')
```

Resultado:

![Calc](/images/lcd_thresh.png)

Dessa forma, conseguimos eliminar todas as cores que poderiam influenciar e temos os dígitos para serem reconhecidos.

Com o codigo abaixo, podemos simular todos os diferentes algoritimos simples que o OpenCV implementa.

```python
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
img = cv.imread('../DATA/lcd_calc.jpg',0)
ret,thresh1 = cv.threshold(img,127,255,cv.THRESH_BINARY)
ret,thresh2 = cv.threshold(img,127,255,cv.THRESH_BINARY_INV)
ret,thresh3 = cv.threshold(img,127,255,cv.THRESH_TRUNC)
ret,thresh4 = cv.threshold(img,127,255,cv.THRESH_TOZERO)
ret,thresh5 = cv.threshold(img,127,255,cv.THRESH_TOZERO_INV)
titles = ['Original Image','BINARY','BINARY_INV','TRUNC','TOZERO','TOZERO_INV']
images = [img, thresh1, thresh2, thresh3, thresh4, thresh5]
for i in range(6):
    plt.subplot(2,3,i+1),plt.imshow(images[i],'gray')
    plt.title(titles[i])
    plt.xticks([]),plt.yticks([])
plt.show()
```

![LCDThreshold](/images/lcd_demo.png)

Para os casos onde exista maior variação de iluminação ou ainda o threshold simples não resolver, existe o threshold adaptativo:

A assinatura do método é a seguinte:
cv.adaptiveThreshold(src, maxValue, adaptiveMethod, thresholdType, blockSize, C[, dst])

- src - array de origem (imagem)
- thresh - valor do limiar
- maxval - valor máximo
- type:
  - cv2.ADAPTIVE_THRESH_MEAN_C : valor limite é a média da área dos vizinhos.
  - cv2.ADAPTIVE_THRESH_GAUSSIAN_C : valor limite é a soma ponderada dos valores de vizinhança onde os pesos são uma janela gaussiana (tamanho do bloco x tamanho do bloco da posição x,y menos o valor C _(abaixo)_).
- blockSize - tamanho do bloco dos vizinhos
- C - É apenas uma constante que é subtraída da média ou da média ponderada calculada.

Exemplo:

```python
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
img = cv.imread('../DATA/lcd_calc.jpg',0)
th1 = cv.adaptiveThreshold(img,255,cv.ADAPTIVE_THRESH_GAUSSIAN_C,\
            cv.THRESH_BINARY,27,5)
plt.imgshow(th1,cmap='gray')
```

![SudokuThreshold](/images/lcd_adaptative.png)

O resultado fica bem melhor, né?

Documentação:
<https://docs.opencv.org/3.4.3/d7/d4d/tutorial_py_thresholding.html>
