# Extrair informações de arquivos JSON com o JQ

Nesta seção do treinamento, vamos mergulhar fundo na extração de informações de arquivos JSON usando o utilitário JQ. A partir do comando "select", você aprenderá como filtrar dados específicos de um arquivo JSON e obter apenas as informações relevantes. O comando "map" permitirá que você transforme os dados JSON para atender às suas necessidades específicas. Em seguida, o comando "sort" o ajudará a classificar os dados JSON de várias maneiras. Com o comando "group_by", você poderá agrupar dados JSON com base em chaves ou valores específicos. Finalmente, com o comando "reduce", você poderá realizar cálculos em dados JSON e gerar resultados úteis para sua análise. Vamos começar!

## Comando "select" para filtrar dados JSON:

O comando "select" é um dos mais úteis do JQ para filtrar dados JSON. Ele permite que você selecione um subconjunto dos dados com base em um critério específico.

O comando "select" usa a seguinte sintaxe básica:
```
select [filtro] [arquivo]
```

Onde "filtro" é a expressão usada para selecionar os dados desejados e "arquivo" é o nome do arquivo JSON de entrada.

A expressão de filtro pode ser uma variedade de operações e expressões lógicas para selecionar os dados desejados. Por exemplo, para selecionar todos os objetos no JSON que tenham o valor "true" para a chave "completed", você pode usar a seguinte expressão:
```
select(.completed == true) arquivo.json
```

Você também pode usar operadores lógicos e de comparação para refinar ainda mais a seleção. Por exemplo, para selecionar todos os objetos que tenham o valor "true" para a chave "completed" e o valor "5" para a chave "userId", você pode usar a seguinte expressão:
```
select(.completed == true and .userId == 5) arquivo.json
```

O comando "select" também pode ser combinado com outros comandos do JQ para transformar os dados selecionados em um formato desejado. Por exemplo, para selecionar apenas os valores da chave "title" dos objetos que correspondem à expressão de filtro, você pode usar o seguinte comando:
```
select(.completed == true and .userId == 5) | .title arquivo.json
```

Esses são apenas alguns exemplos do poderoso comando "select" do JQ. Experimente com diferentes expressões de filtro e combinações de comandos para explorar todas as possibilidades do JQ para manipulação de dados JSON.

### Exercícios:

Dado o arquivo **funcionarios.json** 
```
[
  {
    "nome": "João",
    "idade": 27,
    "cidade": "São Paulo",
    "profissao": "Engenheiro",
    "salario": 6500
  },
  {
    "nome": "Maria",
    "idade": 35,
    "cidade": "Rio de Janeiro",
    "profissao": "Médica",
    "salario": 12000
  },
  {
    "nome": "Pedro",
    "idade": 42,
    "cidade": "Porto Alegre",
    "profissao": "Advogado",
    "salario": 8500
  },
  {
    "nome": "Ana",
    "idade": 22,
    "cidade": "Belo Horizonte",
    "profissao": "Estudante",
    "salario": null
  }
]
```
#### Exercício 1:
Filtre os funcionários com idade igual a 30 anos.

***Resolução:***
```$ jq '.[] | select(.idade == 30)' funcionarios.json```

#### Exercício 2:
Filtre os funcionários com idade maior do que 30 anos.

***Resolução:***
```$ jq '.[] | select(.idade > 30)' funcionarios.json```

#### Exercício 3:
Filtre os funcionários com cargo de "Analista de Sistemas".

***Resolução:***
```$ jq '.[] | select(.cargo == "Analista de Sistemas")' funcionarios.json```

#### Exercício 4:
Filtre os funcionários com idade entre 30 e 40 anos e com cargo de "Analista de Dados".

***Resolução:***
```$ jq '.[] | select(.idade >= 30 and .idade <= 40 and .cargo == "Analista de Dados")' funcionarios.json```

## Comando "map" para transformar dados JSON:
## Comando "sort" para classificar dados JSON:
## Comando "group_by" para agrupar dados JSON: