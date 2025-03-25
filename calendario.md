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
    <th>Seamana</th>
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
    <td>2. Lab 0: SDL<br><a href="{{ 'assets/slides/A02-sdl.pdf' | relative_url }}">[slides]</a></td>
    <td><a href="https://gameprogrammingpatterns.com/double-buffer.html">Game Prog. Patterns, 8. Double Buffer</a></td>
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
    <td>3. Eng Soft: Game Loop<br><a href="{{ 'assets/slides/A03-game-loop.pdf' | relative_url }}">[slides]</a></td>
    <td><a href="https://gameprogrammingpatterns.com/game-loop.html">Game Prog. Patterns, 9. Game Loop</a></td>
  </tr>

  <!-- Semana 3 -->
  <tr>
    <td rowspan="2">3</td>
    <td>24/03</td>
    <td>4. Eng Soft: Game Objects<br><a href="{{ 'assets/slides/A04-game-objects.pdf' | relative_url }}">[slides]</a></td>
    <td><a href="https://gameprogrammingpatterns.com/update-method.html">Game Prog. Patterns, 10. Update Method</a><br><a href="https://gameprogrammingpatterns.com/component.html">Game Prog. Patterns, 14. Component</a></td>
  </tr>
  <tr>
    <td>26/03</td>
    <td>5. Lab 1: Pong</td>
    <td></td>
    <td rowspan="4">
      TP1: Pong
    </td>
  </tr>

  <!-- Semana 4 -->
  <tr>
    <td rowspan="2">4</td>
    <td>31/03</td>
    <td>6. Física: Forças/Objetos Rígidos</td>
    <td></td>
  </tr>
  <tr>
    <td>02/04</td>
    <td>7. Física: Detecção de Colisão</td>
    <td></td>
  </tr>

  <!-- Semana 5 -->
  <tr>
    <td rowspan="2">5</td>
    <td>07/04</td>
    <td>8. Gráficos 2D: Bitmaps, Sprites e Tilemap</td>
    <td></td>
  </tr>
  <tr>
    <td>09/04</td>
    <td>9. Lab 2: Asteroids</td>
    <td></td>
    <td rowspan="4">
      TP2: Asteroids
    </td>
  </tr>

  <!-- Semana 6 -->
  <tr>
    <td rowspan="2">6</td>
    <td>14/04</td>
    <td>10. Gráficos 2D: Sistema de Partículas</td>
    <td></td>
  </tr>
  <tr>
    <td>16/04</td>
    <td>11. Gráficos 2D: Câmeras e Animação</td>
    <td></td>
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
    <td>12. Game Design: Fundamentos</td>
    <td></td>
    <td rowspan="2">
      PF1: Game Design Document
    </td>
  </tr>

  <!-- Semana 8 -->
  <tr>
    <td rowspan="2">8</td>
    <td>28/04</td>
    <td>13. Física: Resolução de Colisão</td>
    <td></td>
  </tr>
  <tr>
    <td>30/04</td>
    <td>14. Lab 3: Super Mario Bros</td>
    <td></td>
    <td rowspan="4">
      TP3: Super Mario Bros 1-1
    </td>
  </tr> 

  <!-- Semana 9 -->
  <tr>
    <td rowspan="2">9</td>
    <td>05/05</td>
    <td>15. Gráficos 3D: Pipeline Gráfico</td>
    <td></td>
  </tr>
  <tr>
    <td>07/05</td>
    <td>16. Gráficos 3D: Objetos 3D</td>
    <td></td>
  </tr> 

  <!-- Semana 10 -->
  <tr>
    <td rowspan="2">10</td>
    <td>12/05</td>
    <td>17. Gráficos 3D: Transformações</td>
    <td></td>
  </tr>
  <tr>
    <td>14/05</td>
    <td>18. Lab 4: Star Fox</td>
    <td></td>
    <td rowspan="4">
      TP4: Star Fox Tunel
    </td>
  </tr>

  <!-- Semana 11 -->
  <tr>
    <td rowspan="2">11</td>
    <td>19/05</td>
    <td>29. Gráficos 3D: Cores e Texturas</td>
    <td></td>
  </tr>
  <tr>
    <td>21/05</td>
    <td>20. Gráficos 3D: Shaders</td>
    <td></td>
  </tr>

  <!-- Semana 12 -->
  <tr>
    <td rowspan="2">12</td>
    <td>26/05</td>
    <td>21. Gráficos 3D: Visibilidade</td>
    <td></td>
  </tr>
  <tr>
    <td>28/05</td>
    <td>22. IA: Máquinas de Estados Finitos</td>
    <td></td>
    <td rowspan="7">
      TP3: Prototipação
    </td>
  </tr> 

  <!-- Semana 13 -->
  <tr>
    <td rowspan="2">13</td>
    <td>02/06</td>
    <td>23. IA: Pathfinding</td>
    <td></td>
  </tr>
  <tr>
    <td>04/06</td>
    <td>24. IA: Game Playing</td>
    <td></td>
  </tr>

  <!-- Semana 14 -->
  <tr>
    <td rowspan="2">14</td>
    <td>09/06</td>
    <td>25. IA: Procedural Content Generation</td>
    <td></td>
  </tr>
  <tr>
    <td>11/06</td>
    <td>26. Áudio: representações</td>
    <td></td>
  </tr> 

  <!-- Semana 15 -->
  <tr>
    <td rowspan="2">15</td>
    <td>16/06</td>
    <td>27. Áudio: síntese</td>
    <td></td>
  </tr>
  <tr>
    <td>18/06</td>
    <td>28. Áudio: sequenciamento</td>
    <td></td>
  </tr> 

  <!-- Semana 16 -->
  <tr>
    <td rowspan="2">16</td>
    <td>23/06</td>
    <td><b>Playtesting</b></td>
    <td></td>
    <td>PF3: Playtesting</td>
  </tr>
  <tr>
    <td>25/06</td>
    <td><b>Atividades Complementares</b></td>
    <td></td>
    <td rowspan="3">
      TP3: Finalização
    </td>
  </tr> 

  <!-- Semana 17 -->
  <tr>
    <td rowspan="2">17</td>
    <td>30/06</td>
    <td>30. Eng Soft: Debug & Teste</td>
    <td></td>
  </tr>
  <tr>
    <td>02/07</td>
    <td>31. Conclusão</td>
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
