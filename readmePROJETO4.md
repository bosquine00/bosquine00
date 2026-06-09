## Descrição do Projeto:

O projeto desenvolvido pelos alunos [Seu Nome e Nome da Dupla] na linguagem C++ consiste em um sistema que simula um autocomplete de jogos. Nosso sistema busca títulos a partir de um prefixo (ignorando espaços e não diferenciando letras maiúsculas de minúsculas) e retorna até k resultados, ordenando-os primeiramente pela maior popularidade e, em caso de empate, por ordem alfabética. Utilizamos alocação estática para a base de dados, já a alocação dinâmica foi implementada na criação dos nós da Trie e na Lista Encadeada (Fila) usada para a exploração da árvore em largura (BFS).

O coração do projeto está presente nas seguintes classes já definidas:

* `Game.hpp` que recebe os argumentos para criação da entidade de um jogo e seus atributos de título, descrição e popularidade.

  

* `Trie.hpp` que é o coração do sistema como um todo, tendo todos os métodos que gerenciam a inserção de chaves, navegação pelos nós, conversão e busca de prefixos.

  
  
  

## Instruções de Compilação

Para compilar o código, no arquivo `main.cpp` dentro da pasta com todos os outros arquivos, eu realizei meus testes do código com a seguinte inclusão no cabeçalho:

```cpp
#include <iostream>
#include <vector>
#include "Trie.hpp"
#include "GamesDatabase.hpp"
#include "lista_encadeada.hpp"
