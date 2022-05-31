---
layout: post
title:  "Como instalar e configurar o Tensorflow/Keras com suporte para CPU e GPU no Windows"
date:   2022-05-24 00:00
category: blog
icon: www
keywords: tensorflow, cpu, gpu, deep learning, ciência de dados, machine learning
image: 2022-05-30-tensorflow_gpu/tf-gpu.png
preview: 0
---

## Introdução

Em um [artigo anterior](https://gallileugenesis.github.io/blog/2022/CPUvsGPU.html) vimos um visão geral sobre as CPUs e as GPUs. Nesse artigo você verá como instalar e configurar o Tensorflow/Keras com suporte para CPU e GPU no Windows.

O processo é simples, mas é preciso ficar atento com a compatibilidade de versões de todos os pacotes e softwares necessários. 

## 1º passo: baixar e instalar o Anacoda

A melhor opção para fazer esse processo é por meio do ambiente Anaconda. Você pode baixa-lo clincando no link a seguir:

- [Anaconda](https://www.anaconda.com/)

*Nota: Anaconda é uma plataforma de distribuição Python, de código aberto, e com uma série de ferramentas para o desenvilvimento de projetos em inteligencia artificial integradas*.

## 2º passo: abra o CMD.exe Prompt 

Feito isso, abra o *Anaconda Navigator*, vá até *CMD.exe Prompt* e clique em *Launch*, como mostrado abaixo.

<p center>
<img src = "https://github.com/gallileugenesis/gallileugenesis.github.io/blob/main/post-img/blog/2022-05-30-tensorflow_gpu/anaconda.png?raw=true" width="600">
</p>



## 3º passo: crie um ambiente Anaconda

Você deve garantir que o TensorFlow tenha a versão do Python compatível. A melhor maneira de fazer isso é criar um ambiente Anaconda. Cada ambiente que você cria pode ter sua própria versão Python, de drivers e bibliotecas Python. S

O comando a seguir cria um ambinete chamado tensorflow para a versão python 3.9. Você pode nomea-lo como quiser. 

> conda create --name tensorflow python=3.9

Para entrar neste ambiente, você deve usar o seguinte comando:

> conda activate tensorflow

Vamos agora adicionar suporte ao Jupyter ao seu novo ambiente.

> conda install -c conda-forge nb_conda

## 4º passo: instale o TensorFlow para GPU e CPU

O comando a seguir instala o TensorFlow para suporte a GPU. Todas as instalações de driver complexas devem ser tratadas por este comando.

> conda install -c anaconda tensorflow-gpu

## 5º passo: registre seu ambiente

O comando a seguir registra seu ambiente tensorflow. Novamente, certifique-se de "conda ativar" seu novo ambiente tensorflow.

> python -m ipykernel install --user --name tensorflow --display-name "Python 3.9 (tensorflow)"

## 6º passo: teste seu ambiente

Agora você pode iniciar o notebook Jupyter. Use o seguinte comando.

> jupyter notebook

Em seguda, copie o seguinte código em uma das célulos do jupyter noteook


```python
import sys
import pip

# checa se o pandas e sklearn já estão instaladas e as instalam, caso não. 
Package = ['pandas', 'sklearn']
for i in Package:
    if i not in sys.modules:
        pip.main(['install', i])

import tensorflow.keras
import pandas as pd
import sklearn as sk
import tensorflow as tf

print(f"Versão Tensorflow: {tf.__version__}")
print(f"Versão Keras: {tensorflow.keras.__version__}")
print()
print(f"Versão Python {sys.version}")
print(f"Versão Pandas {pd.__version__}")
print(f"Versão Scikit-Learn {sk.__version__}")
gpu = len(tf.config.list_physical_devices('GPU'))>0
print("GPU está", "disponível" if gpu else "Não disponível")
```
Muito obrigado por ler esse artigo. 

Caso tenha interesse, você pode me encontrar no [GitHub](https://github.com/gallileugenesis) e [Linkedin](https://www.linkedin.com/in/gallileugenesis/).