# <span style="color: pink;">Resumo dos Seminários de SQL</span>

## <span style="color: pink;">Introdução</span>
- Os seminários de SQL tiveram como objetivo aprofundar o conhecimento sobre bancos de dados relacionais, focando em técnicas e conceitos fundamentais para o desenvolvimento e gerenciamento eficaz de dados. A importância desses seminários reside na capacitação dos participantes para otimizar consultas, garantir a integridade dos dados e melhorar a performance geral das aplicações.

## <span style="color: pink;">Operadores de Agregação</span>

### <span style="color: #8ab3cf;">Definição e Exemplos</span>

- Os operadores de agregação permitem realizar cálculos sobre um conjunto de valores, retornando um único resultado. Os principais operadores incluem:

- COUNT: Conta o número de registros.
- SUM: Soma valores de uma coluna.
- AVG: Calcula a média dos valores.
- MAX e MIN: Retornam, respectivamente, o maior e o menor valor.

### <span style="color: #8ab3cf;">Exemplo:</span>

    SELECT COUNT(*) FROM vendas;
    SELECT AVG(preco) FROM produtos;

## <span style="color: pink;">Joins em SQL</span>

### <span style="color: #8ab3cf;">Explicação dos Tipos de Joins com Exemplos Práticos</span>

- Joins permitem combinar registros de duas ou mais tabelas com base em uma condição relacionada. Os principais tipos de joins são:

- INNER JOIN: Retorna registros que têm correspondência em ambas as tabelas.
- LEFT JOIN: Retorna todos os registros da tabela da esquerda e os correspondentes da tabela da direita.
- RIGHT JOIN: O oposto do LEFT JOIN.
- FULL JOIN: Retorna registros quando há correspondência em uma ou ambas as tabelas.

### <span style="color: #8ab3cf;">Exemplo:</span>

    SELECT a.nome, b.produto 
    FROM clientes a 
    INNER JOIN vendas b ON a.id = b.cliente_id;

## <span style="color: pink;">Operadores Lógicos</span>

### <span style="color: #8ab3cf;">Uso e Exemplos de AND, OR, NOT</span>

- Os operadores lógicos são utilizados para combinar condições em consultas SQL:

- AND: Retorna resultados que atendem a todas as condições.
- OR: Retorna resultados que atendem a pelo menos uma das condições.
- NOT: Exclui resultados que atendem a uma condição.

### <span style="color: #8ab3cf;">Exemplo:</span>

    SELECT * FROM clientes 
    WHERE idade > 18 AND cidade = 'São Paulo';

## <span style="color: pink;">Subconsultas</span>

### <span style="color: #8ab3cf;">O que São e Como São Utilizadas</span>

- Subconsultas são consultas aninhadas dentro de outra consulta, permitindo a execução de operações mais complexas. Elas podem ser usadas em cláusulas WHERE, FROM ou SELECT.

### <span style="color: #8ab3cf;">Exemplo:</span>

    SELECT nome FROM clientes 
    WHERE id IN (SELECT cliente_id FROM vendas WHERE total > 1000)

## <span style="color: pink;">Funções de Agregação com GROUP BY</span>

### <span style="color: #8ab3cf;">Explicação e Exemplos de Uso</span>

- A cláusula GROUP BY é utilizada para agrupar resultados com base em uma ou mais colunas e aplicar funções de agregação.

### <span style="color: #8ab3cf;">Exemplo:</span>

    SELECT cidade, COUNT(*) 
    FROM clientes 
    GROUP BY cidade;

## <span style="color: pink;">Indexação e Performance</span>

### <span style="color: #8ab3cf;">Importância e Cenários de Uso</span>

- A indexação melhora a velocidade das consultas em tabelas grandes, permitindo acesso mais rápido aos dados. É crucial em operações de leitura frequente.

- Exemplo de Cenário: Utilizar índices em colunas que são frequentemente usadas em condições de pesquisa ou joins.

## <span style="color: pink;">Transações e Controle de Confiabilidade</span>

### <span style="color: #8ab3cf;">Conceitos Chave e Aplicações</span>

- Transações garantem que um conjunto de operações seja executado de forma completa e segura, seguindo os princípios ACID (Atomicidade, Consistência, Isolamento e Durabilidade).

### <span style="color: #8ab3cf;">Exemplo:</span>


    BEGIN;
    UPDATE conta SET saldo = saldo - 100 WHERE id = 1;
    UPDATE conta SET saldo = saldo + 100 WHERE id = 2;
    COMMIT;

## <span style="color: pink;">Stored Procedures e Triggers</span>

### <span style="color: #8ab3cf;">Definição e Exemplos Práticos</span>

- Stored Procedures: Conjuntos de instruções SQL que podem ser executados como uma única chamada. Facilitam a reutilização de código e a lógica de negócios.

### <span style="color: #8ab3cf;">Exemplo:</span>


    CREATE PROCEDURE atualizarPreco (IN id INT, IN novo_preco DECIMAL)
    BEGIN
    UPDATE produtos SET preco = novo_preco WHERE id = id;
    END;

- Triggers: Procedimentos que são automaticamente executados em resposta a eventos em uma tabela, como inserções, atualizações ou deleções.

### <span style="color: #8ab3cf;">Exemplo:</span>

    CREATE TRIGGER antes_inserir_venda
    BEFORE INSERT ON vendas
    FOR EACH ROW
    SET NEW.data = NOW();

## <span style="color: pink;">Conclusão</span>
- Os seminários proporcionaram uma visão abrangente sobre conceitos fundamentais de SQL e seu papel no desenvolvimento de bancos de dados. A inter-relação entre os temas, como a importância das transações para manter a integridade dos dados e o uso de joins e subconsultas para consultas mais eficientes, é crucial para qualquer desenvolvedor que busca criar aplicações robustas e confiáveis. O conhecimento adquirido fortalecerá a habilidade de otimizar e gerenciar dados de forma eficaz.