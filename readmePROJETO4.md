## Descrição do Projeto:

O projeto desenvolvido pelos alunos Arthur de Assis, Davi Henrique e Mateus Bosquine na linguagem C++ consiste em um sistema que simula um autocomplete de jogos. Nosso sistema busca títulos a partir de um prefixo (ignorando espaços e não diferenciando letras maiúsculas de minúsculas) e retorna até k resultados, ordenando-os primeiramente pela maior popularidade e, em caso de empate, por ordem alfabética. Utilizamos alocação estática para a base de dados, já a alocação dinâmica foi implementada na criação dos nós da Trie e na Lista Encadeada (Fila) usada para a busca da árvore em largura (BFS).

O coração do projeto está presente nas seguintes classes já definidas:

* `Game.hpp` que recebe os argumentos para criação da entidade de um jogo e seus atributos de título, descrição e popularidade.

  

* `Trie.hpp` que é o coração do sistema como um todo, tendo todos os métodos que gerenciam a inserção de chaves, navegação pelos nós, conversão e busca de prefixos.

  
  
  

## Instruções de Compilação

Para compilar o código, no arquivo `main.cpp` dentro da pasta com todos os outros arquivos, eu realizei meus testes do código com a seguinte inclusão no cabeçalho:

```
#include <iostream>
#include <vector>
#include "Trie.hpp"
#include "GamesDatabase.hpp"
#include "lista_encadeada.hpp"
```

  

Para que o código fosse compilado, utilize o seguinte código no terminal do `main.cpp` :
```
g++ main.cpp Game.cpp Trie.cpp GamesDatabase.cpp lista_encadeada.cpp -o app
```

* ##### g++: Compilador padrão de C++ .

* ##### main.cpp: Arquivo principal que inicializa a árvore e roda os testes.

* ##### Game.cpp Trie.cpp lista_encadeada.cpp GamesDatabase.cpp:  Arquivos que guardam toda a lógica do sistema e a base de dados.

* ##### -o: Sinalizador do sistema (output).

* ##### app: É o arquivo executável do main.cpp que nasce após todo o processo.

  
## Instruções de Execução

  
Por fim, para imprimir os resultados, o programa exige que os argumentos sejam passados direto na linha de comando (onde `k` é o número limite de resultados e `"prefixo"` é a busca). Utiliza-se o seguinte comando no terminal:



`Windows`:

```
.\app.exe k "prefixo"
```

 
`Linux/Mac`:

```
./app k "prefixo"
```

## Divisão dos arquivos na pasta do projeto

* `Game.hpp` Armazena toda estrutura da classe Game, com a definição do construtor, destrutor e seus métodos de impressão do título, popularidade e descrição.
  

* `Game.cpp` Define a lógica do que os métodos apresentados no `Game.hpp` devem fazer.
  

* `Trie.hpp` Armazena toda estrutura da classe Trie e TrieNode, com a definição da árvore, métodos de ordenação, autocomplete, inserção, verificação da existência de um título e etc.
  

* `Trie.cpp` Define a lógica do que os métodos apresentados no `Trie.hpp` devem fazer.


* `lista_encadeada.hpp` / `lista_encadeada.cpp` Definem a estrutura da Fila baseada em nós usada para varrer a árvore na busca por largura(BFS).


* `GamesDatabase.hpp` / `GamesDatabase.cpp` Base de dados fornecida com o catálogo estático de jogos.

  
* `main.cpp` Executa o driver code.
  


## Breve explicação de como executar os testes
 
Os testes do sistema foram implementados no arquivo `main.cpp` de forma sequencial (conforme o código teste enviado) e exigem a passagem de parâmetros via linha de comando para buscas dinâmicas.


### Passo 1: Compilação

Para executar os testes, deve-se compilar todos os arquivos do projeto juntos, com o seguinte comando no terminal:

  

```
g++ main.cpp Game.cpp Trie.cpp GamesDatabase.cpp lista_encadeada.cpp -o app
```
  

### Passo 2: Execução
Após a compilação gerar o executável, rode o programa passando a quantidade limite de jogos e o prefixo, com o comando:

`Linux/Mac`:
```
 ./app 10 "ca"
```
 
`Windows`: 
```
.\app.exe 10 "ca"
```

Ao rodar o executável, o console imprimirá as seguintes operações baseadas nos testes programados no arquivo principal:

**Carga de Dados:** O sistema inicializa a Trie iterando sobre `numberOfGames` e insere todos os jogos oriundos da base `GamesDatabase.cpp` na árvore de prefixos utilizando ponteiros.

**Busca Exata:** O sistema realiza um teste booleano acionando o método `contains` para verificar se o título exato "Castle Crashers" existe na árvore, imprimindo "Sim" ou "Não".

**Autocomplete e Busca em Largura (BFS):** O sistema executa a busca pelo prefixo designado, desce na estrutura da Trie e utiliza a estrutura da Lista Encadeada para recuperar os jogos válidos na subárvore.

**Ordenação e Relatório Final:** Após armazenar os jogos encontrados em um vetor, o sistema ordena os resultados por popularidade (e ordem alfabética em caso de empate) usando uma adaptação do algoritmo QuickSort, filtrando a quantidade limite `k` e imprimindo a tabela com o Título e a Popularidade de cada jogo encontrado.


## Exemplos de uso pela linha de comando

O sistema deve sempre receber os argumentos numéricos e textuais de forma estruturada. Caso o prefixo contenha espaços em branco, ele deve obrigatoriamente ser passado entre aspas.

**Exemplo 1: Busca simples (até 3 resultados)**
```bash
./app 3 ha
```
*Saída esperada:*
```text
Busca pelo prefixo ha
Título | Descrição | Popularidade
Hades | Roguelike de acao baseado na mitologia grega | 95
Half Life | FPS classico de ficcao cientifica | 92
Halo | FPS futurista com campanha e multiplayer | 85
```

**Exemplo 2: Busca ignorando espaços e case-sensitive**
```bash
./app 5 "half l"
```
*Saída esperada:*
```text
Busca pelo prefixo half l
Título | Descrição | Popularidade
Half Life | FPS classico de ficcao cientifica | 92
```

**Exemplo 3: Busca sem resultados**
```bash
./app 3 zelda
```
*Saída esperada:*
```text
Busca pelo prefixo zelda
No results found
```

**Exemplo 4: Chamada incorreta do sistema (falta de argumentos)**
```bash
./app 3
```
*Saída esperada:*
```text
Usage: ./app k prefix
```

