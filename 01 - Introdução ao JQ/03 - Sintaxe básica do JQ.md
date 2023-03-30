# Sintaxe básica do JQ

A sintaxe básica do JQ segue o formato geral:

jq [opções] filtro [arquivo]

- **jq**: é o comando para invocar o JQ.
- **opções**: são as opções de linha de comando que podem ser usadas com o JQ. Alguns exemplos comuns incluem `-c` (para produzir uma saída compacta) e `-r` (para produzir uma saída em formato raw).
- **filtro**: é a expressão de filtragem que será aplicada aos dados JSON.
- **arquivo**: é o arquivo JSON de entrada que será processado. Se não for especificado, o JQ usará a entrada padrão (stdin).

Algumas expressões de filtro comuns do JQ incluem:

- `.`: seleciona o objeto JSON inteiro.
- `.chave`: seleciona o valor da chave específica.
- `.[]`: seleciona todos os elementos de um array JSON.
- `.[] | seleção`: aplica uma seleção a cada elemento de um array JSON.
- `. | seleção`: aplica uma seleção ao objeto JSON inteiro.

Por exemplo, para extrair o valor da chave "nome" de um objeto JSON, use a seguinte expressão de filtro:

jq '.nome' arquivo.json

Isso retornará o valor da chave "nome" do arquivo JSON especificado. Combinando diferentes expressões de filtro, é possível realizar uma variedade de manipulações e transformações em dados JSON usando o JQ.