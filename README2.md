## Descrição do Projeto:

O projeto desenvolvido pelos alunos Arthur de Assis, Davi Henrique e Mateus Bosquine na linguagem C++ consiste em um sistema desenvolvido na linguagem C++ que simula o matchmaking de um jogo online. Nosso sistema ordena pelo score e timestamp dos jogadores, insere, retira, realoca e imprime todos os grupos com jogadores. Utilizamos arrays de tamanho fixo para alocação estática, já a alocação dinâmica foi implementada no merge, mergeSort, formGroup e getWaitingPlayer. 

O coração do projeto está presente nas seguintes classes já definidas pelo professor:

* `Player.hpp` que recebe os argumentos para criação de um player e implementá-lo ao sistema de organização

  

* `Matchmaking.hpp` que é o coração do sistema como um todo, tendo todos os métodos que gerenciam as filas e grupos de partida

  
  
  

## Instruções de Compilação

Para compilar o código, no arquivo `main.cpp` dentro da pasta com todos os outrs arquivos, eu realizei meus testes do código com a seguinte inclusão no cabeçalho:

```
#include <iostream>
#include "Player.hpp"
#include "Matchmaking.hpp"
#include <chrono>
using namespace std;
using namespace std::chrono;
```

  

Para que o código fosse compilado, utilize o seguinte código no terminal do `main.cpp` :
```
g++ main.cpp Matchmaking.cpp Player.cpp -o matchmaking
```

* ##### g++: Compildor padrão de C++ .

* ##### main.cpp: Arquivo que cria todas as disciplinas e roda os testes.

* ##### Matchmaking.cpp Player.cpp:  Arquivos que guardam toda a lógica do sistema .

* ##### -o: Sinalizador do sistema (output).

* ##### matchmaking: É o arquivo executável do main.cpp que nasce após todo o processo.

  
## Instruções de Execução

  
Por fim, para imprimir os resultados, utilize o seguinte comando no terminal:



`Windows`:

```
.\matchmaking.exe
```

 
`Linux/Mac`:

```
./matchmaking
```

## Divisão dos arquivos na pasta do projeto

* `Player.hpp` Armazena toda estrutura da classe Player, com a definição do construtor, destrutor e seus outros métodos.
  

* `Player.cpp` Define a lógica do que os métodos apresentados no `Player.hpp` devem fazer.
  

* `Matchmaking.hpp` Armazena toda estrutura da classe Matchmaking, com a definição do construtor, destrutor e seus outros métodos de gerenciamento.
  

* `Matchmaking.cpp` Define a lógica do que os métodos apresentados no `Matchmaking.hpp` devem fazer.

  
* `main.cpp` Executa o driver code.
  


## Breve explicação de como executar os testes
 
Os testes do sistema foram implementados diretamente no arquivo `main.cpp` de forma sequencial e automatizada. Não é necessário que o usuário insira dados manualmente durante a execução,.


### Passo 1: Compilação

Para executar os testes, deve-se compilar todos os arquivos do projeto juntos, com o seguinte comando no terminal:

  

```bash
g++ main.cpp Player.cpp Matchmaking.cpp -o testes_matchmaking
````
  

### Passo 2: Execução
Após a compilação gerar o executável, rode o programa com o comando:

`Linux/Mac`:
```
 ./testes_matchmaking
```
 
`Windows`: 
```
testes_matchmaking.exe
```

Ao rodar o executável, o console imprimirá as seguintes operações:

**Inserção e Remoção:** O sistema cria 6 jogadores fictícios, insere alguns na fila de espera, imprime a fila, remove um jogador específico pelo ID e insere outro.

**Teste do Insertion Sort:** O sistema executa a ordenação por inserção, mede o tempo gasto em microssegundos (usando a biblioteca <chrono>) e imprime a fila ordenada.

**Teste do Merge Sort:** A fila é modificada novamente e o sistema executa a ordenação por intercalação (Merge Sort), também medindo o tempo e imprimindo o resultado.

**Formação de Grupos:** O sistema tenta formar um grupo válido de 2 jogadores (com diferença máxima de score de 100) e imprime os integrantes. Em seguida, tenta formar um grupo impossível de 3 jogadores, testando o tratamento de erro (retornando nulo).

**Relatório Final:** Ao final, o programa exibe quais jogadores sobraram na fila de espera e imprime o comparativo de tempo gasto pelos dois algoritmos de ordenação.