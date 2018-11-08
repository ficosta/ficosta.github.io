---
layout: post
title: Lendo e exibindo imagens com OpenCV
comments: true
categories: [OpenCV, ComputerVision]
tags: [OpenCV, imshow, imread]
---

Esse é o primeiro post de uma série sobre OpenCV, matplotlib e numpy, nele você vai aprender a ler e exibir corretamente uma imagem.

Funções abordadas: cv2.imread() e cv2.imshow()

## Lendo imagens com OpenCV

A função utilizada para ler imagens com o OpenCV é a `imread()`.

A função espera o argumento do caminho e opcionamente o modo de leitura dos canais.

`cv2.imread(filename[, flags])`

**Atenção** ao caminho das imagens, uma vez que a função **não** irá retornar um erro caso a imagem não esteja disponível!

A função retorna um objeto _numpy.ndarray_ caso consiga carregar corretamente uma imagem e _None_ em caso de falha.

O retorno dos canais da imagem será sempre _BGR_ Blue, Green, Red. É preciso utilizar `cvtColor()` para converter em RGB.

##### Flags

Opcionamente você pode utilizar:

- cv2.IMREAD_COLOR : Carrega apenas os canais de cor da imagem. O canal de alpha é ignorado. Esse é o valor padrão.
- cv2.IMREAD_GRAYSCALE : Carrega a imagem em escala de cinza.
- cv2.IMREAD_UNCHANGED : Carrega a imagem e o canal de alpha.

No lugar das flags, você pode utilizar _1, 0 ou -1_ respectivamente.

Exemplo:

```python
import numpy as np
import cv2

# Carrega a imagem em escala de cinza
img = cv2.imread('messi5.jpg',0)
```

## Exibindo imagens com OpenCV

Para exibir imagens com OpenCV utilize imshow(). A janela é ajustada automaticamente para o tamanho da imagem.

A função recebe dois argumentos, o nome da janela e a imagem a ser exibida. Você pode criar inumeras janelas porém, os nomes devem ser diferentes.

```python
cv2.imshow('image',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

![imshow PrintScreen](/images/opencv_imshow_screenshot.jpg)

`waitKey(0)` irá aguardar por uma tecla a ser pressionada, posteriormente `destroyAllWindows()` irá fechar a janela.

Em um outro post falaremos mais sobre essas 2 funções e em um post futuro, também iremos abordar como utilizar a biblioteca Matplotlib para exibir imagens com controles adicionais. Até lá!
