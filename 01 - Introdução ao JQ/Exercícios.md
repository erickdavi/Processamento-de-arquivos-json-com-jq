# Exercícios

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
```
jq '.pessoas[] | select(.cidade == "São Paulo")' dados.json
```

### Exercício 2:
Filtre o arquivo **dados.json** para exibir o nome e o e-mail de todas as pessoas com mais de 25 anos.

***Resolução:***
```
jq '.pessoas[] | select(.idade > 25) | {nome: .nome, email: .email}' dados.json
```

### Exercício 3:
Filtre o arquivo dados.json para exibir a lista de interesses de cada pessoa.

**Resolução:**
```
jq '.pessoas[].interesses' dados.json
```

### Exercício 4:
Filtre o arquivo dados.json para exibir a soma das idades de todas as pessoas.

**Resolução:**
```
jq '[.pessoas[].idade] | add' dados.json
```

### Exercício 5:
Filtre o arquivo dados.json para exibir o nome, a cidade e o estado de todas as pessoas.

**Resolução:**
```
jq '.pessoas[] | {nome: .nome, cidade: .cidade, estado: .estado}' dados.json
```