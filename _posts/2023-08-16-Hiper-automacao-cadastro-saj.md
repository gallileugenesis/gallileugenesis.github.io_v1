---
layout: post
title:  "Cadastro automático de processos no SAJ"
date:   2023-08-16 00:00
category: projetos
icon: www
keywords: projetos, hiper-automação, sistemas especialistas, automação 
image: 2023-08-16-Hiper-automacao-cadastro-saj\1-Hiper-automação.png
preview: 0
---



Este projeto teve como objetivo automatizar o processo de cadastro de processos no [SAJ](https://www.softplan.com.br/produto/saj-tribunais/). O cadastro dos processos é realizado mediante o preenchimento automático de campos predeterminados, com valores conhecidos e campos cujas informações necessitam ser extraídas de documentos específicos. Além disso, os referidos documentos tem que ser anexos ao sistema para completar o cadastro.

A identificação dos documentos foi um desafio, uma vez que não havia dados rotulados para treinar um modelo de classificação supervisionado. A solução foi desenvolver um sistema especialista, baseado em regras. Basicamente, o sistem é suportado por diversas ferramentas de processamento de linguagem natural e um conjunto de regras composto por palavras-chaves e seus respectivos pesos, os quais podem ser negativos ou positivos.   

Já a automação do cadastro foi realizada com o [UiPath](https://www.uipath.com/).
