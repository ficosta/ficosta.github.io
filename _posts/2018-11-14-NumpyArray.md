---
layout: post
title: NumPy Array
comments: true
categories: [NumPy]
tags: [NumPy, Array]
---

Ultimamente tenho estudado bastante as bibliotecas para ciência de dados e hoje eu vou falar sobre a bibliote NumPy. Ela é muito importante para trabalhar de forma eficiente com matrizes e vetores.

## Array NumPy

Para trabalhar com a biblioteca NumPy primeiramente é preciso importar com:

```python
import numpy as np
```

Logo todas as vezes que utizarmos a biblioteca, chamaremos os métodos com np.nomeMétodo().

#### Iniciando um Array

Os arrays podem ser inicializados de diversas formas.

Array 2D vazio:

```python
np.zeros(5)
```

    array([0., 0., 0., 0., 0.])

Array 2D com 1's:

```python
np.ones(5)
```

    array([1., 1., 1.])

Manualmente utilizando uma lista:

```python
my_list = [1,2,3]
array = np.array(my_list)
```

    array([1, 2, 3])

Gerando números como arange do python:

```python
np.arange(10)
```

    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

Delimitando o inicio, o final e o passo:

```python
np.arange(2,20,2)
```

    array([ 2,  4,  6,  8, 10, 12, 14, 16, 18])

Gerando o a quantidade de valores dentro de um intervalo:

```python
#Gerando 7 valores no intervalo de 1 a 10
np.linspace(1,10,7)
```

    array([ 1. ,  2.5,  4. ,  5.5,  7. ,  8.5, 10. ])

Gerando um array 2d com uma diagonal com 1's:

```python
#Array de 250 x 250 com uma lina na diagonal
np.eye(250)
```

    array([[1., 0., 0., ..., 0., 0., 0.],
           [0., 1., 0., ..., 0., 0., 0.],
           [0., 0., 1., ..., 0., 0., 0.],
           ...,
           [0., 0., 0., ..., 1., 0., 0.],
           [0., 0., 0., ..., 0., 1., 0.],
           [0., 0., 0., ..., 0., 0., 1.]])

![Plot](/images/numpy/eye_250.png)

Array (2,2) com números randômicos:

```python
np.random.rand(2,2)
```

    array([[0.90139809, 0.21695395],
           [0.76259878, 0.69440245]])

Randômicos inteiros:

```python
#Dez números de 0 a 50
ranarr = np.random.randint(0,50,10)
```

    array([48, 35, 36, 18, 47,  1, 38, 18, 18, 31])

Reorganizando um vetor para uma matriz:

```python
array = np.rand(15)
#valores: array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14])
array = array.reshape(5,3)
```

    array([[ 0,  1,  2],
           [ 3,  4,  5],
           [ 6,  7,  8],
           [ 9, 10, 11],
           [12, 13, 14]])

Bom, acredito que foi abordado uma grande forma de inicializar um array 2d e uma matriz. Ainda existem outras formas e algumas das funções podem ter seus parâmetros alterados para gerar outros dados.

Veja mais em:
[Documentação NumPy](https://docs.scipy.org/doc/numpy-1.11.0/numpy-ref-1.11.0.pdf)
