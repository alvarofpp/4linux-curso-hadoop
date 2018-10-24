# Apache Pig
Apache Pig é uma abstração para o MapReduce.

## Pig Latin
Pig Latin é utilizado para escrever programas de análise de dados no Apache Pig. Sua sintaxe e semântica são semelhantes ao SQL.

- [Pig Latin Basics](https://pig.apache.org/docs/latest/basic.html).

**Executar script** pelo terminal:
```bash
pig -x tez script.pig
```

### Descrição dos comandos

| Comando      | Descrição     |
| ------------ | ------------- |
| `DESCRIBE`   | Para exibir o as informações de uma relação |
| `DISTINCT`   | Serve para eliminar a duplicidade entre os registros |
| `DUMP`       | Permite imprimir o conteúdo de uma relação no console |
| `EXPLAIN`    | Exiba os panosde execução MapReduce |
| `FOREACH/GENERATE` | Usado para gerar transformações de dados especificadas com base nos dados da coluna |
| `FILTER`     | Operador usado para selecionar as tuplas necessárias de uma relação com base em uma condição |
| `FULL OUTER` | Cria uma relação completa retorna as linhas quando há uma correspondência em uma das relações |
| `GROUP`      | Permite agrupar dados a partir de um campo |
| `JOIN`       | Serve para realizar JOIN(relacionamento) entre os registros |
| `JsonLoader` | Carrega dados como arquivos no formato JSON |
| `LEFT OUTER` | Cria uma junção externa para retorna todas as linhas da tabela à esquerda, mesmo que não haja correspondências na relação certa |
| `LIMIT`      | Permitir limitar uma quantidade de dados |
| `LOAD`       | Permite carregar os dados do sistema de arquivos Local e HDFS em uma relação |
| `ORDER`      | Classifique uma relação baseada em um ou mais campos |
| `RIGHT OUTER`| Cria uma junção externa para retorna todas as linhas da tabela à direita, mesmo que não haja correspondências na relação certa |
| `SPLIT`      | Operador usado para dividir uma relação em duas ou mais relações |
| `STORE`      | Armazene dados no sistema de arquivos |
| `TextLoader` | É uma função Load usada para carregar dados não estruturados no formato UTF-8 |

Modos de **carregar dados**:
```pig
-- Normal
lista_data = LOAD '/user/maria_dev/u.data' AS (usuarioID:int, filmeID:int, classificacao:int, data:int);

-- Com separador |
lista_item = LOAD '/user/maria_dev/u.item' USING PigStorage('|') AS (filmeID:int, filmeTitulo:chararray, dataLancamento:chararray, videoLancamento:chararray, link:chararray);

-- JSON
funcionarios_json = LOAD '/user/maria_dev/funcionarios.json' USING JsonLoader('id_func:int, nome:chararray, cargo:chararray, salario:chararray, departamento:chararray');
```

Modos de **gravar dados**:
```pig
-- Com separador ;
STORE lista_item INTO 'outputItem' USING PigStorage(';');

-- JSON
STORE funcionarios_json INTO '/user/maria_dev/arquivo.json' USING JsonStorage();
```