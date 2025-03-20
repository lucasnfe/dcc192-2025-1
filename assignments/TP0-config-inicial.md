---
layout: page
title:  TP0 - Configuração Inicial
permalink: /avaliacoes/tp0-config-inicial
nav_exclude: true
---

# TP0: Configuração Inicial

#### Entrega: 24/03 às 18:59h

## Introdução

Jogos digitais são projetos de software relativamente grandes e complexos. Sendo assim, em contextos profissionais, eles são tipicamente desenvolvidos de maneira estruturada em um ambiente de desenvolvimento integrado (IDE) com um sistema de controle de versão. 
Nesse projeto você irá configurar o ambiente de desenvolvimento de jogos que será utilizado ao longo do curso. 

Primeiro você irá baixar e instalar a IDE CLion para programação e teste dos jogos. Em seguida, você irá criar um repositório GitHub (via Gihub Classroom) para o controle de versão e submissão do seu trabalho. Além disso, como primeiro projeto do seu repositório, você irá escrever um pequeno programa em C++ usando a biblioteca SDL para desenhar um quadrado em uma janela, como ilustrado na figura abaixo:

<img src="{{ 'assets/images/tp0/1-result.png' | relative_url }}" alt="tp0-config-inicial" width="1024"/>

Ao terminar esse programa, você terá que customizá-lo adicionando algumas funcionalidades extras, que estão descritas no final desse roteiro.

## Código-base

Siga as instruções abaixo para baixar o código-base desse trabalho prático:

1. Se você não tiver uma conta no GitHub, crie uma seguindo o tutorial [**[nesse link]**](https://git-scm.com/book/pt-br/v2/GitHub-Configurando-uma-conta)
2. Se você não tiver o git instalado no seu computador, faça a instalação seguindo o tutorial [**[nesse link]**](https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Instalando-o-Git)
3. Aceite o projeto `TP0: Configuração Inicial` no GitHub classroom [**[nesse link]**](https://classroom.github.com/a/fF3t-96b)
4. Clone o seu novo repositório no seu computador:

    ```
    # Substitua <GITHUB_USERNAME> pelo seu usuário do GitHub
    git clone https://github.com/ufmg-dcc192/tp0-config-inicial-<GITHUB_USERNAME>.git
    ```

## Instruções

### **Parte 1: Instalação**

Na primeira parte, você irá baixar e instalar a IDE CLion e a biblioteca SDL.

1. **Instalar a IDE CLion**

    1. Acesse o site da CLion [**[nesse link]**](https://www.jetbrains.com/clion) e siga as instruções de instalação para o seu sistema operacional;

    2. Durante a instalação, crie uma conta utilizando o seu email do DCC (ou da UFMG), o que irá ativar uma licensa gratuita.

2. **Instalar a bilioteca SDL**

    - **Linux**

        1. Acesse o site da versão 2.32.2 da SDL [**[nesse link]**](https://github.com/libsdl-org/SDL/releases/tag/release-2.32.2) e baixe o pacote `Source code.zip`

        2. Extraia o conteúdo do pacote no diretório temporário `/tmp/SDL2/`

        4. Instale a biblioteca no diretório `/opt/SDL2/`:
        
            ```
            cd /tmp/SDL2/
            ./configure --prefix /opt/SDL2/
            make all
            sudo make install
            ```

    - **Windows (64 bits)**

        1. Acesse o site da versão 2.32.2 da SDL [**[nesse link]**](https://github.com/libsdl-org/SDL/releases/tag/release-2.32.2) e baixe o pacote `SDL2-devel-2.32.2-VC.zip`

        2. Extraia o conteúdo do pacote no diretório `C:\Arquivos de Programas\SDL2\`, como na figura a seguir:

            <img src="{{'/assets/images/tp0/2-parte1-win.png' | prepend: site.baseurl }}" alt="p1-parte1" width="1024"/>

        3. Copie o arquivo `SDL2.dll` do diretório `C:\Arquivos de Programas\SDL2\lib\x64\` para o diretório `C:\Windows\System32\`, como na figura a seguir:

            <img src="{{'/assets/images/tp0/3-parte2-win.png' | prepend: site.baseurl }}" alt="p1-parte2" width="1024"/>            

    - **Mac**
        1. Acesse o site da versão 2.32.2 da SDL [**[nesse link]**](https://github.com/libsdl-org/SDL/releases/tag/release-2.32.2) e baixe o pacote `SDL2-2.32.2.dmg`

        2. Clique na imagem para abrí-la e copie e o pacote `SDL2.framework` para o diretório `/Library/Frameworks/`. Ao final dessa etapa, a SDL deve estar configurada dessa maneira:

            <img src="{{'/assets/images/tp0/4-parte1-mac.png' | prepend: site.baseurl }}" alt="p1-parte1" width="1024"/>

### **Parte 2: primeiro programa SDL**

Nessa etapa, você irá utilizar a IDE Clion para escrever um programa em C++/SDL2 que desenha um quadrado em uma janela. Siga as instruções `TODO` nos arquivos do projeto  que você baixou do GitHub, respeitando a seguinte ordem:

1. **main.cpp**

O projeto do TP0 contém apenas um arquivo `main.cpp` e portanto quando você concluir as instruções desse arquivo, essa etapa 2 estará concluída. A figura abaixo ilustra como essas intruções irão aparecer como comentários ordenados:

<img src="{{'/assets/images/tp0/5-main.png' | prepend: site.baseurl }}" alt="p1-parte1" width="1024"/>

### **Parte 3: Customização**

Na terceira, e última etapa, você irá adicionar algumas funcionalidades extras:

1. Desenhe pelo menos mais um quadrado na tela preenchido com uma cor diferente do primeiro.

2. Desenhe múltiplos pontos com a função `SDL_RenderDrawPoint`.

3. Desenhe linhas usando a função `SDL_RenderDrawLines`.

## Submissão

Para submeter o seu trabalho, basta fazer o commit e o push das suas alterações no repositório que foi criado para
você no GitHub classroom.

```
git add .
git commit -m 'Submissão TP0'
git push
```

## Barema

- Parte 1: Instalação (0%)
- Parte 2: Um primeiro programa SDL (85%)
- Parte 3: Customização (15%)

## Referências

- Git: [https://git-scm.com/book/pt-br/v2](https://git-scm.com/book/pt-br/v2)
- Instalação da SDL: [https://lazyfoo.net/tutorials/SDL/01_hello_SDL/index.php](https://lazyfoo.net/tutorials/SDL/01_hello_SDL/index.php)