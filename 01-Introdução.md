# Introdução

## O que é o utilitário jq?

O utilitário jq é uma ferramenta de linha de comando para processamento de dados JSON. Ele é usado para filtrar, extrair, transformar e manipular dados JSON de uma variedade de fontes, como arquivos, saídas de comando e dados transmitidos pela rede. O jq é projetado para ser uma ferramenta leve e de alta velocidade que pode lidar com grandes volumes de dados JSON com facilidade.

A principal funcionalidade do jq é extrair informações específicas de arquivos JSON, como valores de chaves específicas ou subconjuntos de objetos JSON que atendam a determinados critérios de pesquisa. O jq também pode ser usado para transformar os dados JSON em diferentes formatos de saída, como CSV, XML, TSV e outros. Ele fornece uma maneira eficiente e flexível de trabalhar com dados JSON em ambientes de linha de comando e scripts. 

## Instalando o JQ

Para instalar o JQ, siga estas instruções:

1. Abra um terminal ou prompt de comando.
2. Certifique-se de ter permissões de administrador no sistema.
3. Execute o seguinte comando, dependendo do sistema operacional que você está usando:
- **Linux**: Use o gerenciador de pacotes da sua distribuição Linux para instalar o JQ. Por exemplo, no Ubuntu ou Debian, execute o seguinte comando: 
- **macOS**: Use o gerenciador de pacotes Homebrew para instalar o JQ. Execute o seguinte comando no terminal:
- **Windows**: Baixe o arquivo executável pré-compilado a partir do site oficial do JQ em https://stedolan.github.io/jq/download/. Em seguida, descompacte o arquivo em um diretório de sua escolha e adicione o diretório à sua variável de ambiente PATH.
4. Após a instalação, verifique se o JQ está instalado corretamente executando o seguinte comando no terminal:
Se o JQ foi instalado corretamente, você deverá ver a versão do JQ instalada na saída do comando.

## Sintaxe básica do JQ

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

## Comandos básicos do JQ

O JQ oferece uma ampla variedade de comandos para manipular e transformar dados JSON. Alguns dos comandos mais comuns incluem:

### Seleção de chaves
Para selecionar um valor específico de uma chave, use a notação ponto (. ):
```
jq '.chave'
```

### Seleção de objetos
Para selecionar um objeto inteiro, use a notação de chaves ({}):
```
jq '{ chave: .valor }'
```
### Filtrando resultados
Para filtrar resultados com base em determinados critérios, use a cláusula **select**:
```
jq '.[] | select(.chave == "valor")'
```
### Concatenando resultados
Para concatenar resultados em uma única matriz, use o comando `**add**`:

### Alterando a saída
Para formatar a saída JSON de uma maneira específica, use a opção **--compact-output** ou **--pretty-output**:

## Exercícios

Dado o arquivo 'dados.json'
```
{
  "pessoas": [
    {
      "nome": "João",
      "idade": 25,
      "cidade": "São Paulo",
      "estado": "SP",
      "telefone": "(11) 99999-1111",
      "email": "joao@gmail.com",
      "interesses": ["tecnologia", "futebol"]
    },
    {
      "nome": "Maria",
      "idade": 30,
      "cidade": "Rio de Janeiro",
      "estado": "RJ",
      "telefone": "(21) 99999-2222",
      "email": "maria@hotmail.com",
      "interesses": ["cinema", "viagens"]
    },
    {
      "nome": "Pedro",
      "idade": 20,
      "cidade": "Belo Horizonte",
      "estado": "MG",
      "telefone": "(31) 99999-3333",
      "email": "pedro@yahoo.com",
      "interesses": ["música", "esportes"]
    }
  ]
}
```

### Exercício 1:
Filtre o arquivo **dados.json** para exibir todas as pessoas que moram em São Paulo.

**Resolução:**
```cat dados.json | jq '.pessoas[] | select(.cidade == "São Paulo")'```

### Exercício 2:
Filtre o arquivo **dados.json** para exibir o nome e o e-mail de todas as pessoas com mais de 25 anos.

***Resolução:***
```cat dados.json | jq '.pessoas[] | select(.idade > 25) | {nome: .nome, email: .email}'```

### Exercício 3:
Filtre o arquivo dados.json para exibir a lista de interesses de cada pessoa.

**Resolução:**
```cat dados.json | jq '.pessoas[].interesses'```

### Exercício 4:
Filtre o arquivo dados.json para exibir a soma das idades de todas as pessoas.

**Resolução:**
```cat dados.json | jq '[.pessoas[].idade] | add'```

### Exercício 5:
Filtre o arquivo dados.json para exibir o nome, a cidade e o estado de todas as pessoas.

**Resolução:**
```cat dados.json | jq '.pessoas[] | {nome: .nome, cidade: .cidade, estado: .estado}'```