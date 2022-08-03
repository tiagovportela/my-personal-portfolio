---
title: Predict Portuguese Football matchs results  2
subtitle: In this project was build a dataset and a ML model to predicted the
  outcome of portuguese football matchs.
date: 2022-07-28T11:04:23.619Z
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
### Goal: Predict Portuguese Football League Match Results.

### Roadmap

1. Data Mining
  
2. Data Cleaning
  
3. Data Exploration
  
4. Feature Engineering
  
5. Preditive Modeling
  

### 1. Data mining

For met the project goal, i need a dataset with data from matches, player in match, and odds.

#### 1.1 Matchs Data

The web is full with data from footbal games, but only for the top leagues. So i do a research and find that portuguese league [official website](https://ligaportugal.pt) have all games data from 2017 until now. After more research i discover a hidden endopoint that return a resume for league game.

```textile
/pt/liga/jogo/{league_edition}/1/{match_week}/{match}/resumo/true
```

With that i buil a simple program that collect data from all leagues from 2017 untill 2022 and save it to a CSV file. Because the response from endpoint is huge i choose the following features:

- Game Date
  
- Game Hour
  
- Home Team
  
- Away Team
  
- Home Team Score
  
- Away Team Score
  
- Home Team Formation
  
- Away Team Formation
  
- Lineups Players
  
- Referee
  
- Assistants
  
- Home Team Penalties
  
- Away Team Penalties
  
- Game stats like faul, shots, red and yellow cards, ball possetion and courners
  

#### 1.2 Players data.

A good site with football player data is [https://sofifa.com](https://sofifa.com). After looking through the site I didn't find any api with the data of interest, so I used scrapy, which is the python framework for webscraping. After collect data for the years between 2017 and 2021, I had a dataset as follows:

#### 1.3 Odds Data

This is the easiest data to find. The https://www.football-data.co.uk/ had CSV for all portuguese league seasons that i need, i juts have to download it.

### 2. Data Cleaning.

#### 2.1 Match Data.

First i drop the columns with 80% ou more of missing values. Depois disso quei com

as seguintes colunas com missing values:

| Column Name | Percentage Missing Values |
| --- | --- |
| Home team Formation | 0.05 |
| Away team Formation | 0.05 |
| home Player 1 - 11 | 0.05 |
| away Player 1 - 11 | 0.05 |

As colunas Home Team Formation e Away Team Formation irei preencher com o valor da moda em Casa e Fora de cado uma das equipas

As colunas com o nome dos jogadores do 11 inicial, com outra chamada ao endpoint mas para outro campo que tambem contem esta informação.

### 2.2 Players Data.

Cada jogador presente no dataset tem um conjunto de 77 atributos.
Destas apenas 13 tem valores nao numericos (tabela em baixo).


| Name                                   | Wage   | Value   | Best Positions   | Weight   | Height   | Age    | Preferred Foot   | Work Rate      | Body Type      | Joined       | Contract Valid Until   | Traits                                               |
|:---------------------------------------|:-------|:--------|:-----------------|:---------|:---------|:-------|:-----------------|:---------------|:---------------|:-------------|:-----------------------|:-----------------------------------------------------|
| Jonas Gonçalves Oliveira               | €30K   | €19.5M  | ST               | 74kg     | 182cm    | 33y.o. | Right            | High/ Medium   | Lean (170-185) | Sep 12, 2014 | 2020                   | ['Diver', 'Finesse Shot', 'Technical Dribbler (AI)'] |
| Romain Jules Salin                     | €10K   | €2.3M   | GK               | 76kg     | 189cm    | 32y.o. | Left             | Medium/ Medium | Lean (185+)    | Jul 29, 2017 | 2019                   | []                                                   |
| Domingos Sousa Coutinho Meneses Duarte | €6K    | €3.9M   | CB               | 78kg     | 190cm    | 22y.o. | Right            | Medium/ Medium | Lean (185+)    | Sporting CP  | Jun 30, 2018           | []                                                   |
| António Filipe Norinho de Carvalho     | €6K    | €1.8M   | GK               | 79kg     | 186cm    | 32y.o. | Right            | Medium/ Medium | Lean (185+)    | Jul 1, 2015  | 2019                   | ['Comes For Crosses']                                |
| Ewerton da Silva Pereira               | €5K    | €1.1M   | CDM CM           | 69kg     | 179cm    | 24y.o. | Right            | Medium/ Medium | Lean (170-185) | Aug 11, 2014 | 2021                   | []  

Assim porcedi à remoção das unidades em cada uma destas colunas.

| Name                                   |   Wage |    Value |   Weight |   Height |   Age | Preferred Foot   | Work Rate      | Body Type      |   Joined |   Contract Valid Until |
|:---------------------------------------|-------:|---------:|---------:|---------:|------:|:-----------------|:---------------|:---------------|---------:|-----------------------:|
| Jonas Gonçalves Oliveira               |  30000 | 1.95e+07 |       74 |      182 |    33 | Right            | High/ Medium   | Lean (170-185) |     2014 |                   2020 |
| Romain Jules Salin                     |  10000 | 2.3e+06  |       76 |      189 |    32 | Left             | Medium/ Medium | Lean (185+)    |     2017 |                   2019 |
| Domingos Sousa Coutinho Meneses Duarte |   6000 | 3.9e+06  |       78 |      190 |    22 | Right            | Medium/ Medium | Lean (185+)    |      nan |                   2018 |
| António Filipe Norinho de Carvalho     |   6000 | 1.8e+06  |       79 |      186 |    32 | Right            | Medium/ Medium | Lean (185+)    |     2015 |                   2019 |
| Ewerton da Silva Pereira               |   5000 | 1.1e+06  |       69 |      179 |    24 | Right            | Medium/ Medium | Lean (170-185) |     2014 |                   2021 |

