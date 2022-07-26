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

Ao inspecionar o site oficial da liga portuguesa encontrei um endpoint que retorna os dados do jogo.

```
"https://www.ligaportugal.pt/pt/liga/jogo/{league_edition}/1/{week}/{match_number}/resumo/true"
```

Assim construi um dataset com os dados de todos os jogos da liga.

![portuguese league data](ligapt_raw_data_header.png)

|    | name                   | type    |   null |   unique |
|---:|:-----------------------|:--------|-------:|---------:|
|  0 | Date                   | object  |      0 |      131 |
|  1 | Hour                   | object  |      0 |       13 |
|  2 | Home team              | object  |      0 |       18 |
|  3 | Away team              | object  |      0 |       18 |
|  4 | Home team score        | int64   |      0 |        7 |
|  5 | Away team score        | int64   |      0 |        7 |
|  6 | Home team Formation    | float64 |     15 |        5 |
|  7 | Away team Formation    | float64 |     15 |        6 |
|  8 | Home_Remates           | int64   |      0 |       25 |
|  9 | Away_Remates           | int64   |      0 |       24 |
| 10 | Home_Posse de Bola     | int64   |      0 |       41 |
| 11 | Away_Posse de Bola     | int64   |      0 |       41 |
| 12 | Home_Faltas Cometidas  | int64   |      0 |       24 |
| 13 | Away_Faltas Cometidas  | int64   |      0 |       24 |
| 14 | Home_Cantos            | int64   |      0 |       16 |
| 15 | Away_Cantos            | int64   |      0 |       17 |
| 16 | Home_Cartões Amarelos  | int64   |      0 |        8 |
| 17 | Away_Cartões Amarelos  | int64   |      0 |        8 |
| 18 | Home_Cartões Vermelhos | int64   |      0 |        3 |
| 19 | Away_Cartões Vermelhos | int64   |      0 |        3 |
| 20 | home Player 1          | object  |     15 |      197 |
| 21 | home Player 2          | object  |     15 |      203 |
| 22 | home Player 3          | object  |     15 |      198 |
| 23 | home Player 4          | object  |     15 |      199 |
| 24 | home Player 5          | object  |     15 |      200 |
| 25 | home Player 6          | object  |     15 |      190 |
| 26 | home Player 7          | object  |     15 |      200 |
| 27 | home Player 8          | object  |     15 |      201 |
| 28 | home Player 9          | object  |     15 |      211 |
| 29 | home Player 10         | object  |     15 |      200 |
| 30 | home Player 11         | object  |     15 |      207 |
| 31 | away Player 1          | object  |     15 |      208 |
| 32 | away Player 2          | object  |     15 |      194 |
| 33 | away Player 3          | object  |     15 |      202 |
| 34 | away Player 4          | object  |     15 |      197 |
| 35 | away Player 5          | object  |     15 |      195 |
| 36 | away Player 6          | object  |     15 |      213 |
| 37 | away Player 7          | object  |     15 |      212 |
| 38 | away Player 8          | object  |     15 |      201 |
| 39 | away Player 9          | object  |     15 |      195 |
| 40 | away Player 10         | object  |     15 |      188 |
| 41 | away Player 11         | object  |     15 |      200 |
| 42 | url                    | object  |      0 |      306 |
| 43 | Referee                | object  |      0 |       22 |
| 44 | 1 Assistant            | object  |      0 |       38 |
| 45 | 2 Assistant            | object  |      0 |       39 |
| 46 | 3 Assistant            | object  |      0 |       84 |
| 47 | Home Penalties         | float64 |    306 |        0 |
| 48 | Away Penalties         | float64 |    306 |        0 |

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