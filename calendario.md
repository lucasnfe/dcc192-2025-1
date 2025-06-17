---
layout: page
title: Calendário
description: Lista de módulos e tópicos do curso.
---

# Calendário

Calendário da disciplina com base na [[RESOLUÇÃO CEPE Nº 04/2024]](https://ufmg.br/storage/a/f/3/a/af3a8d2b58d73e8ae287c7f7ccb0d6a2_17324557300295_624904561.pdf):


<!-- {% for module in site.modules %}
{{ module }}
{% endfor %} -->

<table>
  <tr>
    <th>Semana</th>
    <th>Data</th>
    <th>Aulas</th>
    <th>Leituras</th>
    <th>Trabalhos</th>
  </tr>

  <!-- Semana 1 -->
  <tr>
    <td rowspan="2">1</td>
    <td>10/03</td>
    <td>1. Introdução<br><a href="{{ 'assets/slides/A01-introducao.pdf' | relative_url }}">[slides]</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>12/03</td>
    <td>2. SDL<br><a href="{{ 'assets/slides/A02-sdl.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Patterns:<br><a href="https://gameprogrammingpatterns.com/double-buffer.html">8. Double Buffer</a></td>
    <td rowspan="4">
    <a href="{{ '/avaliacoes/tp0-config-inicial' | relative_url }}">TP0: Setup</a>
    </td>
  </tr>

  <!-- Semana 2 -->
  <tr>
    <td rowspan="2">2</td>
    <td>17/03</td>
    <td><b>Atividades Complementares</b></td>
    <td></td>
  </tr>
  <tr>
    <td>19/03</td>
    <td>3. Eng. Soft.: Game Loop<br><a href="{{ 'assets/slides/A03-game-loop.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Patterns:<br><a href="https://gameprogrammingpatterns.com/game-loop.html">9. Game Loop</a></td>
  </tr>

  <!-- Semana 3 -->
  <tr>
    <td rowspan="2">3</td>
    <td>24/03</td>
    <td>4. Eng. Soft.: Game Objects<br><a href="{{ 'assets/slides/A04-game-objects.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Patterns:<br><a href="https://gameprogrammingpatterns.com/update-method.html">10. Update Method</a><br><a href="https://gameprogrammingpatterns.com/component.html">14. Component</a></td>
  </tr>
  <tr>
    <td>26/03</td>
    <td>5. Física: Vetores (Intro. TP1)<br><a href="{{ 'assets/slides/A05-vetores.pdf' | relative_url }}">[slides]</a></td>
    <td>The Nature of Code:<br><a href="https://natureofcode.com/vectors/">1. Vectors</a></td>
    <td rowspan="4">
      <a href="{{ '/avaliacoes/tp1-pong' | relative_url }}">TP1: Pong</a>
    </td>
  </tr>

  <!-- Semana 4 -->
  <tr>
    <td rowspan="2">4</td>
    <td>31/03</td>
    <td>6. Física: Objetos Rígidos<br><a href="{{ 'assets/slides/A06-rigid-bodies.pdf' | relative_url }}">[slides]</a></td>
    <td>The Nature of Code:<br><a href="https://natureofcode.com/forces/">2. Forces</a></td>
  </tr>
  <tr>
    <td>02/04</td>
    <td>7. Física: Colisão I<br><a href="{{ 'assets/slides/A07-colisaoI.pdf' | relative_url }}">[slides]</a></td>
    <td><a href="https://www.jeffreythompson.org/collision-detection/index.php">Jeff Thompson's Collision Detection Tutorial</a></td>
  </tr>

  <!-- Semana 5 -->
  <tr>
    <td rowspan="2">5</td>
    <td>07/04</td>
    <td>8. Física: Colisão II<br><a href="{{ 'assets/slides/A08-colisaoII.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Patterns:<br><a href="https://gameprogrammingpatterns.com/spatial-partition.html">20. Spatial Partition</a></td>
  </tr>
  <tr>
    <td>09/04</td>
    <td>9. Gráficos 2D: Partículas (Intro. TP2)<br><a href="{{ 'assets/slides/A09-particulas.pdf' | relative_url }}">[slides]</a></td>
    <td>The Nature of Code: <br><a href="https://natureofcode.com/particles/">4. Particle Systems</a><br>
    Game Prog. Patterns: <a href="https://gameprogrammingpatterns.com/object-pool.html">19. Object Pool</a></td>
    <td rowspan="4">
      <a href="{{ '/avaliacoes/tp2-asteroids' | relative_url }}">TP2: Asteroids</a>
    </td>
  </tr>

  <!-- Semana 6 -->
  <tr>
    <td rowspan="2">6</td>
    <td>14/04</td>
    <td>10. Gráficos 2D: Fundamentos<br><a href="{{ 'assets/slides/A10-graficos2d.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Alg. & Tech.: 2. 2D Graphics</td>
  </tr>
  <tr>
    <td>16/04</td>
    <td>11. Gráficos 2D: Interfaces<br><a href="{{ 'assets/slides/A11-interface.pdf' | relative_url }}">[slides]</a></td>
    <td>Lazy Foo' Productions:<a href="https://lazyfoo.net/articles/article06/index.php"> State Machines</a></td>
  </tr>

  <!-- Semana 7 -->
  <tr>
    <td rowspan="2">7</td>
    <td>21/04</td>
    <td><b>Feriado (Tiradentes)</b></td>
    <td></td>
  </tr>
  <tr>
    <td>23/04</td>
    <td>12. Game Design I</td>
    <td></td>
    <td rowspan="2">
      <a href="{{ '/avaliacoes/pf1-gdd' | relative_url }}">PF1: Game Design Document</a>
    </td>
  </tr>

  <!-- Semana 8 -->
  <tr>
    <td rowspan="2">8</td>
    <td>28/04</td>
    <td>13. Game Design II</td>
    <td></td>
  </tr>
  <tr>
    <td>30/04</td>
    <td>14. Gráficos 2D: Câmeras (Intro. TP3)<br><a href="{{ 'assets/slides/A14-cameras2d.pdf' | relative_url }}">[slides]</a></td>
    <td><a href='https://www.gamedeveloper.com/design/scroll-back-the-theory-and-practice-of-cameras-in-side-scrollers'>Scroll Back: The Theory and Practice of Cameras in Side-Scrollers</a></td>
    <td></td>
  </tr> 

  <!-- Semana 9 -->
  <tr>
    <td rowspan="2">9</td>
    <td>05/05</td>
    <td>15. Áudio: síntese<br><a href="{{ 'assets/slides/A15-audio-synth.pdf' | relative_url }}">[slides]</a></td>
    <td>The Pudding: <a href="https://pudding.cool/2018/02/waveforms/">Waveforms</a></td>
    <td rowspan="4">
      <a href="{{ '/avaliacoes/tp3-smb' | relative_url }}">TP3: Super Mario Bros 1-1</a>
    </td>
  </tr>
  
  <tr>
    <td>07/05</td>
    <td>16. Áudio: reprodução<br><a href="{{ 'assets/slides/A16-audio-system.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Alg. & Tech.: 6. Sound</td>
  </tr> 

  <!-- Semana 10 -->
  <tr>
    <td rowspan="2">10</td>
    <td>12/05</td>
    <td>17. Áudio: Composição I</td>
    <td><a href="https://www.musictheory.net/lessons">MusicTheory.net: Lessons</a></td>
  </tr>
  <tr>
    <td>14/05</td>
    <td>17. Áudio: Composição II</td>
    <td><a href="https://www.youtube.com/watch?v=dMkTdYmOgiQ&t=88s&ab_channel=Zectro">Zectro: A Guide to Making Video Game Music</a></td>
  </tr>

  <!-- Semana 11 -->
  <tr>
    <td rowspan="2">11</td>
    <td>19/05</td>
    <td>18. Gráficos 2D: HUD (Intro TP4)<br><a href="{{ 'assets/slides/A18-hud.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Alg. & Tech.: 10. User Interfaces</td>
    <td></td>
  </tr>
  <tr>
    <td>21/05</td>
    <td>19. IA: Modelagem de Comportamento<br><a href="{{ 'assets/slides/A19-ia1-behavior.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Prog. Alg. & Tech.: 9. Artificial Intelligence (State-Based Behaviors)</td>
    <td></td>
  </tr>

  <!-- Semana 12 -->
  <tr>
    <td rowspan="2">12</td>
    <td>26/05</td>
    <td>20. IA: Pathfinding I<br><a href="{{ 'assets/slides/A20-ia2-pathfindingI.pdf' | relative_url }}">[slides]</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>28/05</td>
    <td>21. IA: Pathfinding II<br><a href="{{ 'assets/slides/A21-ia2-pathfinding2.pdf' | relative_url }}">[slides]</a></td>
    <td>Red Blob Games: <a href="https://www.redblobgames.com/pathfinding/a-star/introduction.html">Introduction to the A* Algorithm</a></td>
    <td></td>
  </tr> 

  <!-- Semana 13 -->
  <tr>
    <td rowspan="2">13</td>
    <td>02/06</td>
    <td>22. IA: Steering Behaviors<br><a href="{{ 'assets/slides/A22-ia3-steering.pdf' | relative_url }}">[slides]</a></td>
    <td>The Nature of Code:<br><a href="https://natureofcode.com/autonomous-agents/">5. Autonomous Agents</a></td>
    <td rowspan="4">
      <a href="{{ '/avaliacoes/tp4-smb2' | relative_url }}">TP4: Super Mario Bros 1-2</a>
    </td>
  </tr>
  <tr>
    <td>04/06</td>
    <td>23. IA: Procedural Content Generation<br><a href="{{ 'assets/slides/A23-ia4-pcg.pdf' | relative_url }}">[slides]</a></td>
    <td>Kate Compton's GDC Talk: <a href="https://www.youtube.com/watch?v=WumyfLEa6bU&ab_channel=GameDevelopersConference">Practical Procedural Generation for Everyone</a></td>
  </tr>

  <!-- Semana 14 -->
  <tr>
    <td rowspan="2">14</td>
    <td>09/06</td>
    <td>24. Narrativas: Cutscenes<br><a href="{{ 'assets/slides/A24-narratives-cutscene.pdf' | relative_url }}">[slides]</a></td>
    <td></td>
  </tr>
  <tr>
    <td>11/06</td>
    <td>25. Narrativas: Quests<br><a href="{{ 'assets/slides/A25-narratives-quests.pdf' | relative_url }}">[slides]</a></td>
    <td>Leszek Szczepanski's GDC Talk: <a href="https://www.youtube.com/watch?v=ykPZcG8_mPU&ab_channel=GameDevelopersConference">Building Non-Linear Narratives in Horizon: Zero Dawn</a></td>
  </tr> 

  <!-- Semana 15 -->
  <tr>
    <td rowspan="2">15</td>
    <td>16/06</td>
    <td>26. Gráficos 3D: Fundamentos<br><a href="{{ 'assets/slides/A26-graphics1.pdf' | relative_url }}">[slides]</a></td>
    <td>Game Engine Architecture: 10. The Rendering Engine (pgs. 443-453) </td>
    <td rowspan="4">
      PF2: Prototipação
    </td>
  </tr>
  <tr>
    <td>18/06</td>
    <td>27. Gráficos 3D: Modelos e Transformações</td>
    <td></td>
  </tr> 

  <!-- Semana 16 -->
  <tr>
    <td rowspan="2">16</td>
    <td>23/06</td>
    <td>28. Gráficos 3D: Iluminação</td>
    <td></td>
  </tr>
  <tr>
    <td>25/06</td>
    <td><b>Atividades Complementares</b></td>
    <td></td>
  </tr> 

  <!-- Semana 17 -->
  <tr>
    <td rowspan="2">17</td>
    <td>30/06</td>
    <td>29. Gráficos 3D: Shaders</td>
    <td></td>
    <td rowspan="2">
      PF3: Playtest & Finalização
    </td>
  </tr>
  <tr>
    <td>02/07</td>
    <td>30. Conclusão</td>
    <td></td>
  </tr>

  <!-- Semana 18 -->
  <tr>
    <td rowspan="2">18</td>
    <td>07/07</td>
    <td><b>Apresentação dos Trabalhos Finais</b></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>09/07</td>
    <td><b>Apresentação dos Trabalhos Finais</b></td>
    <td></td>
    <td></td>
  </tr>

</table>
