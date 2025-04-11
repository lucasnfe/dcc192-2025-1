---
layout: page
title:  TP1 - Pong
permalink: /avaliacoes/tp1-pong
nav_exclude: true
---

# TP1: Pong

#### Entrega: 09/04/2025 às 18:59h

## Introdução

Um dos primeiros e mais populares jogos da era do fliperama é o Pong, desenvolvido pela Atari em 1972. O pong simula um jogo de tênis de mesa, onde cada jogador controla verticalmente uma raquete posicionada em uma das extremidades da tela, com o objetivo de rebater uma bola de tal maneira que o oponente não consiga rebater de volta. Cada vez que um jogador não conseguir rebater a bola, o oponente receberá um ponto. O jogo termina quando um dos jogadores completar 11 pontos. Tanto as raquetes e a bola quanto as marcações de meio de campo e de pontuação são representados por retângulos brancos. O video a seguir mostra um *gameplay* do jogo original:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/e4VRgY3tkh0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen="">
    </iframe>
</div>

## Objetivo

Nesse projeto, você irá desenvolver uma versão de 1 jogador do jogo Pong em C++ e SDL. Nessa versão, o jogador controla a raquete com o objetivo de rebater a bola contra a parede o maior número de vezes possível. Primeiro, você irá criar o laço principal do jogo (*game loop*) com uma taxa de quadros (*framerate*) dinâmica, que processa entradas do teclado, atualiza os objetos do jogo e renderiza os quadros. A modelagem de objetos terá uma arquitetura híbrida, com hierarquia de classes e componentes. Em seguida, você irá utilizar essa estrutura para definir os objetos de jogo do pong. O video a seguir mostra um gameplay da versão que você irá implementar:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/-mM9fSVLPlc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## Código-base

Siga as instruções abaixo para baixar o código-base desse trabalho prático:

1. Aceite o projeto *tp1-pong* no GitHub classroom [[nesse link]](https://classroom.github.com/a/VL3UwkYl)
2. Clone o seu novo repositório no seu computador:

    ```
    # Substitua <GITHUB_USERNAME> pelo seu usuário do GitHub
    git clone https://github.com/ufmg-dcc192/tp1-pong-<GITHUB_USERNAME>.git
    ```

3. Abra o projeto *tp1-pong* na CLion e, antes de começar a sua implementação, verique com cuidado as definições de métodos e atributos de cada classe:

    - **Game**

        Classe responsável por inicializar, gerenciar o laço principal e finalizar o jogo. 

    - **Actor**

        Classe base para todos os objetos do jogo, contendo atributos para transformação (translação, rotação e escala) e métodos para processamento de eventos
        de entrada, atualização e gerenciamento de componentes. 

    - **Component**

        Classe base para todos os componentes do jogo, contendo métodos para processamento de eventos de entrada e atualização. 

    - **DrawComponent**

        Componente de desenho de objetos com retângulos coloridos. 

    - **Ball**

        Classe que estende Actor para representar a bola do jogo Pong.
        
    - **Paddle**

        Classe que estende Actor para representar a raquete do jogo Pong.

    - **Math**

        Classes e funções implementando todas as operações matemáticas necessárias para o desenvolvimento dos jogos dessa disciplina.

## Instruções

### **Parte 1: Game Loop**

Na primeira parte, você irá implementar o laço principal do jogo utilizando uma abordagem de taxa de quadros dinâmica.

1. **Game.cpp**

    1. Complete o método `Initialize` para inicializar o contador de tempo `mTicksCount`
    2. Implemente o método `RunLoop` para executar o laço principal do jogo
    3. Implemente o método `UpdateGame` para controlar a taxa de atualização de quadros

Ao final dessa etapa, você deverá ver uma janela com fundo preto que pode ser fechada com o ícone na barra superior. Além disso, se você imprimir (`SDL_Log`) o valor da variável `deltaTime` dentro da função `UpdateGame`, você deverá ver valores próximos a `0.016`, como ilustram as imagens a seguir:

<img src="{{ 'assets/images/tp1/1-result.png' | relative_url }}" alt="tp1-pong-1" width="560"/>
<img src="{{ 'assets/images/tp1/2-result.png' | relative_url }}" alt="tp1-pong-1" width="560"/>

### **Parte 2: Modelo de Objetos**

Na segunda parte, você irá implementar uma estrutura de objetos com hierarquia de classes e componentes.

1. **Actor.cpp**

    1. Implemente o construtor `Actor` para adicionar ao jogo o actor que está sendo criado 
    2. Implemente o destrutor `~Actor` para remover ao jogo o actor que está sendo destruído 
    3. Implemente o método `Update` para atualizar o actor e seus componentes
    4. Implemente o método `ProcessInput` para processar as entradas do actor e seus componentes

2. **DrawComponent.cpp**

    1. Implemente o construtor `DrawComponent` para adicionar o componente desenhável ao jogo
    2. Implemente o destrutor `~DrawComponent` para remover o componente desenhável ao jogo
    3. Implemente o método `Draw` para desenhar um quadrado com o renderer do jogo

3. **Game.cpp**

    1. Implemente o método `UpdateActors` para atualizar os actors do jogo
    2. Implemente o método `AddActor` para adicionar um actor ao jogo
    3. Implemente o método `RemoveActor` para remover um actor do jogo
    4. Implemente o método `AddDrawable` para adicionar um componente visual ao jogo
    5. Implemente o método `RemoveDrawable` para remover um componente visual ao jogo
    6. Complete o método `ProcessInput` para passar os eventos de entrada aos actors do jogo
    7. Complete o método `GenerateOutput` para desenhar os componentes visuais
    8. Complete o método `Shutdown` para deletar os actors do jogo

Ao final dessa segunda etapa, você deverá poder criar actors e adicioná-los ao jogo na função `Game::Initialize()`. Por exemplo, experimente criar um retângulo branco de tamanho 100x200 no meio da tela com o código abaixo:

```
Actor *a = new Actor(this);
a->SetPosition(Vector2(mWindowWidth/2.0,mWindowHeight/2.0));
new DrawComponent(a, 100, 200);
```

A primeira vista pode parecer estranho criar um DrawComponent sem armazenar o ponteiro resultando em uma 
variável. Isso não é necessário pois passamos o ponteiro do actor na construção do componente. De qualquer forma, 
o seu jogo deveria mostrar a seguinte saída:

<img src="{{ 'assets/images/tp1/3-result.png' | relative_url }}" alt="tp1-pong-1" width="560"/>

### **Parte 3: Objetos do Pong**

Na terceira, você irá utilizar a estrutura de actors criada na parte anterior para criar os actors do Pong: Ball e Paddle.

1. **Paddle.cpp**

    1. Implemente o construtor `Paddle` para adicionar um componente de desenho
    2. Implemente o método `OnProcessInput` para atualizar a direção do movimento da raquete
    3. Implemente o método `OnUpdate` para atualizar a posição da raquete
    
2. **Ball.cpp**

    1. Implemente o construtor `Ball` para adicionar um componente de desenho
    2. Implemente o método `OnUpdate` para atualizar a posição da bola

3. **Game.cpp**

    1. Implemente o método `InitializeActors` para inicializar a bola e a raquete

Essa etapa conclui as implementações básicas do jogo, que deveria ter um resultado como o mostrado no vídeo do início do roteiro.

### **Parte 4: Customização**

Na quarta, e última etapa, você irá customizar a implementação básica para criar uma versão exclusiva do Pong.

1. Ajuste o tamanho da quadra (janela), a posição horizontal das raquetes bem como suas velocidades e alturas da forma que achar mais interessante;

2. Defina um novo esquema de cores que modifique as cores do fundo, da raquete e da bola;

3. Crie um novo actor para desenhar uma parede do lado oposto da raquete. Você pode escolher a largura e a cor dessa parede, mas a altura deve ser igual a altura da janela. Ajuste a posição de colisão da bolinha para que ela retorne exatamente quando bater nessa parede.

## Submissão

Para submeter o seu trabalho, basta fazer o commit e o push das suas alterações no repositório que foi criado para
você no GitHub classroom.

```
git add .
git commit -m 'Submissão TP1'
git push
```

## Barema

- Parte 1: Game Loop (10%)
- Parte 2: Modelo de Objetos (50%)
- Parte 3: Objetos do Pong (30%)
- Parte 4: Customização (10%)

## Referências

- Parte 1: 
    - [Game Programming in C++, Cap 1: The Game Loop and Game Class](https://learning.oreilly.com/library/view/game-programming-in/9780134598185/ch01.xhtml#ch01lev2sec3)
    - [Game Programming in C++, Cap 1: Updating the Game](https://learning.oreilly.com/library/view/game-programming-in/9780134598185/ch01.xhtml#ch01lev2sec11)

- Parte 2: 
    - [Game Programming in C++, Cap 2: Game Objects](https://learning.oreilly.com/library/view/game-programming-in/9780134598185/ch02.xhtml#ch02lev2sec1)    

- Parte 3: 
    - [Game Programming in C++, Cap 1: Updating the Game](https://learning.oreilly.com/library/view/game-programming-in/9780134598185/ch01.xhtml#ch01lev2sec11)
