# Extrair informações de arquivos JSON com o JQ

Nesta seção do treinamento, vamos mergulhar fundo na extração de informações de arquivos JSON usando o utilitário JQ. A partir do comando "select", você aprenderá como filtrar dados específicos de um arquivo JSON e obter apenas as informações relevantes. O comando "map" permitirá que você transforme os dados JSON para atender às suas necessidades específicas. Em seguida, o comando "sort" o ajudará a classificar os dados JSON de várias maneiras. Com o comando "group_by", você poderá agrupar dados JSON com base em chaves ou valores específicos. Finalmente, com o comando "reduce", você poderá realizar cálculos em dados JSON e gerar resultados úteis para sua análise. Vamos começar!

## Comando "select" para filtrar dados JSON:

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

### Exercícios:

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
#### Exercício 1:
Filtre os funcionários com idade igual a 30 anos.

***Resolução:***
```
jq '.[] | select(.idade == 30)' funcionarios.json
```

#### Exercício 2:
Filtre os funcionários com idade maior do que 30 anos.

***Resolução:***
```
$ jq '.[] | select(.idade > 30)' funcionarios.json
```

#### Exercício 3:
Filtre os funcionários com cargo de "Analista de Sistemas".

***Resolução:***
```
$ jq '.[] | select(.cargo == "Analista de Sistemas")' funcionarios.json
```

#### Exercício 4:
Filtre os funcionários com idade entre 30 e 40 anos e com cargo de "Analista de Dados".

***Resolução:***
```
$ jq '.[] | select(.idade >= 30 and .idade <= 40 and .cargo == "Analista de Dados")' funcionarios.json
```

## Comando "map" para transformar dados JSON:
O comando map é utilizado para transformar dados JSON. Ele é capaz de modificar todos os elementos de um array e de todos os objetos de um conjunto de dados JSON.

A sintaxe básica do comando map é a seguinte:
```
jq 'map(EXPRESSÃO)' arquivo.json
```

A expressão pode ser qualquer operação que transforme os dados desejados. Por exemplo, é possível adicionar ou remover elementos de um array, modificar valores de chaves em objetos JSON ou até mesmo criar novos objetos.

**Exemplo:**
Suponha que temos o seguinte arquivo JSON com informações sobre pessoas:
 ```
[
    {
        "nome": "João",
        "idade": 25,
        "cidade": "São Paulo",
        "profissão": "Engenheiro",
        "salario": 5000
    },
    {
        "nome": "Maria",
        "idade": 32,
        "cidade": "Rio de Janeiro",
        "profissão": "Médica",
        "salario": 8000
    },
    {
        "nome": "Pedro",
        "idade": 28,
        "cidade": "Belo Horizonte",
        "profissão": "Advogado",
        "salario": 6000
    }
]
 ```

Suponha também que queremos adicionar uma nova chave chamada "situacao" para cada pessoa, baseada em sua idade. Para isso, podemos utilizar o comando map da seguinte forma:

```
jq 'map(. + {"situacao": if .idade >= 30 then "adulto" else "jovem" end})' arquivo.json
```

A expressão . + {"situacao": if .idade >= 30 then "adulto" else "jovem" end} adiciona uma nova chave chamada "situacao" para cada objeto do array. O valor dessa chave é definido de acordo com a idade da pessoa.

O resultado será o seguinte:
```
[
  {
    "nome": "João",
    "idade": 25,
    "cidade": "São Paulo",
    "profissão": "Engenheiro",
    "salario": 5000,
    "situacao": "jovem"
  },
  {
    "nome": "Maria",
    "idade": 32,
    "cidade": "Rio de Janeiro",
    "profissão": "Médica",
    "salario": 8000,
    "situacao": "adulto"
  },
  {
    "nome": "Pedro",
    "idade": 28,
    "cidade": "Belo Horizonte",
    "profissão": "Advogado",
    "salario": 6000,
    "situacao": "jovem"
  }
]
```

Note que o resultado final contém a nova chave "situacao" adicionada para cada objeto do array.

### Exercícios:

Dao o seguinte arquivo 'clientes.json'
```
[
  {
    "nome": "Isabela",
    "idade": 22,
    "cidade": "Curitiba",
    "produto": "Vestido",
    "valor": 95.0,
    "data_ultima_compra": "2022-03-10",
    "Interesses": ["Esportes", "Roupas", "Bebidas"]
  },
  {
    "nome": "Lucas",
    "idade": 30,
    "cidade": "São Paulo",
    "produto": "Camisa",
    "valor": 50.0,
    "data_ultima_compra": "2022-03-12",
    "Interesses": ["Filmes", "Música", "Esportes"]
  },
  {
    "nome": "Gabriela",
    "idade": 27,
    "cidade": "Rio de Janeiro",
    "produto": "Calça",
    "valor": 120.0,
    "data_ultima_compra": "2022-03-05",
    "Interesses": ["Viagens", "Gastronomia", "Arte"]
  },
  {
    "nome": "Rodrigo",
    "idade": 35,
    "cidade": "Belo Horizonte",
    "produto": "Tênis",
    "valor": 200.0,
    "data_ultima_compra": "2022-03-18",
    "Interesses": ["Esportes", "Cinema", "Moda"]
  },
  {
    "nome": "Laura",
    "idade": 25,
    "cidade": "Porto Alegre",
    "produto": "Blusa",
    "valor": 80.0,
    "data_ultima_compra": "2022-03-07",
    "Interesses": ["Música", "Literatura", "Arte"]
  },
  {
    "nome": "Fernando",
    "idade": 29,
    "cidade": "São Paulo",
    "produto": "Jaqueta",
    "valor": 150.0,
    "data_ultima_compra": "2022-03-20",
    "Interesses": ["Esportes", "Gastronomia", "Moda"]
  },
  {
    "nome": "Maria",
    "idade": 33,
    "cidade": "Belo Horizonte",
    "produto": "Saia",
    "valor": 60.0,
    "data_ultima_compra": "2022-03-02",
    "Interesses": ["Viagens", "Esportes", "Arte"]
  },
  {
    "nome": "João",
    "idade": 26,
    "cidade": "Porto Alegre",
    "produto": "Calça",
    "valor": 100.0,
    "data_ultima_compra": "2022-03-11",
    "Interesses": ["Filmes", "Literatura", "Arte"]
  },
  {
    "nome": "Luciana",
    "idade": 24,
    "cidade": "Curitiba",
    "produto": "Vestido",
    "valor": 120.0,
    "data_ultima_compra": "2022-03-17",
    "Interesses": ["Esportes", "Gastronomia", "Moda"]
  },
]

```

#### Exercício 1:
Utilize o comando map para extrair apenas os nomes dos clientes do arquivo clientes.json.
***Resolução:***
```
jq 'map(.nome)' clientes.json
```

#### Exercício 2:
Utilize o comando map para adicionar uma nova chave-valor desconto em cada objeto, onde o valor será o resultado do cálculo do desconto de 10% sobre o valor da compra.
***Resolução:***
```
jq 'map(.desconto = (.valor * 0.1) | {nome, idade, cidade, produto, valor, data_ultima_compra, Interesses, desconto})' clientes.json
```

#### Exercício 3:
Utilize o comando map para renomear a chave produto para item.
***Resolução:***
```
jq 'map(.item = .produto | del(.produto))' clientes.json
```

#### Exercício 4:
Utilize o comando map para filtrar apenas os clientes que moram em São Paulo.
***Resolução:***
```
jq 'map(select(.cidade == "São Paulo"))' clientes.json
```

#### Exercício 5:
Utilize o comando map para calcular a média de idade dos clientes.
***Resolução:***
```
jq 'map(.idade) | add / length' clientes.json
```

## Comando "sort" para classificar dados JSON:
## Comando "group_by" para agrupar dados JSON: