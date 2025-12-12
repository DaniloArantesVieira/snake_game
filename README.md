# 🐍 Snake Game - Graph Theory Implementation

> Uma reinterpretação do clássico jogo da cobrinha (Snake), onde o tabuleiro e a movimentação são gerenciados através de **Estruturas de Dados** e **Teoria dos Grafos**, em vez de validações matriciais simples.

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=CONCLUIDO&color=GREEN&style=for-the-badge)
![Badge Python](http://img.shields.io/static/v1?label=LINGUAGEM&message=PYTHON&color=blue&style=for-the-badge)
![Badge Pygame](http://img.shields.io/static/v1?label=LIB&message=PYGAME&color=red&style=for-the-badge)

## 🧠 O Conceito (Graph Theory)

Diferente da maioria dos jogos Snake que utilizam matrizes 2D simples (`matrix[x][y]`), este projeto modela o tabuleiro como um **Grid Graph** (Grafo em Grade).

### Estrutura Lógica
* **Vértices (Nós):** Cada célula do tabuleiro (30x30px) é um vértice único.
* **Arestas (Conexões):** A movimentação só é permitida se existir uma **aresta** conectando o vértice atual ao próximo.
* **Mapeamento:** O grid 2D é linearizado para IDs inteiros usando a fórmula: $ID = (y \times Width) + x$.

### Por que isso é interessante?
Ao usar grafos, a lógica de colisão ("bater na parede") torna-se uma questão de conectividade topológica. Se quisermos criar um labirinto ou obstáculos internos, basta **remover a aresta** entre dois nós, e a cobra entenderá automaticamente que aquele caminho está bloqueado, sem alterar o código de movimentação.

```python
# Exemplo da lógica de validação no código:
# Em vez de verificar coordenadas (if x > width), verificamos a conexão:

if graph.has_edge(posicao_atual, proxima_posicao):
    mover_cobra()
else:
    game_over()
