---
layout: page
title:  TP4 - Super Mario Bros 1-2
permalink: /avaliacoes/tp4-smb2
nav_exclude: true
---

# TP4: Super Mario Bros 1-2

#### Entrega: 16/06/2025 às 23:59h

## Introdução

No último [trabalho prático](tp3-smb) (TP3), você implementou as mecânicas básicas de correr, pular, e acertar inimigos a primeira fase do Super Mario Bros (SMB). Para isso, você teve que desenvolver os sistema de câmera, colisão e animação, além de um *parser* de *levels* construídos no Tiled. Nesse TP4, você irá expandir esse projeto para incluir o menu principal e a segunda fase do jogo. Além disso, o seu jogo agora terá um Heads-Up Display (HUD), música e efeitos sonoros.

## Objetivo

O objetivo desse projeto é praticar a implementação de gerenciadores de cenas, HUD e sistemas de áudio em jogos. Primeiro, você irá implementar telas de UI e seus elemetos básicos, como textos, botões e imagens. Em seguida, você irá implementar um gerenciador de cenas como uma máquina de estados finita usando if/else (ao invés de switch). Depois, você irá utilizar a estrutura de UI criada para construir o HUD do jogo. Por fim, você irá implementar um sistema para gerenciar um conjunto finito de canais de áudio da SDL_Mixer. O vídeo a seguir mostra um gameplay da versão que você irá implementar:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/ut-L9AxYgmM?si=I5qAgEoj4Zv5_CI_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

## Código-base

1. Aceite o projeto *tp4-super-mario-bros-1-2* no GitHub classroom [[nesse link]](https://classroom.github.com/a/jPTjYsA1)

2. Clone o seu novo repositório no seu computador:

    ```
    # Substitua <GITHUB_USERNAME> pelo seu usuário do GitHub
    git clone https://github.com/ufmg-dcc192/tp4-super-mario-bros-1-2-<GITHUB_USERNAME>.git
    ```

3. Abra o projeto *tp4-super-mario-bros-1-2* na CLion e, antes de começar a sua implementação, verique com cuidado as definições de métodos e atributos de cada classe:

    - **UIScreen**

        Classe base para criação de telas de interface, como menus e HUD. 

    - **UIElement**

        Classe abstrata base para implementação de elementos de UI. Ela define atributos básicos de posição, tamanho e cor, que podem ser usados para desenhar elementos de interface. Essa classe deve ser estendida quando um novo elemento de UI for criado.

    - **UIFont**

        Classe auxiliar para carregar e descarregar fontes em formato true type.

    - **UIText**, **UIButton**, **UIImage**

        Classes que estendem UIElement para implementar três elementos de interface básicos: texto, botões e imagens.

    - **HUD**

        Classe que estende UIScreen para implementar o HUD do jogo, condendo uma contagem de pontos, fase e tempo. 
      
    - **AudioSystem**

        Classe para gerenciamento de sons, permitindo tocar, pausar, resumir e parar sons armazenados em arquivos.

    - **SpatialHashing**

        Classe que implementa um Hash Spacial para otimização de renderização e colisão. Você não irá trabalhar nessa classe, ela foi adicionada para possibilitar a criação de jogos maiores nos projetos finais.

    Observação: o código base desse projeto foi construído a partir do anterior [[TP3: Super Mario Bros 1-1]](tp3-smb), assim. As classes restantes já foram introduzidas anteriormente. 

## Instruções

### **Parte 1: Menu Principal**

Na primeira parte, você irá construir o menu principal do jogo e, para isso, terá que implementar um sistema de UI simples que suporte textos, botões e imagens.

#### **Parte 1-1: Textos**

Vamos começar nossa implementação pelos elementos de texto. Os botoões e a imagens seguirão uma ideia similar.

- **Font.cpp**

    1. Implemente o método `Load()` para carregar um mapa de fontes true type considerando uma lista de tamanhos de fonte suportados.

    2. Implemente o méodo `Unload()` para descarregar todas as fontes que estão carregadas no mapa de fontes.

    3. Complete o método `RenderText()` para renderizar uma string em uma textura usando a fonte carregada.

- **UIText.cpp**

    Objetos `UIText` são utilizados para desenhar textos de UI. Eles estendem a class base `UIElement` com um atributo `std::string mText`, que contém o texto que será mostrado, e outro `SDL_Texture *mTextTexture`, que representa uma textura com esse texto e um atributo `UIFont* mFont` com a fonte que será utilizada para renderizar `mTextTexture`. Esses atributos serão utilizados para gerenciar e desenhar textos em telas de UI (`UIScreens`).

    1. Implemente o construtor da classe chamando a função `SetText` para atualizar a textura do texto.

    2. Implemente o método `SetText(const std::string &text)` para modificar tanto a string `mText` quanto a textura `mTextTexture`. Nessa etapa, você irá utilizar os métodos da classe `Font.cpp` implementados.

    3. Implemente o método `Draw` para desenhar o texto em uma determina **posição relativa** na tela. 

- **Game.cpp** 

    1. Implemete o método `LoadFont()` para criar objetos do tipo `Font` ao jogo. As fontes carregas serão armazenadas em um dicionário, para que, quando 
    elas forem utilizadas novamente por elementos de interface, elas sejam recuperadas diretamente da memória primária, e não da secundária.

- **UIScreen.cpp**

    1. Implemente o construtor da classe para adicionar o novo objeto à lista de telas do jogo e carregar a fonte que será utilizada na UI da mesma.

    2. Implemente o destrutor para destruir os textos que foram adicionados à tela.

    3. Implemente o método `Draw()` para desenhar os textos.

    4. Implemente o método `AddText()` para adicionar elementos de texto à tela

Ao final dessa etapa, você deveria ser capaz de criar uma tela com o construtor `UIScreen` e adicionar textos a ela. Para testar o seu código, adicione o seguinte trecho ao método `Game::LoadMainMenu()`:

```
auto mainMenu = new UIScreen(this, "../Assets/Fonts/SMB.ttf");
mainMenu->AddText("Super Mario Bros", Vector2(170.0f, 50.0f), Vector2(300.0f, 30.0f), 60);
```

Você deveria ver uma tela conforme a imagem a seguir:

<img src="{{ 'assets/images/tp4/1-result.png' | relative_url }}" alt="tp4-smb-1" width="560"/>

#### **Parte 1-2: Botões**

 Um botão pode ser visto como um UIText dentro de uma área retângular que pode ser pressionada via mouse ou teclado. Por isso, a classe `UIButton` possui um atributo `UIText mText` e outro `std::function<void()> mOnClick`. O texto `mText` será desenhado dentro do botão, que quando for pressionado, chamará a função apontada por `mOnClick`.

- **UIButton.cpp**

    1. Implemente o método `Draw` para desenhar o texto do botão e o seu fundo caso ele esteja selecionado.

    2. Implemente o método `OnClick` para chamar a função do botão.

- **UIScreen.cpp**

    1. Complemente o código do destrutor para destruir os botões que foram adicionados à tela.

    2. Complemente o método `Draw()` para desenhar os botões.

    3. Implemente o método `HandleKeyPress()` para navegar na lista de botões com o teclado.

    4. Implemente o método `AddButton()` para adicionar botões à tela

Ao final dessa etapa, você deveria ser capaz de adicionar botões às tela. Para testar o seu código, adicione o seguinte trecho ao método `Game::LoadMainMenu()` abaixo da linha que adicionou na etapa anterior para criar um texto:

```
auto button1 = mainMenu->AddButton("1 Player", Vector2(mWindowWidth/2.0f - 100.0f, 200.0f), Vector2(200.0f, 40.0f),
                                       nullptr);

auto button2 = mainMenu->AddButton("2 Players", Vector2(mWindowWidth/2.0f - 100.0f, 250.0f), Vector2(200.0f, 40.0f),
                                       nullptr);
```

Assumindo que você manteve o texto criado na etapa anterior, você deveria ver uma tela conforme a imagem a seguir:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/MzhULVJToGE?si=f8E7yYPCQ3KrvcDC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

#### **Parte 1-3: Imagens**

Carregar uma imagem de UI é similar à carregar um texto, pois também envolve criar uma textura, mas dessa vez a partir de um arquivo de imagem armazenado na memória secundária, ao invés de uma fonte true type.  

- **UIImage.cpp**

1. Implemente o construtor da classe para carregar uma textura que será desenhada por essa imagem.

2. Implemente o destrutor da classe para destruir a textura que foi carregada no construtor.

3. Implemente o método `Draw()` para desenhar a textura na tela.

- **UIScreen.cpp**

1. Complemente o código do destrutor para destruir as imagens que foram adicionados à tela.

2. Complemente o método `Draw()` para desenhar as imagens.

3. Implemente o método `AddImage()` para adicionar imagens à tela.

Ao final dessa etapa, você deveria ser capaz de criar imagens nas telas de UI. Para testar o seu código, susbtitua o código que carrega o texto pelo que carrega a imagem: 

```
const Vector2 titleSize = Vector2(178.0f, 88.0f) * 2.0f;
const Vector2 titlePos = Vector2(mWindowWidth/2.0f - titleSize.x/2.0f, 50.0f);
mainMenu->AddImage("../Assets/Sprites/Logo.png", titlePos, titleSize);
```

Ajustando a posição dos botões criados na etapa anterior para que eles fiquem abaixo da imagem, você deveria ver uma saída como a do vídeo a seguir:

<div class="embed-youtube">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/uUWEcvJ_ICw?si=i0q9sxg57lGfQwKG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

### **Parte 2: Gerenciamento de Cenas**

Na segunda parte, você irá desenvolver um gerenciador de cenas para possibilitar descagarregamento e carregamento de game objects durante o jogo. Lembre-se que gerenciadores de cenas são implementados como uma máquina de estados finita, que por simplicidade será incluída diretamente na classe `Game`.  

Quando a função `SetGameScene` é chamada, ela irá alterar um estado `mSceneManagerState` da máquina para `SceneManagerState::Entering` e salva o tempo de transição. Assim, durante o update, o jogo poderá verificar esse estado e, utilizando um contador, verificar quando o tempo de transição tiver passado.

- **Game.cpp**

1. Implemente o método `SetGameScene(Game::GameScene scene, float transitionTime)` para mudar o estado da máquina de estados para `SceneManagerState::Entering` e armazenar a cena destino `Game::GameScene scene` passada como parâmetro. Essa função também possui um parâmetro `transitionTime` para controlar em quanto tempo a transição irá ocorrer. Controlar o tempo de transição é útil em momentos que você precisa esperar uma animação ocorrer antes de fazer a transição, como quando o Mario morre ou passa de fase.

2. Implemente o método `UpdateSceneManager` para atualizar a máquina de estados do gerenciador de cenas. Note que cada estado da máquina possui um tempo de transição. Isso é útil para fazer transições menos abruptas durante o jogo. É importante destacar também que quando a máquina estiver no estado `SceneManagerState::Active` e o tempo de transição tiver decorrido, ela irá chamar o método `Game::ChangeScene()`, que faz a troca de cenas efetivamente.

3. No método `UpdateGame`, chame o médoto `UpdateSceneManager` que você implementou no item anterior.

4. No método `GenerateOutput`, desenhe um retângulo preto nos momentos de transição de cena, ou sejam quando o gerenciador de cenas estiver no estado ativo.

5. No método `LoadMainMenu`, altere a criação do botão `Player 1` para chamar o método `SetGameScene` quando ele for pressionado, passando a cena GameScene::Level1 como parâmetro:

    ```
    mainMenu->AddButton("1 Player", button1Pos, buttonSize, [this]() {
            SetGameScene(GameScene::Level1)});
    ```

Ao final dessa etapa, você deveria ser capaz de fazer transições de cenas com o método `SetGameScene`, como mostrado abaixo:

<div class="embed-youtube">
<iframe width="560" height="315" src="https://www.youtube.com/embed/Q7GdEjFvzH0?si=pFN_hSx-8JAdAx-K" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

### **Parte 3: HUD**

Agora que você tem como criar telas de UI com a classe `UIScene`, você pode utilizá-la para criar um HUD. Basta
estender essa classe e adicionar textos, imagens e botões conforme necessidade. No caso do Super Mario Bros.,
o HUD é composto apenas de textos, a não ser o ícone das moedas, que é uma pequena imagem. Nessa seção, vamos implementar apenas o contador de pontos, o título da fase e o contador de tempo.

- **HUD.cpp**

1. Implemente o construtor da classe para criar os textos do contador de score, título da fase e contador de tempo do HUD. 

2. Implemente o método `SetTime(int time)` para alterar o texto do contador de tempo para um certo valor 
inteiro `time` passado como parâmetro.

3. Implemente o método `SetLevelName(const std::string &levelName)` para alterar o nome da fase para uma
certa string `levelName` passada como parâmetro.

- **Game.cpp**

1. Complete o método `ChangeScene` para criar um HUD quando a próxima cena `mNextScene` for o `Level1` ou 
`Level2`

2. Complete o método `UpdateGame` para chamar a função `UpdateLevelTime`, que irá atualizar o contador de tempo do HUD.

3. Implemente o método `UpdateLevelTime` para atualizar o tempo de jogo quando o jogo estiver em qualquer cena que não seja o menu principal e não estiver pausado. Essa função deve matar o Mario caso o tempo tenha acabado.

Ao final dessa etapa, você deveria ver um HUD tanto na primeira quanto na segunda fase do jogo, como mostrado no vídeo abaixo:

<div class="embed-youtube">
<iframe width="560" height="315" src="https://www.youtube.com/embed/Hkh0UwwJ0fg?si=P-FLvILPRqb6p1e1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

### **Parte 4: Sistema de Áudio**

Agora vamos construir um sistema de áudio para tocar músicas de fundo e efeitos sonoros. Esse sistema será implementado na classe `AudioSystem` e seguirá as mesmas ideias vistas na Aula 16. 

- **AudioSystem.cpp**

1. Implemente o construtor da classe para inicializar a SDL_mixer e alocar o número de canais de áudio passados como parâmetro.

2. Implemente o destrutor da classe para desalocar os sons carregados.

3. Implemente o método `Update` para verificar quais sons ainda estão tocando, para liberar canais que não tenham mais sons em reprodução.

4. Implemente o método `PlaySound(const std::string& soundName, bool looping)` para tocar um determinado som passado como parâmetro.  
O parâmetro `soundName` é o nome do arquivo de áudio armazenado no diretório `Assets/Sounds`. Note não é preciso adicionar esse prefixo quando for tocar um som, pois o próprio sistema de som já faz isso para você. O parâmetro `looping` controla se o som tocará repetidamente ou não. Lembre-se que quando esse método for chamado, pode ser que todos os canais estão ocupados, então temos que aplicar uma política para parar sons atualmente em reprodução. Usaremos a mesma política definida na Aula 16.

5. Implemente o método `StopSound(SoundHandle sound)` para parar o som definido pelo `SoundHandle sound`

6. Implemente o método `PauseSound(SoundHandle sound)` para pausar o som definido pelo `SoundHandle sound`

7. Implemente o método `Resume(SoundHandle sound)` para retomar o som definido pelo `SoundHandle sound`

- **Game.cpp**

1. Instancie um `AudioSystem` no método `Initialize`

2. Complete o método `ChangeScene` para tocar músicas de fundo nas fases 1 e 2

3. Complete o método `TogglePause` para tocar um efeito sonoro quando o jogo for pausado, parando a música de fundo. De forma inversa, quando jogo for retomado, toque um efeito sonoro e retome a música de fundo.

- **Mario.cpp**

    Todos os efeitos sonoros de interação do Mario com objetos do jogo, como inimigos e moedas, serão implementados na classe do Mario. Utilize o AudioSystem implementado para tocar os sons necessários (vide os TODOs desse arquivo).

    Ao final dessa última etapa, você deveria ouvir as músicas de fundo da primeira e segunda fase, bem como os efeitos sonoros de ações do Mario (pular, colisão com bloco, matar goomba, etc.) e o feedback sonoro de pause, como no vídeo do início do roteiro. 

### **Parte 5: Customização**

Na quinta, e última etapa, você irá ajustar as variáveis do jogo para criar uma versão única do Super Mário Bros.

1. Modifique a tela do menu principal (logo, botões, background, etc...) para que ele fique o mais parecido com a do jogo original.

2. Adicione moedas coletáveis nas fases, incluindo um contador no HUD para contar o número de moedas coletadas. Sugestão, crie um novo actor para itens coletáveis, como moedas e power ups. 

3. Adicione um efeito cross-fade (fade our + fade in) no gerenciador de cenas. 

## Submissão

Para submeter o seu trabalho, basta fazer o *commit* e o *push* das suas alterações no repositório que foi criado para você no GitHub classroom.

```
git add .
git commit -m 'Submissão TP4'
git push
```

## Barema

- Parte 1: Menu Principal (20%)
- Parte 2: Gerenciamento de Cenas (20%)
- Parte 3: HUD (20%)
- Parte 4: Sistema de Áudio (20%)
- Parte 5: Customização (20%)

## Referências

- [Game Programming in C++, Cap 7, Audio](https://www.oreilly.com/library/view/game-programming-in/9780134598185/)
- [Game Programming in C++, Cap 11, User Interfaces](https://www.oreilly.com/library/view/game-programming-in/9780134598185/)