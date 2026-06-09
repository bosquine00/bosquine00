Descrição do Projeto:

O projeto desenvolvido pelos alunos [Seu Nome e Nome da Dupla] consiste em um sistema desenvolvido na linguagem C++ que simula um autocomplete de jogos. Nosso sistema busca títulos a partir de um prefixo (ignorando espaços e não diferenciando letras maiúsculas de minúsculas) e retorna até k resultados, ordenando-os primeiramente pela maior popularidade e, em caso de empate, por ordem alfabética. Utilizamos alocação estática para a base de dados (que não instancia novos jogos dinamicamente) e uma alocação dinâmica guiada por uma Fila customizada (Lista Encadeada) para a exploração da árvore em largura (BFS) e criação dos nós da Trie.
O coração do projeto está presente nas seguintes classes:
Game.hpp que recebe os argumentos para criação da entidade de um jogo e seus atributos (título, descrição e popularidade).
Trie.hpp que é o coração do sistema como um todo, tendo todos os métodos que gerenciam a inserção de chaves, navegação pelos nós e busca de prefixos.

Instruções de Compilação

Para compilar o código, no arquivo main.cpp dentro da pasta com todos os outros arquivos, eu realizei meus testes do código com a seguinte inclusão no cabeçalho:
#include <iostream>
#include <vector>
#include "Trie.hpp"
#include "GamesDatabase.hpp"
#include "lista_encadeada.hpp"

Para que o código fosse compilado, utilize o seguinte comando no terminal na mesma pasta do main.cpp:
g++ main.cpp Game.cpp Trie.cpp GamesDatabase.cpp lista_encadeada.cpp -o app

g++: Compilador padrão de C++.

main.cpp Game.cpp Trie.cpp GamesDatabase.cpp lista_encadeada.cpp: Arquivos que criam a estrutura da árvore, as listas de busca e rodam a lógica e os testes.

-o: Sinalizador do sistema (output).

app: É o arquivo executável gerado após todo o processo de compilação.

Instruções de Execução

Por fim, para imprimir os resultados, o programa exige que você passe os argumentos direto na linha de comando (onde `k` é o número de resultados e `"prefixo"` é a busca). Utilize o seguinte comando no terminal:

Windows:
.\app.exe k "prefixo"

Linux/Mac:
./app k "prefixo"

Divisão dos arquivos na pasta do projeto

Game.hpp Armazena toda a estrutura da classe Game, com a definição do construtor, destrutor e os métodos getters.
Game.cpp Define a lógica do que os métodos apresentados no Game.hpp devem fazer.
Trie.hpp Armazena toda a estrutura da classe Trie e TrieNode, com a definição da árvore, métodos de conversão de chave, inserção, ordenação (QuickSort adaptado) e busca de autocomplete.
Trie.cpp Define a lógica do que os métodos apresentados no Trie.hpp devem fazer.
lista_encadeada.hpp Armazena a estrutura de Nós e da Lista Encadeada (Fila) usada para varrer a árvore na busca por largura.
lista_encadeada.cpp Define o funcionamento da lista, inserções e remoções de nós.
GamesDatabase.hpp e GamesDatabase.cpp Arquivos fornecidos contendo o catálogo de jogos armazenados de forma estática.
main.cpp Executa o driver code e os testes de sistema.

Breve explicação de como executar os testes

Os testes do sistema foram implementados no arquivo main.cpp e exigem a passagem de parâmetros via linha de comando (embora no teste de código inicial tenham sido executados de forma sequencial automatizada).

Passo 1: Compilação

Para executar os testes, deve-se compilar todos os arquivos do projeto juntos, com o seguinte comando no terminal:
g++ main.cpp Game.cpp Trie.cpp GamesDatabase.cpp lista_encadeada.cpp -o app

Passo 2: Execução

Após a compilação gerar o executável, rode o programa passando a quantidade limite de jogos e o que você deseja pesquisar. Exemplo buscando até 10 jogos com o prefixo "ca":

Linux/Mac:
 ./app 10 "ca"

Windows:
.\app.exe 10 "ca"

Ao rodar o executável (conforme configurado na nossa `main`), o console imprimirá as seguintes operações:
Carga de Dados: O sistema inicializa a Trie e insere todos os jogos oriundos do arquivo GamesDatabase.cpp usando ponteiros.
Busca Exata: O sistema realiza um teste do método `contains` buscando o título "Castle Crashers" na árvore, ignorando espaços e cases.
Autocomplete e Ordenação: O sistema executa a busca pelo prefixo designado, desce na estrutura da Trie para recuperar a subárvore usando a Lista Encadeada, ordena os jogos encontrados pelo algoritmo QuickSort customizado (popularidade e ordem alfabética) e imprime a tabela final no console.