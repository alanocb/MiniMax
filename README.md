![image](https://github.com/alanocb/MiniMax/assets/99679262/f2c1e5d8-90fe-448d-b427-4630d6a2db37)

# Inteligência Artificial - Mini Projeto MiniMax

**Alano Baptista - 20190818 | Luquenia Galiano - 20210451 | 27/10/2023**

## Introdução

Os computadores têm a habilidade em determinar o próximo melhor passo em jogos como o Jogo do Galo, Damas e Xadrez. Mas como é possível? Um dos algoritmos mais cruciais é o minimax, uma abordagem geral para jogos adversáriais, nos quais você e seu oponente têm objetivos opostos. Este pretende escolher a jogada ótima mesmo no pior cenário possível, considerando que o oponente também está jogando de forma otimizada. Optar pela jogada mais vantajosa não se resume a simplesmente escolher uma que nos levará à vitória, mas sim a selecionar uma jogada que nos assegure o melhor resultado, mesmo se o oponente escolher a melhor jogada.

O algoritmo minimax é um programa recursivo desenvolvido para encontrar a estratégia de jogo mais eficaz, reduzindo ao máximo as chances de perder e maximizar as oportunidades de vencer. Visualmente, podemos representar o minimax como uma exploração dos nós de uma árvore de possibilidades do jogo para descobrir a melhor jogada a ser feita. Nesse caso, o nó raiz da árvore é o estado atual do jogo onde o algoritmo minimax é iniciado.

O nosso foco é utilizar o minimax para criar uma inteligência artificial imbatível para o jogo do galo. No entanto, também é possível aplicá-lo a jogos complexos, como xadrez, damas e até aplicá-lo em métodos de negociações. Geralmente o jogador que inicia o uso do minimax é chamado de jogador maximizador. Em outras palavras, é aquele que busca maximizar suas chances de vitória no jogo. Por outro lado, o oponente do jogador maximizador é chamado de jogador minimizador. Dessa forma, o jogador minimizador é aquele que as chances de vitória precisam ser minimizadas.

## Pruning

O "pruning" em minimax refere-se a uma técnica que otimiza o processo de busca na árvore de possibilidades do jogo. Eliminando certos ramos da árvore que não são relevantes para a decisão final, reduzindo significativamente a quantidade de cálculos necessários. Existem dois tipos principais de pruning em minimax: alpha-beta pruning e delta pruning. Ambos ajudam a economizar recursos computacionais, tornando o algoritmo mais eficiente e capaz de lidar com jogos complexos em tempo hábil.

### Alpha e beta

No contexto do algoritmo minimax, o "alpha" e o "beta" são valores que representam os limites inferiores e superiores de avaliação de um nó na árvore de possibilidades do jogo.

- **Alpha**: É o limite inferior que representa a melhor avaliação atual para o jogador maximizador. Ou seja, é o valor mínimo que o jogador maximizador sabe que pode alcançar até o momento.
- **Beta**: Representa o limite superior que representa a melhor avaliação atual para o jogador minimizador. É o valor máximo que o jogador minimizador sabe que pode alcançar até o momento.
- Geralmente, esses valores são inicializados com -infinito para o alpha e +infinito para o beta. Isso é feito para garantir que qualquer valor encontrado durante a busca na árvore será melhor do que os valores iniciais.

![image](https://github.com/alanocb/MiniMax/assets/99679262/b09b56ff-eac5-4bb3-8759-38dc8716f7a3)

![image](https://github.com/alanocb/MiniMax/assets/99679262/799e2a8e-9827-4934-a424-938a1f84e40d)


Nas imagens fornecidas, temos um exemplo ilustrativo do processo de pruning no contexto do algoritmo minimax.

## Jogo do Galo

No nosso caso utilizamos o jogo do galo, como o jogo tem relativamente poucas opções o algoritmo pode visualizar todas as opções até chegar a um terminal state e escolher aquela que garante melhor chances para vencer, o terminal state será e um estado final onde alguém terá vencido ou ouve um empate.

No Jogo do Galo, isso ocorre quando X ou O têm 3 marcações consecutivas, ou quando não há mais jogadas disponíveis, resultando em empate. Podemos atribuir um valor a cada estado terminal para que o algoritmo reconheça o objetivo. Por exemplo, podemos dar o valor de 1 para um estado onde X ganha, 0 para um empate e -1 se O ganha.

A partir dai os valores serão passados recursivamente entre o estado de max e estados de min até chegar ao ponto atual para tomar a melhor jogada possível. Aqui está uma representação do funcionamento do algoritmo no jogo do galo, começamos no estado atual, que é o nó isolado. Temos três opções de jogada.

![image](https://github.com/alanocb/MiniMax/assets/99679262/3c5d0c54-1c24-44db-bb2b-34dfcbceddba)

O algoritmo tenta primeiro o nó da esquerda. No entanto, ao colocar um "X" na próxima jogada, na jogada seguinte o adversário colocando um "O" em qualquer uma das posições, resultará na sua vitória, retornando um valor de -1.

No nó do meio, ao colocarmos um "X", garantimos nossa vitória, o que resulta em um retorno de 1.

No último caso, após colocarmos um "X", o adversário tem duas opções: uma em que nada acontece e outra em que ele se torna o vencedor. Caso escolha a opção em que nada acontece, garantimos nossa vitória. No entanto, o algoritmo nunca escolherá esse caminho, pois precisamos minimizar o estado. Portanto, o adversário sairá vencedor neste caminho, retornando um valor de -1.

O único caminho em que ganhamos, independentemente da escolha do adversário, é o caminho do meio, logo este será escolhido pelo minimax.

## Minimax em Negociação e Política

Na arena da negociação e política, ambas as partes têm um objetivo comum, buscar o melhor resultado para si mesmas. Nesse contexto, o algoritmo Minimax surge como uma ferramenta valiosa. Ao avaliar as opções com base em determinadas heurísticas, ele determina o valor ótimo, buscando equilibrar os interesses de ambas as partes e alcançar um resultado favorável para todos os envolvidos.

Ao considerar o contexto da negociação, é crucial notar que, sem a aplicação do algoritmo Minimax, o negociador mais habilidoso tende a maximizar seus próprios ganhos. No entanto, o Minimax visa remover esse fator, priorizando uma abordagem equitativa. A heurística utilizada deve incorporar elementos cruciais como a demanda e a oferta, garantindo que as negociações sejam conduzidas de maneira justa e equilibrada, visando o benefício mútuo das partes envolvidas.

Em cenários de negociação política, é importante ressaltar que especialmente em situações de conflito, a definição de uma heurística relacionada ao bem-estar das pessoas pode levantar questões éticas complexas. A busca pelo melhor resultado muitas vezes enfrenta dilemas morais, exigindo uma reflexão cuidadosa sobre os princípios éticos envolvidos.

## Conclusão

Em resumo, o algoritmo minimax se revela uma ferramenta poderosa não apenas para a criação de inteligências artificiais imbatíveis em jogos como o jogo do galo, mas também para a tomada de decisões em contextos mais amplos. Ao permitir que o jogador maximize suas chances de vitória enquanto minimiza as do oponente, o minimax demonstra sua utilidade em situações em que a escolha do melhor resultado é crucial, enfrentando adversários e incertezas de maneira estratégica e eficaz. Dessa forma, torna-se uma valiosa abordagem na busca pela excelência em estratégias de jogo e em tomadas de decisões estratégicas em diversos cenários.

## Bibliografia

- [FreeCodeCamp - Minimax Algorithm Guide](https://www.freecodecamp.org/news/minimax-algorithm-guide-how-to-create-anunbeatable-ai/)
- [YouTube - Minimax Algorithm Tutorial](https://www.youtube.com/watch?v=P2TcQ3h0ipQ&list=WL&index=13&ab_channel=freeCodeCamp.org)
- [YouTube - Alpha-Beta Pruning](https://www.youtube.com/watch?v=SLgZhpDsrfc&ab_channel=SpanningTree)
- [OpenAI Chat](https://chat.openai.com)
