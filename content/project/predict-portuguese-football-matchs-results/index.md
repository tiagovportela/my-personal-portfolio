---
title: Predict Portuguese Football matchs results
subtitle: In this project was build a dataset and a ML model to predicted the
  outcome of portuguese football matchs.
date: 2022-07-25T18:36:13.273Z
summary: >
  Este projecto tem como objectico prever o resultado da Liga Portuguesa de
  Futebol. Estando divido em varias fases.


  1. Criar um dataset com varias importantes para a previsao do resultado

  2. Limpar os dados para que possam ser consumidos pelo modelo de machine learning

  3. Encontrar o melhor modelo para o problema

  4. Verificar a qualidade do modelo

  5. Melhoramentos futuros
draft: false
featured: false
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---
## Project architecture

## 1. Buil dataset

Para criar o dataset adquado para o objectivo recolhi dados da web sobre os jogos, jogares e odds das principais casas de apostas e fundios num dataset

### 1.1 Scrape Data

#### 1.1.1 Players data

Um bom site com dados de jogadores de futebol é o [sofifa.com](https://sofifa.com).
Depois de examinar o site não encontrei nenhuma api com os dados de interesse, por isso usei scrapy, que é um framework the python para webscraping.
Apos o scrape fiquei com um dataset da seguinte forma:

![header sofifa raw data](sofifa_raw_data_header.png)

O dataset é composto por 77 colunas e 476 linhas, correspondento a 77 atributos de 476 jogadores.

#### 1.1.2 Portuguese League Games

Ao inspecionar o site oficial da liga portuguesa encontrei que ele contei uma api que retorna os dados do jogo.

```
"https://www.ligaportugal.pt/pt/liga/jogo/{league_edition}/1/{week}/{match_number}/resumo/true"
```

#### 1.1.3 Portuguese Leagues Games Odds

dsgdfgdgdfgdd

### 1.2 Clean data

asdasdasd sdfsdf

#### 1.2.1 Clean SOFIFA Players data

fssdfjjj fdsdf lkjsd

#### 1.2.2 Clean Portuguese League Games data

dsdssdf sddggdfg

#### 1.2.3 Clean Portuguese Leagues Games Odds data

asdasdas gdgdfgdf

### 1.3 Merge data

asdasda sdfsdfsdf
dsfsdf