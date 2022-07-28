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
### Goal:

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
/pt/liga/jogo/{league_edition}/league_id/{match_week}/{match}/resumo/true
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
  

The dataset have the following features:

| Column Name | Type | Unique | Null Values |
| --- | --- | --- | --- |
| Date | object | 131 | 0   |
| Hour | object | 13  | 0   |
| Home team | object | 18  | 0   |
| Away team | object | 18  | 0   |
| Home team score | int64 | 7   | 0   |
| Away team score | int64 | 7   | 0   |
| Home team Formation | int64 | 5   | 0   |
| Away team Formation | int64 | 6   | 0   |
| Home_Remates | int64 | 25  | 0   |
| Away_Remates | int64 | 24  | 0   |
| Home_Posse de Bola | int64 | 41  | 0   |
| Away_Posse de Bola | int64 | 41  | 0   |
| Home_Faltas Cometidas | int64 | 24  | 0   |
| Away_Faltas Cometidas | int64 | 24  | 0   |
| Home_Cantos | int64 | 16  | 0   |
| Away_Cantos | int64 | 17  | 0   |
| Home_Cartões Amarelos | int64 | 8   | 0   |
| Away_Cartões Amarelos | int64 | 8   | 0   |
| Home_Cartões Vermelhos | int64 | 3   | 0   |
| Away_Cartões Vermelhos | int64 | 3   | 0   |
| home Player 1 | object | 204 | 0   |
| home Player 2 | object | 208 | 1   |
| home Player 3 | object | 202 | 0   |
| home Player 4 | object | 208 | 0   |
| home Player 5 | object | 206 | 1   |
| home Player 6 | object | 197 | 0   |
| home Player 7 | object | 205 | 1   |
| home Player 8 | object | 208 | 0   |
| home Player 9 | object | 216 | 1   |
| home Player 10 | object | 203 | 1   |
| home Player 11 | object | 214 | 1   |
| away Player 1 | object | 216 | 0   |
| away Player 2 | object | 199 | 0   |
| away Player 3 | object | 208 | 0   |
| away Player 4 | object | 199 | 0   |
| away Player 5 | object | 201 | 0   |
| away Player 6 | object | 219 | 0   |
| away Player 7 | object | 218 | 0   |
| away Player 8 | object | 205 | 1   |
| away Player 9 | object | 200 | 0   |
| away Player 10 | object | 196 | 0   |
| away Player 11 | object | 208 | 0   |
| url | object | 306 | 0   |
| Referee | object | 22  | 0   |
| 1 Assistant | object | 38  | 0   |
| 2 Assistant | object | 39  | 0   |
| 3 Assistant | object | 84  | 0   |
| Home Penalties | float64 | 1   | 0   |
| Away Penalties | float64 | 1   | 0   |

#### 1.2 Players data.

A good site with football player data is [https://sofifa.com](https://sofifa.com). After looking through the site I didn't find any api with the data of interest, so I used scrapy, which is the python framework for webscraping. After collect data for the years between 2017 and 2021, I had a dataset as follows:

| Column Name | Type | Unique | Null Values |
| --- | --- | --- | --- |
| Name | object | 476 | 0   |
| Wage | object | 14  | 0   |
| Value | object | 106 | 0   |
| Overall Rating | int64 | 26  | 0   |
| Best Positions | object | 81  | 0   |
| Weight | object | 38  | 0   |
| Height | object | 35  | 0   |
| Age | object | 20  | 0   |
| Preferred Foot | object | 2   | 0   |
| Weak Foot | int64 | 5   | 0   |
| Skill Moves | int64 | 5   | 0   |
| International Reputation | int64 | 4   | 0   |
| Work Rate | object | 8   | 0   |
| Body Type | object | 9   | 0   |
| Joined | object | 167 | 0   |
| Contract Valid Until | object | 8   | 0   |
| Crossing | int64 | 74  | 0   |
| Finishing | int64 | 75  | 0   |
| Heading Accuracy | int64 | 68  | 0   |
| Short Passing | int64 | 62  | 0   |
| Volleys | int64 | 79  | 0   |
| Dribbling | int64 | 73  | 0   |
| Curve | int64 | 76  | 0   |
| FK Accuracy | int64 | 72  | 0   |
| Long Passing | int64 | 69  | 0   |
| Ball Control | int64 | 67  | 0   |
| Acceleration | int64 | 72  | 0   |
| Sprint Speed | int64 | 71  | 0   |
| Agility | int64 | 67  | 0   |
| Reactions | int64 | 38  | 0   |
| Balance | int64 | 69  | 0   |
| Shot Power | int64 | 73  | 0   |
| Jumping | int64 | 59  | 0   |
| Stamina | int64 | 72  | 0   |
| Strength | int64 | 62  | 0   |
| Long Shots | int64 | 80  | 0   |
| Aggression | int64 | 76  | 0   |
| Interceptions | int64 | 78  | 0   |
| Positioning | int64 | 80  | 0   |
| Vision | int64 | 65  | 0   |
| Penalties | int64 | 73  | 0   |
| Marking | int64 | 76  | 0   |
| Standing Tackle | int64 | 73  | 0   |
| Sliding Tackle | int64 | 72  | 0   |
| GK Diving | int64 | 38  | 0   |
| GK Handling | int64 | 34  | 0   |
| GK Kicking | int64 | 36  | 0   |
| GK Positioning | int64 | 36  | 0   |
| GK Reflexes | int64 | 39  | 0   |
| Traits | object | 136 | 0   |
| LS  | int64 | 57  | 0   |
| ST  | int64 | 57  | 0   |
| RS  | int64 | 57  | 0   |
| LW  | int64 | 66  | 0   |
| LF  | int64 | 62  | 0   |
| CF  | int64 | 62  | 0   |
| RF  | int64 | 62  | 0   |
| RW  | int64 | 66  | 0   |
| LAM | int64 | 61  | 0   |
| CAM | int64 | 61  | 0   |
| RAM | int64 | 61  | 0   |
| LM  | int64 | 61  | 0   |
| LCM | int64 | 58  | 0   |
| CM  | int64 | 58  | 0   |
| RCM | int64 | 58  | 0   |
| RM  | int64 | 61  | 0   |
| LWB | int64 | 58  | 0   |
| LDM | int64 | 58  | 0   |
| CDM | int64 | 58  | 0   |
| RDM | int64 | 58  | 0   |
| RWB | int64 | 58  | 0   |
| LB  | int64 | 60  | 0   |
| LCB | int64 | 62  | 0   |
| CB  | int64 | 62  | 0   |
| RCB | int64 | 62  | 0   |
| RB  | int64 | 60  | 0   |
| GK  | int64 | 34  | 0   |