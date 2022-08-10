---
title: Portuguese Political Sentiment
date: 2022-08-10T11:50:42.851Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
# Goal: Build a bot that measure the sentiment about political parties and leaders

In this project a bot for Twitter was developed. This bot is able to collect tweets with direct references to the parties and respective leader. After collect the data, a sentiment analysis was made and published the summary on twitter account.

### Data Collection

Os tweets foram recolhidos atrevez da API do twitter, usando o Tweepy que é um package Python para a API do Twitter.
Apenas foram consideradas tweets com referencias directas aos partidos e lideres.
É considerada uma referencia directa, qualquer tweet com uma menção à conta do partido ou lider ou com as seguintes palavras-chave.



* PS - *"O PS"* e " partido socialista"
* PSD - *" o PSD",* " o  PPD/PSD" e " o PPD"
* BE -  *" o BE"* e " bloco de esquerda"
* PCP *\- " o PCP"* e " partido comunista"
* PAN - " o PAN"
* IL *\- " o IL"*, " a IL" e " iniciativa liberal"
* LIVRE *\- " o livre"* e " partido livre"
* CH *\- " o CH"* e" partido chega"


Apenas foram considerados tweets publicados na Europa.