# Comando "map" para transformar dados JSON:
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

## Exercícios:

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
  }
]

```

### Exercício 1:
Utilize o comando map para extrair apenas os nomes dos clientes do arquivo clientes.json.

***Resolução:***
```
jq 'map(.nome)' clientes.json
```

### Exercício 2:
Utilize o comando map para adicionar uma nova chave-valor desconto em cada objeto, onde o valor será o resultado do cálculo do desconto de 10% sobre o valor da compra.

***Resolução:***
```
jq 'map(.desconto = (.valor * 0.1) | {nome, idade, cidade, produto, valor, data_ultima_compra, Interesses, desconto})' clientes.json
```

### Exercício 3:
Utilize o comando map para renomear a chave produto para item.

***Resolução:***
```
jq 'map(.item = .produto | del(.produto))' clientes.json
```

### Exercício 4:
Utilize o comando map para filtrar apenas os clientes que moram em São Paulo.

***Resolução:***
```
jq 'map(select(.cidade == "São Paulo"))' clientes.json
```

### Exercício 5:
Utilize o comando map para calcular a média de idade dos clientes.

***Resolução:***
```
jq 'map(.idade) | add / length' clientes.json
```