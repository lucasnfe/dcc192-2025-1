---
layout: page
title:  TP2 - Asteroids
permalink: /avaliacoes/tp2-asteroids
nav_exclude: true
---

# TP2: Asteroids

#### Entrega: 23/04/2025 às 18:59h

## Introdução

Assim como o Pong (projeto anterior), o Asteroids (lançado pela Atari em 1979) também foi um dos jogos mais populares da era do fliperama. O asteroids é um jogo com uma temática espacial onde o jogador controla uma nave com o objetivo de atirar raios laser para destruir todos os asteroides que se movem no mapa sem colidir com nenhum deles. Quando o jogador destruir todos os asteroides, um número maior de asteroides do que o anterior será criado no mapa, aumentando a dificuldade do jogo. Se o jogador colidir com um asteroid, ele perderá uma vida. O jogo termina quando o jogador perder suas três vidas. O video a seguir mostra um *gameplay* do jogo original:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/WYSupJ5r2zo?si=NNIkvpXUij-DR0Zc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## Objetivo

Nesse projeto, você irá desenvolver as mecânicas princiais de movimentação, colisão e tiro do Asteroids em C++ e SDL. Nessa versão, o jogador poderá mover-se e atirar com a nave como no jogo original, destruindo os asteroides caso um laser os acerte. O jogo será reiniciado quando a nave colidir com um asteroide. Inicialmente você irá implementar os componentes `RigidBodyComponent` e `CircleColliderComponent` para movimentar e detectar as colisões dos objetos do jogo. Em seguida, você irá modificar o componente `DrawCollider` para desenhar os objetos simulando gráficos vetoriais. Por fim, você irá utilizar esses componentes para implementar uma nave que atira raios laser e gerar um dado número de asteroides com geometrias aleatórias. O video a seguir mostra um gameplay da versão que você irá implementar:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/WrbIiKNksL4?si=Qp5D_RNHu9K5nIg5" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## Código-base

1. Aceite o projeto *tp2-asteroids* no GitHub classroom [[nesse link]](https://classroom.github.com/a/9e8MRQ68)

2. Clone o seu novo repositório no seu computador:

    ```
    # Substitua <GITHUB_USERNAME> pelo seu usuário do GitHub
    git clone https://github.com/ufmg-dcc192/tp2-asteroids-<GITHUB_USERNAME>.git
    ```

3. Abra o projeto *tp2-asteroids* na CLion e, antes de começar a sua implementação, verique com cuidado as definições de métodos e atributos de cada classe:

    - **RigidBodyComponent**

        Componente de movimentação de objetos rígidos. 

    - **CircleColliderComponent**

        Componente de detecção de colisão baseado em comparações entre círculos. 

    - **Ship**

        Classe que estende `Actor` para representar a nave.
        
    - **Asteroid**

        Classe que estende `Actor` para representar um asteroide.

    - **Laser**

        Classe que estende `Actor` para representar uma partícula de laser, que é atirada pela nave quando o jogador pressiona a tecla **Espaço**.    

    Observação: o código base desse projeto foi construído a partir do código do projeto anterior [[TP1: Pong]](tp1-pong), portanto muitas das classes já foram introduzidas anteriormente.

## Instruções

### **Parte 1: Desenhos Vetoriais**

Na primeira parte, você irá modificar o componente `DrawComponent` para desenhar os objetos do jogo simulando gráficos vetoriais.

- **DrawComponent.cpp**

    1. Implemente o método `DrawPolygon` para desenhar um polígono formado por um conjunto de vértices

    2. Implemente o método `DrawCircle` para gerar e desenhar um conjunto de vértices em um círculo

    3. Implemente o método `Draw` para desenhar um objeto

Ao final dessa primeira etapa, teste a sua implementação criando um actor com um `DrawComponent` na função `Game::Initialize()`. Por exemplo, experimente criar um actor representado por um triângulo com o código abaixo:

```
std::vector<Vector2> vertices;
vertices.emplace_back(Vector2(0.0f, -50.0f));
vertices.emplace_back(Vector2(-50.0f, 50.0f));
vertices.emplace_back(Vector2(50.0f, 50.0f));

Actor *testActor = new Actor(this);
testActor->SetPosition(Vector2(mWindowWidth / 2.0f, mWindowHeight / 2.0f));

new DrawComponent(testActor, vertices);
```

O seu jogo deveria mostrar a seguinte saída:

<img src="{{ 'assets/images/tp2/1-result.png' | relative_url }}" alt="tp1-pong-1" width="560"/>

Note que o círculo verde ainda não está inscrito no polígono do actor. Isso ocorre porque a função
`DrawCircle` tem um valor padrão de raio `r=10`. Nas próximas etapas, você pode alterar o raio do
círculo para o raio definino no componente `CircleColdier`.

### **Parte 2: Movimentação de Objetos Rígidos**

Na segunda parte, você irá implementar os componentes `RigidBodyComponent` e `CircleColliderComponent` para movimentar e detectar as colisões dos objetos do jogo.

- **RigidBodyComponent.cpp**

    1. Implemente o método `ApplyForce` para adicionar uma força à acceleração

    2. Implemente o método `Update` para calcular a nova posição do objeto utilizando o Método de Euler Semi-implícito

    3. Implemente o método `ScreenWrap` para teletransportar os objetos para o lado oposto quando eles saírem da tela

- **CircleColliderComponent.cpp**

    1. Implemente o método `Intersect` para detectar a colisão de círculos com círculos

Ao final dessa segunda etapa, teste a sua implementação adicionando um componente  `RigidBodyComponent` ao actor de criado ao final da etapa anterior. Aplique um força qualquer a esse actor, como no exemplo abaixo:

```
RigidBodyComponent *rb = new RigidBodyComponent(testActor, 1.0f);
rb->ApplyForce(Vector2(0.0f, 1000.0f));
``` 

O seu jogo deveria mostrar uma saída como esta:

<img src="{{ 'assets/images/tp2/2-result.gif' | relative_url }}" alt="tp1-pong-1" width="560"/>

Note que essa visualização é um gif, portanto o frame rate está perceptivelmente mais baixo do que o que você verá na sua implementação.

### **Parte 3: Objetos do Asteroids**

Na terceira parte, você irá utilizar os novos componentes para implementar uma nave que atira raios laser e gerar um dado número de asteroides com geometrias aleatórias.

- **Game.cpp**

    1. Inicialize a classe `Random` para gerar números aleatórios

    2. Instancie a nave e os asteroides

    3.  Implemente os métodos `AddAsteroid` e `RemoveAsteroid` para gerenciar a criação e remoção de asteroides

- **Ship.cpp**

    1. Implemente o construtor de `Ship` criando um triângulo a partir de três vértices para representar a nave visualmente e instanciando seus componentes

    2. Complete o método `OnProcessInput` para mover a nave para frente e rotacioná-la quando o jogador os direcionais para frente e esquerda/direita, respectivamente.

    3. Implemente o método `OnUpdate` para atualizar a nave a cada quadro

- **Asteroid.cpp**

    1. Implemente o construtor `Asteroid` gerando um círculo com ruídos para representar o asteroide visualmente e instanciando seus componentes

    2. Implemente o destrutor `~Asteroid` para removê-lo da lista de asteroides do jogo.

    3. Gere um conjunto de vértices em uma circunferência adicionando um pequeno ruído aleatório a cada um deles

- **Laser.cpp**

    1. Implemente o construtor `Laser` gerando um segmento de reta para representar o asteroide visualmente e instanciando seus componentes

    2. Implemente o método `OnUpdate` para atualizar o raio laser a cada quadro

Essa etapa conclui as implementações básicas do jogo, que deveria ter um resultado como o mostrado no vídeo do início do roteiro.

### **Parte 4: Customização**

Na quarta, e última etapa, você irá ajustar as variáveis do jogo para criar uma versão única do Asteroids.

1. Ajuste os tamanhos do universo (janela), nave e asteroides da forma que achar mais interessante;

2. Ajuste os parâmetros de movimentação (aceleração, velocidade escalar, velocidade máxima, velocidade mínima, massa, coeficientes de resistência, etc) da nave e dos asteroides da forma que achar mais interessante;

3. Implemente a a funcionalidade de gerar três novos asteroides menores e mais rápidos quando um grande é destruído. 

4. Implemente a animação de destruição dos asteroides. Quando um asteroide for destuído, crie um sistema de partículas onde cada partícula é um ponto que é atirado para uma direção aleatória e vive por poucos segundos. 

## Submissão

Para submeter o seu trabalho, basta fazer o *commit* e o *push* das suas alterações no repositório que foi criado para você no GitHub classroom.

```
git add .
git commit -m 'Submissão TP2'
git push
```

## Barema

- Parte 1: Desenhos Vetoriais (30%)
- Parte 2: Movimentação de Objetos Rígidos (20%)
- Parte 3: Objetos do Asteroids (30%)
- Parte 4: Customização (20%)

## Referências

- Parte 1: 
    - [Game Programming in C++, Cap 3, Vectors nad Basic Physics](https://learning.oreilly.com/library/view/game-programming-in/9780134598185/ch03.xhtml)
