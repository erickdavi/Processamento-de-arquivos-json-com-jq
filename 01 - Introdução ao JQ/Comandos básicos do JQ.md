# Comandos básicos do JQ

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
