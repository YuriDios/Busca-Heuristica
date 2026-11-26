# Busca Heurística e Resolução de Problemas

**Grupo 4** — Busca informada, heurísticas, Busca Gulosa (*Greedy Best-First Search*) e A*.

Este repositório reúne os materiais da apresentação:

| Arquivo | Descrição |
|---|---|
| `Busca_heuristica.pdf` | Slides da apresentação |
| `busca_romenia.html` | Demonstração interativa: Busca Gulosa e A* no mapa da Romênia |

## Demonstração interativa

O arquivo `busca_romenia.html` é uma página única, sem dependências. Para usar, basta abri-la em qualquer navegador.

O problema é ir de **Arad** até **Bucharest** no mapa da Romênia (Russell & Norvig). As estradas têm distâncias em km, e a heurística h(n) é a distância em linha reta até Bucharest.

**Controles**

- **Busca gulosa** e **A\***: executam o algoritmo passo a passo no mapa.
- **Limpar**: reinicia a demonstração.
- **Velocidade**: ajusta o ritmo da animação.

**Legenda do mapa**

- Laranja: nó sendo expandido
- Amarelo: fronteira
- Cinza: já expandido
- Vermelho: caminho escolhido

Abaixo do mapa, um log mostra g, h e f de cada expansão, e ao final os dois resultados são comparados.

## Conceitos

A função de avaliação f(n) ordena a fronteira pelo menor valor. O que muda entre os algoritmos é a definição de f(n):

| Algoritmo | f(n) | Observação |
|---|---|---|
| Custo uniforme | g(n) | Só o custo acumulado |
| Busca gulosa | h(n) | Só a estimativa até o objetivo |
| A* | g(n) + h(n) | Custo acumulado mais estimativa restante |

- **g(n)**: custo acumulado do início até n
- **h(n)**: estimativa do custo de n até o objetivo
- **Fronteira**: nós gerados e ainda não expandidos

## Resultados (Arad → Bucharest)

| | Busca gulosa | A* |
|---|---|---|
| Caminho | Arad → Sibiu → Fagaras → Bucharest | Arad → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest |
| Distância | 450 km | 418 km |
| Nós expandidos | 4 | 6 |

A gulosa escolhe Fagaras em Sibiu porque h = 176 é menor que o de Rimnicu Vilcea (193), mas ignora o custo já gasto e termina com um caminho 32 km mais longo. O A* compara f = g + h (413 contra 415) e encontra o caminho ótimo.

## Propriedades

- **Busca gulosa**: não é completa (pode ficar presa) e não é ótima.
- **A***: é ótimo quando a heurística é admissível, isto é, nunca superestima o custo real. A distância em linha reta cumpre isso no mapa da Romênia. O preço é o uso de memória, que cresce de forma exponencial; variantes como IDA*, RBFS e SMA* reduzem esse problema.

## Referência

RUSSELL, S.; NORVIG, P. *Inteligência Artificial*. Mapa da Romênia e heurística de distância em linha reta até Bucharest.
