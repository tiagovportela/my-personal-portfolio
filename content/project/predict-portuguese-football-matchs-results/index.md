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

#### 1.1.1 Scrape Players data

Um bom site com dados de jogadores de futebol é o [sofifa.com](https://sofifa.com).
Depois de examinar o site não encontrei nenhuma api com os dados de interesse, por isso usei scrapy, que é um framework the python para webscraping.
Apos o scrape fiquei com um dataset da seguinte forma:

|    | Name                                   | Wage   | Value   |   Overall Rating | Best Positions   | Weight   | Height   | Age    | Preferred Foot   |   Weak Foot |   Skill Moves |   International Reputation | Work Rate      | Body Type      | Joined       | Contract Valid Until   |   Crossing |   Finishing |   Heading Accuracy |   Short Passing |   Volleys |   Dribbling |   Curve |   FK Accuracy |   Long Passing |   Ball Control |   Acceleration |   Sprint Speed |   Agility |   Reactions |   Balance |   Shot Power |   Jumping |   Stamina |   Strength |   Long Shots |   Aggression |   Interceptions |   Positioning |   Vision |   Penalties |   Marking |   Standing Tackle |   Sliding Tackle |   GK Diving |   GK Handling |   GK Kicking |   GK Positioning |   GK Reflexes | Traits                                               |   LS |   ST |   RS |   LW |   LF |   CF |   RF |   RW |   LAM |   CAM |   RAM |   LM |   LCM |   CM |   RCM |   RM |   LWB |   LDM |   CDM |   RDM |   RWB |   LB |   LCB |   CB |   RCB |   RB |   GK |
|---:|:---------------------------------------|:-------|:--------|-----------------:|:-----------------|:---------|:---------|:-------|:-----------------|------------:|--------------:|---------------------------:|:---------------|:---------------|:-------------|:-----------------------|-----------:|------------:|-------------------:|----------------:|----------:|------------:|--------:|--------------:|---------------:|---------------:|---------------:|---------------:|----------:|------------:|----------:|-------------:|----------:|----------:|-----------:|-------------:|-------------:|----------------:|--------------:|---------:|------------:|----------:|------------------:|-----------------:|------------:|--------------:|-------------:|-----------------:|--------------:|:-----------------------------------------------------|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|------:|------:|------:|-----:|------:|-----:|------:|-----:|------:|------:|------:|------:|------:|-----:|------:|-----:|------:|-----:|-----:|
|  0 | Jonas Gonçalves Oliveira               | €30K   | €19.5M  |               84 | ST               | 74kg     | 182cm    | 33y.o. | Right            |           5 |             3 |                          3 | High/ Medium   | Lean (170-185) | Sep 12, 2014 | 2020                   |         70 |          88 |                 84 |              75 |        85 |          84 |      85 |            77 |             70 |             89 |             66 |             65 |        77 |          85 |        69 |           84 |        69 |        74 |         61 |           85 |           61 |              34 |            87 |       83 |          84 |        23 |                36 |               25 |          12 |            11 |            7 |                8 |             5 | ['Diver', 'Finesse Shot', 'Technical Dribbler (AI)'] |   84 |   84 |   84 |   82 |   84 |   84 |   84 |   82 |    84 |    84 |    84 |   81 |    78 |   78 |    78 |   81 |    60 |    60 |    60 |    60 |    60 |   57 |    52 |   52 |    52 |   57 |   19 |
|  1 | Romain Jules Salin                     | €10K   | €2.3M   |               73 | GK               | 76kg     | 189cm    | 32y.o. | Left             |           2 |             1 |                          1 | Medium/ Medium | Lean (185+)    | Jul 29, 2017 | 2019                   |         11 |          11 |                 16 |              36 |        13 |          14 |      11 |            15 |             23 |             13 |             28 |             34 |        53 |          77 |        45 |           23 |        70 |        38 |         67 |           13 |           45 |              26 |            16 |       58 |          11 |        11 |                13 |               16 |          73 |            69 |           65 |               71 |            73 | []                                                   |   26 |   26 |   26 |   26 |   27 |   27 |   27 |   26 |    32 |    32 |    32 |   28 |    33 |   33 |    33 |   28 |    27 |    32 |    32 |    32 |    27 |   27 |    30 |   30 |    30 |   27 |   73 |
|  2 | Domingos Sousa Coutinho Meneses Duarte | €6K    | €3.9M   |               72 | CB               | 78kg     | 190cm    | 22y.o. | Right            |           3 |             2 |                          1 | Medium/ Medium | Lean (185+)    | Sporting CP  | Jun 30, 2018           |         34 |          30 |                 74 |              56 |        27 |          48 |      27 |            27 |             44 |             55 |             60 |             49 |        44 |          66 |        50 |           50 |        69 |        73 |         79 |           31 |           81 |              72 |            31 |       30 |          45 |        69 |                77 |               68 |           9 |             9 |           14 |               14 |            13 | []                                                   |   50 |   50 |   50 |   45 |   46 |   46 |   46 |   45 |    47 |    47 |    47 |   49 |    52 |   52 |    52 |   49 |    62 |    65 |    65 |    65 |    62 |   64 |    72 |   72 |    72 |   64 |   18 |
|  3 | António Filipe Norinho de Carvalho     | €6K    | €1.8M   |               72 | GK               | 79kg     | 186cm    | 32y.o. | Right            |           2 |             1 |                          1 | Medium/ Medium | Lean (185+)    | Jul 1, 2015  | 2019                   |         13 |          11 |                 15 |              15 |        14 |          11 |      14 |            14 |             16 |             13 |             36 |             31 |        43 |          63 |        31 |           20 |        69 |        33 |         65 |           14 |           29 |              18 |            11 |       69 |          12 |        11 |                13 |               11 |          72 |            72 |           65 |               71 |            73 | ['Comes For Crosses']                                |   23 |   23 |   23 |   23 |   24 |   24 |   24 |   23 |    28 |    28 |    28 |   25 |    27 |   27 |    27 |   25 |    22 |    25 |    25 |    25 |    22 |   22 |    25 |   25 |    25 |   22 |   72 |
|  4 | Ewerton da Silva Pereira               | €5K    | €1.1M   |               69 | CDM CM           | 69kg     | 179cm    | 24y.o. | Right            |           3 |             3 |                          1 | Medium/ Medium | Lean (170-185) | Aug 11, 2014 | 2021                   |         54 |          43 |                 58 |              71 |        42 |          57 |      57 |            41 |             67 |             69 |             61 |             60 |        64 |          65 |        69 |           62 |        82 |        73 |         68 |           53 |           73 |              67 |            48 |       59 |          52 |        67 |                67 |               61 |           9 |             9 |           11 |                8 |             9 | []                                                   |   58 |   58 |   58 |   59 |   59 |   59 |   59 |   59 |    62 |    62 |    62 |   62 |    65 |   65 |    65 |   62 |    66 |    69 |    69 |    69 |    66 |   66 |    68 |   68 |    68 |   66 |   16 |

#### 1.1.2 Scrape Portuguese League Games

asasassd

#### 1.1.3 Scrape Portuguese Leagues Games Odds

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