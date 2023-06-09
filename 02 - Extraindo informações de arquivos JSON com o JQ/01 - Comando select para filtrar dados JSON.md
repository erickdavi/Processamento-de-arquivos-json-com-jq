# Comando "select" para filtrar dados JSON
O comando "select" é um dos mais úteis do JQ para filtrar dados JSON. Ele permite que você selecione um subconjunto dos dados com base em critérios específicos, por meio de operações condicionais e lógicas para filtrar dados JSON, tais como Operadores relacionais(<, <=, >, >=, ==, !=), lógicos( and, or, not), tipos de dados (.foo | type == "number") ou expressões regulares.

O comando "select" usa a seguinte sintaxe básica:
```
jq 'select([filtro]) [arquivo]
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

## Exercícios:

Dado o arquivo **funcionarios.json** 
```
[
  {
    "nome": "João",
    "idade": 35,
    "cidade": "São Paulo",
    "profissão": "Analista de Sistemas",
    "salario": 7000
  },
  {
    "nome": "Maria",
    "idade": 27,
    "cidade": "Rio de Janeiro",
    "profissão": "Advogada",
    "salario": 8000
  },
  {
    "nome": "Pedro",
    "idade": 42,
    "cidade": "Belo Horizonte",
    "profissão": "Engenheiro Civil",
    "salario": 10000
  },
  {
    "nome": "Julia",
    "idade": 24,
    "cidade": "Florianópolis",
    "profissão": "Designer Gráfico",
    "salario": 5500
  },
  {
    "nome": "Ricardo",
    "idade": 38,
    "cidade": "Curitiba",
    "profissão": "Gerente de Projetos",
    "salario": 12000
  },
  {
    "nome": "Fernanda",
    "idade": 29,
    "cidade": "Porto Alegre",
    "profissão": "Médica",
    "salario": 15000
  },
  {
    "nome": "Renato",
    "idade": 31,
    "cidade": "Salvador",
    "profissão": "Arquiteto",
    "salario": 9000
  },
  {
    "nome": "Gabriela",
    "idade": 26,
    "cidade": "Recife",
    "profissão": "Analista de Marketing",
    "salario": 6000
  },
  {
    "nome": "Luiz",
    "idade": 45,
    "cidade": "Brasília",
    "profissão": "Professor Universitário",
    "salario": 8000
  },
  {
    "nome": "Mariana",
    "idade": 28,
    "cidade": "Natal",
    "profissão": "Jornalista",
    "salario": 7000
  },
  {
    "nome": "Lucas",
    "idade": 39,
    "cidade": "Fortaleza",
    "profissão": "Médico Veterinário",
    "salario": 11000
  },
  {
    "nome": "Carla",
    "idade": 25,
    "cidade": "Belém",
    "profissão": "Desenvolvedora de Software",
    "salario": 7500
  },
  {
    "nome": "Rodrigo",
    "idade": 33,
    "cidade": "Manaus",
    "profissão": "Gerente de TI",
    "salario": 13000
  },
  {
    "nome": "Ana",
    "idade": 30,
    "cidade": "Porto Velho",
    "profissão": "Psicóloga",
    "salario": 6000
  },
  {
    "nome": "Leonardo",
    "idade": 36,
    "cidade": "Cuiabá",
    "profissão": "Engenheiro de Produção",
    "salario": 950

  }
]
```
## Exercício 1:
Filtre os funcionários com idade igual a 30 anos.

***Resolução:***
```
jq '.[] | select(.idade == 30)' funcionarios.json
```

## Exercício 2:
Filtre os funcionários com idade maior do que 30 anos.

***Resolução:***
```
$ jq '.[] | select(.idade > 30)' funcionarios.json
```

## Exercício 3:
Filtre os funcionários com cargo de "Analista de Sistemas".

***Resolução:***
```
$ jq '.[] | select(.cargo == "Analista de Sistemas")' funcionarios.json
```

## Exercício 4:
Filtre os funcionários com idade entre 30 e 40 anos e com cargo de "Analista de Dados".

***Resolução:***
```
$ jq '.[] | select(.idade >= 30 and .idade <= 40 and .cargo == "Analista de Dados")' funcionarios.json