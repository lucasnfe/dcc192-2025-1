---
layout: page
title:  PF1 - Game Design Document
permalink: /avaliacoes/pf1-gdd
nav_exclude: true
---

# PF1: Game Design Document

#### Entrega: 30/04 às 23:59h

## Introdução

Projetos de jogos profissionais geralmente começam com uma ideia, que antes de ser implementada, passa por uma etapa de validação inicial. Essa etapa geralmente envolve a criação de um documento de design para comunicar a equipe de dessenvolvimento e a potenciais investidores todos os detalhes importantes do projeto. 

## Objetivo

Para o projeto final da disciplina, você irá desenvolver um pequeno jogo completo (início, meio e fim) com todos os principais ciclos de um projeto profissional. O objetivo principal é possibilitar uma vivência completa da produção de jogos, desde a concepção da ideia até a entrega. Implementar e entregar um jogo completo é uma tarefa difícil, pois é muito comum a ideia inicial passar por várias mudanças ao longo do desenvolvimento. Por isso, produzir jogos completos, mesmo que pequenos, é uma experiência fundamental para quem quer se tornar um profissional da área.

## Instruções

O seu jogo deve ser desenvovlido em C++/SDL em um grupo de no máximo 3 pessoas e deve conter: (1) menu inicial, (2) início e fim bem definidos, (3) sistema de progressão básica (dificuldade, narrativa, etc) e (4) interface para reiniciar o jogo quando ele terminar. Nessa primeira etapa, você irá escrever um Documento de Design de Jogo, do inglês, Game Design Document (GDD), para formalizar suas ideias de projeto. Seu GDD deve conter as seguinte seções escritas respeitando um limite de 6 a 10 páginas (1 coluna, espaçamento simples, margem 2.5cm): 

1. **Título e Autores** 

    Apresente o título do projeto e o nome dos membros do grupo.

2. **Declaração Artística** 

    Essa é uma seção de introdução onde você como designer apresenta suas motivações e objetivos com o
    jogo que planeja criar. Para escrever essa seção, faça as seguintes perguntas a si mesmo:

    - Por que você está criando este jogo? 
    - Que ideias você está explorando? 
    - Que tipo de resposta emocional você está procurando? 
    - Este jogo está sendo criado em reação a outros jogos?

3. **Gameplay** 

    Essa é a seção mais importante do documento. Ela detalha a experiência que você espera que o jogador tenha ao jogar o seu jogo.
    Para escrever essa seção, faça as seguintes pergutas a si mesmo:

    - Qual a narrativa do jogo (e.g., história, mundo, personagens, etc)?
    - Quais são as mecânicas básicas do jogo (e.g., correr, pular, atirar, etc)?
    - Qual o objetivo do jogador? 
    - Como o jogo começa e termina?
    - Qual o sistema de progressão do jogo (e.g., narrativa, dificuldade, níveis, missões, etc)?
    - Quais habilidades o jogador deve aprimorar durante a progressão do jogo (e.g., controle do personagem, resolução de quebra-cabeças, memória, estratégias, gerenciamento de recursos, etc)?
    - Qual o esquema de controles? 
    - Quantos jogadores são necessários?

4. **Arte**
    
    Essa seção descreve o estilo de arte que você pretende utilizar para criar os gráficos do seu jogo. Por exemplo, esse é um jogo 2D isométrico com sprites de alta resolução simulando um estilo de pixel art antigo. Utilize imagens como referência para comunicar visualmente o estilo que pretende utilizar. 
    
    Como esse projeto está sendo desenvolvido no contexto de uma disciplina de programação de jogos, e não de arte, não é esperado que você tenha habilidades artística para a produção própria das imagens do seu jogo. Por isso, fique à vontade para utilizar imagens públicas. No entanto, se você tem interesse em começar a desenvolver suas próprias imagens, considere usar pixel art no seu jogo, pois esse é um estilo mais amigável para quem está começando. 

5. **Música e Efeitos Sonoros**

    Essa seção segue a mesma estrutura da anterior, porém para descrever o estilo de música e efeitos sonoros que pretende utilizar no seu jogo. Por exemplo, a música terá um estilo heavy metal melódico com instrumentos sintetizados por computador, como no [[Mega Man X]](https://www.youtube.com/watch?v=KDciDXnm3ek&ab_channel=NintendoComplete). Cada nível do jogo terá um tema diferente com melodias marcantes. Efeitos sonoros serão criados com sons metálicos para aumentar a ambientação do jogo com o universo da robótica.

6. **Tecnologias** 

    Essa seção descreve as tecnologias que você pretende utilizar durante o desenvolvimento e para quais plataformas você pretende publicar o jogo. Por exemplo, esse jogo será desenvolvido em C++ com a biblioteca SDL para facilitar que o jogo seja distribuído para plataformas diferentes. A arte será produzida com o editor pixel art [[Aseprite]](https://www.aseprite.org/) e a música com o sequenciador midi do [[FL Studio]](https://www.image-line.com/). O jogo será publicado para os sistemas operacionais Windows, Mac e Linux.

7. **Marketing** 

    Essa seção descreve a estratégia de marketing que pretende desenvolver para divulgar o seu jogo e criar uma base de fans/jogadores. Como o seu jogo será desenvolvido em um contexto acadêmico, uma campanha de marketing está fora do escopo do projeto final. No entanto, para a disciplina, utilize essa seção para delinear a audiência do seu jogo. Por exemplo, a audiência desse jogo são jogadores experientes de jogos de plataforma e *run & gun*.

8. **Cronograma** 

    Esse seção deve conter uma tabela com as atividades que irá realizar para produzir o jogo e suas respectivas datas previstas de início e fim.

Como os projetos podem ter escopos muito distintos, o seu GDD não precisa necessariamente responder todas as perguntas listadas em cada seção ou seguir exatamente os exemplos que foram dados. O importante é que ele deixe claro qual o objetivo do seu jogo, como ele será jogado, qual a estética visual e sonora, como ele será desenvolvido, qual a sua audiência, para que plataforma será publicado e quanto tempo levará para ficar pronto.

## Submissão

Envie o seu GDD em formato pdf na tarefa `PF1: Documento de Design` do Moodle. **Apenas um membro do grupo precisa fazer a submissão**. 

## Barema

- Formatação: seu documento satisfaz os requerimentos de formato (15%)
- Completude: o documento contém todas as seções especificadas (50%)
- Qualidade: o texto comunica com clareza a ideia do jogo (30%)
- Viabilidade: a proposta é factível dentro do contexto da disciplina (15%)

## Referências

- [[Game Design Documents]](https://gamescrye.com/resources/game-design-documents/), Gamescrye

    Lista com GDDs de jogos famosos.

- [[How to Write a Game Design Document]](https://www.gamedeveloper.com/business/how-to-write-a-game-design-document), Game Developer

    Artigo do Game Developer (importante blog de game design) sobre como escrever GDDs.

- [[Metronome], Game Design Document](https://docs.google.com/document/d/1DxZ-WHQBFgAAixxf6jnZL53yHn_4YlT5oWCjV7fXJJ4/edit?usp=sharing)

    Exemplo de GDD criado em um contexto acadêmico similar à INF721.
