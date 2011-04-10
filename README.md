Estrutura do diretório
======================

* `config.yml` --- Esse arquivo contém as configurações de tempo, 
  memória, origem e etc. Por exemplo:
      
      name:         'teste'
      time_limit:   1
      memory_limit: 256
      source:       'Olimpíada Brasileira de Informática > 2000'

* `checkers/` --- Os scripts desta pasta que verificam a entrada devem 
  receber dois parâmetros `INPUT_PATH` e `TAG_PATH`, onde `FILE_PATH` é 
  o caminho absoluto para o arquivo que estamos verificando e `TAG_PATH` 
  é o caminho absoluto para o arquivo que contém uma tag indicando o 
  tipo de teste. Já os scripts que verificam a saída devem receber três 
  parâmetros `INPUT_PATH`, `OUTPUT_PATH` e `TAG_PATH`.
  
  Suponha que seu problema possui uma divisão dos casos de teste. Para os
  casos `tests/1` e `tests/2` uma restrição é X, para os casos `tests/2`,
  `tests/3`, ... a restrição é Y. Neste caso, o responsável por gerar os casos
  adicionou um arquivo chamado `TAG` nos diretórios `tests/{1,2}` com
  contéudo `tipo-1`, e nos outros com conteúdo `tipo-2`. Dessa forma, o
  `checker` consegue saber como tem que avaliar o arquivo que está recebendo.

  A descrição das possíveis tags estão no arquivo `generator/tags.txt`.
  Preencher este arquivo é responsabilidade do autor do gerador de testes.
  
  Os nomes dos scripts devem seguir este formato:

  * `USUARIO-input.[rb,py]` --- Arquivo feito pelo `USUARIO` que verifica se
    um arquivo de entrada segue as especificações do enunciado.
  * `USUARIO-output.[rb,py]` --- Arquivo feito pelo `USUARIO` que verifica se
    um arquivo de saída segue as especificações do enunciado.

* `checklists/` --- Arquivos que usaremos para acompanhar as 4 fases do desenvolvimento do problema.
  * `fase-01-formulacao.md`
  * `fase-02-analise.md`
  * `fase-03-verificacao.md`
  * `fase-04-preparo-para-competicao.md`

* `docs/`
  * `enunciado.tex` --- Arquivo no formato LaTeX que contém o enunciado 
    do problema.
  * `descricao.tex` --- Arquivo no formato LaTeX que contém uma 
    descrição (sem história) do problema e pelo menos uma idéia de como 
    resolver o problema.
  * `tests/` --- Link simbólico para pasta `tests/0/`.
  * `imagens/` --- Pasta que contém as figuras que você deseja usar no
    enunciado do problema.

* `generator/` --- Pasta que contém os geradores de casos de testes. 
  * `generator.[rb,py,c,cpp]` --- O gerador será executado da pasta onde 
    ele deve criar os arquivos de **entrada**, isto é, da pasta testes.  
    As saídas devem O gerador **deve** criar uma pasta (os nomes das 
    pastas são números sequênciais a partir de 1) para cada conjunto de 
    teste; cada conjunto de teste é composto por várias instâncias. Cada 
    instância é um par de arquivos `inX` e `outX`.
    
    A pasta `0/` não pode ser alterada, pois nela colocaremos os casos que vão 
    estar no enunciado.
  * `tags.txt` -- O arquivo que contém uma descrição das tags que estão nas
    pastas de conjuntos de testes.
* `sols/` --- Pasta que contém as soluções oficiais.
  * `USUARIO-Xpts.[c,cpp,rb,py]`--- O arquivo do usuário `USUARIO` deve ganhar
    `X` pontos quando for submetido ao julgamento.
* `special_judge/` --- A pasta que contém todos os arquivos necessários para
  fazer um julgamento especial.
  * `special_judge.[rb,py]` --- O corretor especial dever receber os
    parâmetros `INPUT_FILE_PATH`, `OUTPUT_FILE_PATH`,
    `CONTESTER_OUTPUT_FILE_PATH`, `CONTESTER_SOURCE_FILE_PATH`, e devolve `0`
    se a solução retornou a resposta correta e `1` caso contrário.
* `tests/` --- Pasta que contém os testes do problema.
  * `0/` --- Pasta que contém os testes que estão presente no enunciado.
  * `K/` (para K > 0) --- Testes gerados pelo gerador de casos.
    * `TAG` --- Arquivo que contém uma `tag`. Essa `tag` ajudará o validador a
      decidir que tipo de validação tem que ser feita.

