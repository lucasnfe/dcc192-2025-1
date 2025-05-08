---
layout: page
title:  TP3 - Super Mario Bros 1-1
permalink: /avaliacoes/tp3-smb
nav_exclude: true
---

# TP3: Super Mario Bros 1-1

#### Entrega: 19/05/2025 às 23:59h

## Introdução

O Super Mario Bros (SMB), lançado pela Nintendo em 1985, foi um dos jogos mais populares da era dos consoles 8 bits. SMB é um jogo de plataforma de rolagem lateral onde o objetivo do jogador é se mover para a direita para chegar a um mastro de bandeira no final de cada nível. O jogador controla o Mario, protagonista da série. O irmão de Mario, Luigi, é controlado pelo segundo jogador no modo multijogador e assume o mesmo papel e funcionalidade de Mario. Na narrativa do jogo, o mundo é chamado de Reino do Cogumelo e o Mario está atravessando-o para salvar a Princesa Peach do antagonista Bowser. 
O video a seguir mostra um *gameplay* do jogo original:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/7qirrV8w5SQ?si=uaXtyaT-f2IL-16m" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## Objetivo

O objetivo desse projeto é praticar a implementação de integração com editores externos, rolagem de câmera, detecção de colisão com AABBs e animação 2D. Para isso, você irá implementar as mecânicas básicas de correr, pular, e acertar inimigos no primeiro nível  do SMB. Primeiro, você irá implementar um parser para carregar objetos do jogo a partir de arquivos csv exportados do editor de mapas [[Tiled]](https://www.mapeditor.org/). Como parte dessa tarefa, você irá implementar o componente `DrawSpriteComponent` para desenhar sprites estáticos (i.e., não-animados) na tela. Segundo, você irá implementar a rolagem de câmera, garantindo que o personagem sempre fique a frente da câmera. Terceiro, você irá implementar o componente `AABBCollideComponent` para detectar colisões entre caixas delimitadoras alinhadas com os eixos (AABBs). Quarto, você irá implementar o componente `DrawAnimatedComponent`, de animações de sprites, utilizando sprite sheets gerados pela [[FreeTexturePacker]](https://free-tex-packer.com/app/). Por fim, você irá implementar os goombas, incluindo as mecânicas de matá-los quando o jogador pula em cima deles e de matar o jogador quando eles o acertam no chão. O vídeo a seguir mostra um gameplay da versão que você irá implementar:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/CK-fD2JSvMo?si=u1GGxFjZxB4p7iwH" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

## Código-base

1. Aceite o projeto *tp3-super-mario-bros-1-1* no GitHub classroom [[nesse link]](https://classroom.github.com/a/A3VJmRBG)

2. Clone o seu novo repositório no seu computador:

    ```
    # Substitua <GITHUB_USERNAME> pelo seu usuário do GitHub
    git clone https://github.com/ufmg-dcc192/tp3-super-mario-bros-1-1-<GITHUB_USERNAME>.git
    ```

3. Abra o projeto *tp3-super-mario-bros-1-1* na CLion e, antes de começar a sua implementação, verique com cuidado as definições de métodos e atributos de cada classe:

    - **DrawSpriteComponent**

        Componente para desenho de sprites estáticos (i.e., não animados). 

    - **DrawAnimatedComponent**

        Componente para desenho de sprites animados (estende `DrawSpriteComponent`). 

    - **AABBColliderComponent**

        Componente para detecção de colisão entre AABBs. 
        
    - **Block**

        Classe que estende `Actor` para representar um bloco do jogo.

    - **Goomba**

        Classe que estende `Actor` para representar o Goomba, inimigo que se movimenta horizontalmente de um lado para o outro.    

    - **Mario**

        Classe que estende `Actor` para representar o Mário, que é controlado pelo jogador.   

    - **Spawner**

        Classe que estende `Actor` para representar um "gatilho" (ou *trigger*) que cria um goomba quando o jogador está próximo.    

    Observação: o código base desse projeto foi construído a partir do código do projeto anterior [[TP2: Asteroids]](tp2-asteroids), portanto muitas das classes já foram introduzidas anteriormente.

## Instruções

### **Parte 0: Preparação dos Assets**

Antes de começar a programar, você irá preparar os assets (recursos) que serão carregados no início do jogo. Esses assets incluem os sprite sheets dos personagens e dos blocos da primeira fase do Super Mario Bros., além de um arquivo .csv com o tilemap dessa fase.

- **Sprite Sheet**

    Utilize o [[FreeTexturePacker]](https://free-tex-packer.com/app/) para gerar os sprite sheets do mario, goomba e blocos. **Desabilite** a opção `Allow trim`, utilize o formato de dados `json (Array)` e o método `BestAreaFit` para exportar os sprite sheets. Copie os sprite sheets (imagens e dados) para os seus respectivos locais dentro do diretório `Assets` do projeto. Por exemplo, copie o sprite sheet do Mario para o local `Assets/Sprites/Mario`.

- **Tilemap**

    Utilize o [[Tiled]](https://www.mapeditor.org/) para abrir o arquivo `Levels/Level1-1/level1-1.tmx` e exportar seu conteúdo para um arquivo `Levels/Level1-1/Level1-1.csv`. Inspecione o csv gerado para compreender sua estrutura de tiles.

### **Parte 1: Carregando uma fase**

Na primeira parte, você irá ler um arquivo .csv exportado pelo Tiled para carregar a primeira fase do jogo. Para poder visualizar os blocos na tela, você também terá que implementar o componente `DrawSpriteComponent` para desenhar sprites estáticos.

- **DrawSpriteComponent.cpp**

    1. Implemente o construtor da classe e o método `Draw` para desenhar sprites estáticos

- **Block.cpp**

    1. Implemente o construtor da classe para adicionar um componente `DrawSpriteComponent` no construtor do bloco

- **Mario.cpp**

    1. Implemente o construtor da classe para adicionar um componente `DrawSpriteComponent` no construtor do personagem

- **Game.cpp**

    1. Implemente o método `LoadTexture` para carregar uma textura com a SDL. Para testar seu código até aqui, crie uma instância de `Block` na função `InitializeActors` com uma textura da sua escolha. 

        ```
        auto block = new Block(this, "../Assets/Sprites/Blocks/BlockA.png");
        block->SetPosition(Vector2(5 * TILE_SIZE, 5 * TILE_SIZE));
        ```

    2. Implemente o método `LoadLevel` para ler o arquivo csv e instanciar uma matriz de inteiros `LEVEL_HEIGHT X LEVEL_WIDTH` representando os IDs dos tiles. Teste o seu código chamando essa função em `InitializeActor`, carregando a fase do arquivo `level1-1.csv`. Imprima a matriz na saída padrão com `SDL_Log` e compare a saída com o conteúdo do arquivo: eles devem ser os mesmos.

    3. Implemente o método `BuildLevel` para percorrer a matriz de tiles carregada no item anterior e instanciar game objects para o mario, os canos e os blocos. Para saber qual ID de tile corresponde a qual textura, abra o arquivo `level1-1.tmx` e inspecione os IDs de cada tile. Inicialize as posições dos objetos no mundo de acordo com as suas posições na matriz de tiles. Guarde a instância do mario no atributo `mMario` da classe game. Os blocos não precisam ser armazenados na classe.
    
    4. Adicione ao método `InitializeActors` a chamada para as função `LoadLevel` e `BuildLevel`, nessa ordem, para que a fase seja carregada e instanciada no momento de inicialização do jogo.

Ao final dessa etapa, você deveria ver uma saída como a ilustrada na figura abaixo:

<img src="{{ 'assets/images/tp3/1-result.png' | relative_url }}" alt="tp3-smb-1" width="560"/>

### **Parte 2: Rolagem de Câmera**

Na segunda parte, você irá implementar o movimento do jogador e da câmera, para que ele possa navegar horizontalmente sem colisão ao longo da fase.

- **Game.cpp**

    1. Implemente o método `UpdateCamera` para fazer a câmera seguir o jogador

- **Mario.cpp**

    1. Adicione o componente `RigidBodyComponent` no construtor do personagem para habilitar sua movimentação. Utilize a função `SetApplyGravity` para desabilitar a gravidade do personagem enquanto você estiver trabalhando na parte 2: isso irá facilitar o teste da câmera.

    2. Implemente o método `OnProcessInput` para mover o jogador horizontalmente

    3. Modifique o método `OnUpdate` para garantir que a posição horizontal do jogador esteja sempre à frente da câmera

Ao final dessa etapa, você deveria ver uma saída como no vídeo a seguir:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/4E3_dHmNRXE?si=XmrFUYrkg_nKfQua" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

### **Parte 3: Detecção de Colisão com AABBs**

Na terceira parte, você irá implementar o componente `AABBColliderComponent` para detectar colisões no jogo.

- **AABBColliderComponent.cpp**

    1. Implemente os métodos `GetMin` e `GetMax` para calcular os pontos de mínimo, máximo da AABB, respectivamente

    2. Implemente método `Intersect` para verificar se duas AABBs têm interseção

    3. Implemente os método `GetMinVerticalOverlap` e `GetMinHorizontalOverlap` para calcular as sobreposições verticais e horizontais da colisão, respectivamente.

    4. Implemente os métodos `DetectHorizontalCollision` e `DetectVertialCollision` para separar uma AABB após uma colisão horizontal e vertical, respectivamente.

    5. Implemente os métodos `ResolveHorizontalCollisions` e `ResolveVerticalCollisions` para resolver as colisões horizontais e verticais, respectivamente, entre os objetos do jogo.

- **Block.cpp**

    1. Adicione o componente `AABBColliderComponent` ao construtor dos blocos para habilitar colisões do jogador com os blocos do nível. Na criação, marque o bloco como estático `isStatic = true`.

- **Mario.cpp**

    1. Habilite a gravidade no personagem, removendo a chamada para a função `SetApplyGravity` que você adicionou na etapa anterior

    2. Adicione o componente `AABBColliderComponent` no construtor do personagem para habilitar colisões do jogador com os blocos do nível. Por padrão, o componente assume que o objeto não é estático, então não é necessário marcá-lo como não estático.

    3. Estenda o método `OnProcessInput` para implementar o pulo. O jogador só pode pular quando estiver no chão `mIsOnGround = true`.

Ao final dessa parte, você deveria ser capaz de navegar na primeira fase com as mecânicas de correr e pular, porém sem animação, como no vídeo a seguir:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/Iyoa4kdtAhU?si=nJ3MxXglRDZTto65" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

### **Parte 4: Animações**

Na quarta parte, você irá implementar o componente `DrawAnimatedSprite` para animar os objetos do jogo. 

- **DrawAnimatedComponent.cpp**

    Todos os quadros de um objeto estão armazenados no vetor `mSpriteSheetData`. Cada posição desse vetor é um ponteiro para um `SDL_Rect*`, representando as coordenadas de um sprite no sprite sheet. Além disso, todas as animações estão armazenadas no mapa `mAnimations`. Uma animação é identificada por um nome (string) e definida por um vetor de índices de quadros (armazenados em `mSpriteSheetData`). A nome da animação corrente é armazenado na variável membro `mAnimName`. 

    1. Implemente o método `Update` para atualizar o timer da animação

    2. Implemente o método `Draw` para desenhar o sprite corrente da animação

    3. Implemente o método `SetAnimation` para mudar a animação corrente

- **Mario.cpp**

    1. Modifique o construtor para que o personagem utilize o componente de desenho `DrawAnimatedComponent` ao invés de `DrawSpriteComponent`.
    
        Ao final desse item, você deveria ter o mesmo resultado da Parte 3, ou seja, o mário se movendo e colidindo mas sempre no estado idle.

    2. Implemente a método `ManageAnimations` para selecionar a animação correta enquanto o jogador estiver vivo `!mIsdead`: 
        1. Se estiver no chão e correndo, a animação correta é `"run"`
        2. Se estiver no chão, mas não estiver correndo, a animação `"idle"` 
        3. Se estiver não estiver no chão, a animação é `"jump"` 


Ao final dessa parte, você deveria ver as animações de run, idle e jump tocando de acordo com o estado do jogador, como no vídeo a seguir:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/B8LGpTGoz9s?si=w02KJvMp8div2c8Z" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

### **Parte 5: Inimigos**

Na quinta parte, você irá implementar os goombas e os spawners, que criam goombas quando o jogador está próximo.

- **Game.cpp**

    1. Estenda o método `BuildLevel` para instanciar spawners de acordo com a matriz de tiles. 

- **Goomba.cpp**

    1. Crie os componentes `RigidBodyComponent`, `AABBColliderComponent`, e `DrawAnimatedComponent` no construtor, de forma similar ao Mario

    2. Implemente o método `Kill` para tocar a animação de morte e desabilitar os componentes

    3. Implemente o método `OnUpdate` para destruir os goombas que já morreram

    4. Implemente o método `OnHorizontalCollision` para alterar a direção do goomba quando ele colidir horizontalmente contra blocos ou outros goombas. Além disso, o Goomba deve matar o mario caso a colisão seja horizontal e contra o jogador.

- **Spawner.cpp**

    1. Implemente o método `OnUpdate` para criar um goomba quando o jogador estiver próximo.

- **Mario.cpp**

    1. Modifique o método `OnUpdate` para detectar quando o jogador morreu.

    2. Implemente o método `Kill` para tocar a animação de morte e finalizar o jogo

    3. Implemente o método `OnHorizontalCollision` para matar o mario caso ele tenha colidido contra um goomba

    4. Implemente o método `OnVerticalCollision` para matar o goomba caso o jogador tenha colidido contra um goomba

Essa etapa conclui as implementações básicas do jogo, que deveria ter um resultado como o mostrado no vídeo do início do roteiro. 

### **Parte 6: Customização**

Na sexta, e última etapa, você irá ajustar as variáveis do jogo para criar uma versão única do Super Mário Bros.

1. Altere os parâmetros de movimentação (velocidade, massa, coeficientes de atrito, etc.) do jogador para encontrar uma jogabilidade que mais lhe agrada.

2. Altere o nível dado ou crie um completamente novo.

3. Implemente a movimentação dos blocos de tijolo (tipo B) quando o mario os acerta por baixo. Nesse caso, o bloco deve se mover para cima e para baixo, retornando exatamente no ponto que estava originalmente.

## Submissão

Para submeter o seu trabalho, basta fazer o *commit* e o *push* das suas alterações no repositório que foi criado para você no GitHub classroom.

```
git add .
git commit -m 'Submissão TP3'
git push
```

## Barema

- Parte 1: Carregando uma fase (5%)
- Parte 2: Rolagem de Câmera (5%)
- Parte 3: Detecção de Colisão com AABBs (30%)
- Parte 4: Animações (30%)
- Parte 5: Inimigos (10%)
- Parte 6: Customização (20%)

## Referências

- Parte 1: 
    - [Game Programming in C++, Cap 3, Vectors nad Basic Physics](https://learning.oreilly.com/library/view/game-programming-in/9780134598185/ch03.xhtml)