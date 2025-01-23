# Atividade Prática: Manipulação de Imagens com Python

## Objetivo
Nesta atividade, você irá aprender a realizar operações básicas de manipulação de imagens utilizando a biblioteca Pillow em Python, incluindo redimensionamento, rotação, aplicação de filtros e salvamento de imagens.

## Pré-requisitos
* Python 3.x instalado
* Biblioteca Pillow instalada (`pip install Pillow`)
* Uma imagem de sua escolha para teste

## Parte 1: Configuração Inicial

Primeiro, vamos importar as bibliotecas necessárias e carregar uma imagem:

```python
from PIL import Image, ImageEnhance, ImageFilter

# Carregando a imagem
imagem = Image.open('sua_imagem.jpg')

# Exibindo informações básicas da imagem
print(f"Formato: {imagem.format}")
print(f"Tamanho: {imagem.size}")
print(f"Modo: {imagem.mode}")
```

## Parte 2: Exercícios Práticos

### Exercício 1: Redimensionamento
Crie uma função que redimensione a imagem para 50% do seu tamanho original:

```python
def redimensionar_imagem(imagem, fator=0.5):
    novo_tamanho = (int(imagem.size[0] * fator), int(imagem.size[1] * fator))
    imagem_redimensionada = imagem.resize(novo_tamanho)
    return imagem_redimensionada

# Teste sua função
imagem_pequena = redimensionar_imagem(imagem)
imagem_pequena.save('imagem_redimensionada.jpg')
```

### Exercício 2: Rotação e Espelhamento
Experimente diferentes transformações geométricas:

```python
def transformar_imagem(imagem):
    # Rotação de 45 graus
    rotacionada = imagem.rotate(45, expand=True)
    
    # Espelhamento horizontal
    espelhada = imagem.transpose(Image.FLIP_LEFT_RIGHT)
    
    return rotacionada, espelhada

# Teste as transformações
rotacionada, espelhada = transformar_imagem(imagem)
rotacionada.save('imagem_rotacionada.jpg')
espelhada.save('imagem_espelhada.jpg')
```

### Exercício 3: Aplicação de Filtros
Crie uma função que aplique diferentes filtros à imagem:

```python
def aplicar_filtros(imagem):
    # Aumentar nitidez
    nitidez = imagem.filter(ImageFilter.SHARPEN)
    
    # Aplicar desfoque
    desfoque = imagem.filter(ImageFilter.BLUR)
    
    # Encontrar bordas
    bordas = imagem.filter(ImageFilter.FIND_EDGES)
    
    return nitidez, desfoque, bordas

# Teste os filtros
nitidez, desfoque, bordas = aplicar_filtros(imagem)
nitidez.save('imagem_nitida.jpg')
desfoque.save('imagem_desfocada.jpg')
bordas.save('imagem_bordas.jpg')
```

## Desafio Final

Combine todas as técnicas aprendidas para criar uma função que:
1. Redimensione a imagem para 75% do tamanho original
2. Rotacione em 30 graus
3. Aplique um filtro de sua escolha
4. Ajuste o brilho e contraste

```python
def processamento_completo(imagem):
    # Redimensionamento
    img_redimensionada = redimensionar_imagem(imagem, 0.75)
    
    # Rotação
    img_rotacionada = img_redimensionada.rotate(30, expand=True)
    
    # Filtro de nitidez
    img_filtrada = img_rotacionada.filter(ImageFilter.SHARPEN)
    
    # Ajuste de brilho e contraste
    enhancer = ImageEnhance.Brightness(img_filtrada)
    img_brilho = enhancer.enhance(1.2)  # Aumenta o brilho em 20%
    
    enhancer = ImageEnhance.Contrast(img_brilho)
    img_final = enhancer.enhance(1.3)  # Aumenta o contraste em 30%
    
    return img_final

# Teste o processamento completo
imagem_final = processamento_completo(imagem)
imagem_final.save('imagem_processada.jpg')
```

## Avaliação
Você será avaliado nos seguintes critérios:
1. Implementação correta das funções solicitadas
2. Qualidade e organização do código
3. Capacidade de combinar diferentes técnicas de processamento
4. Documentação e comentários no código
5. Criatividade no desafio final

## Entrega
* Código Python com todas as funções implementadas
* Imagens originais e processadas
* Um breve relatório explicando suas escolhas de processamento e os resultados obtidos

## Dicas
* Sempre verifique o formato e modo de cor da imagem antes de processá-la
* Faça backup das imagens originais antes de começar o processamento
* Experimente diferentes valores nos parâmetros das funções para entender seu impacto
* Use try/except para lidar com possíveis erros durante o processamento

---
**Autor**: [GUilherme Tavares]  
**Data**: [23/02/2025]  
**Versão**: 1.0