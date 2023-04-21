
# ***Documentação do Código - Criação de Banco de Dados***

Comando básico para criação e manipulação de um banco de dados com imagens ilustrativas

# **✍️ CMD `CREATE DATABASE IF NOT EXISTS`**

Descrição
---------

Este código é uma instrução SQL para criar um banco de dados chamado "db\_flashCardBar" utilizando a linguagem PHP. A cláusula "IF NOT EXISTS" verifica se o banco de dados já existe antes de criar um novo, evitando duplicações. O conjunto de caracteres (character set) utilizado é o "utf8mb4" e a colação (collation) é "utf8mb4\_unicode\_ci", que são adequados para suportar caracteres Unicode, incluindo emojis e outros caracteres multibyte.

Código
------

sql

```sql
CREATE DATABASE IF NOT EXISTS db_flashCardBar CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Detalhes
--------

*   `CREATE DATABASE`: É uma instrução SQL utilizada para criar um novo banco de dados no sistema de gerenciamento de banco de dados (SGBD).
*   `IF NOT EXISTS`: É uma cláusula condicional que verifica se o banco de dados já existe antes de criar um novo. Se o banco de dados já existir, a instrução é ignorada, evitando duplicações.
*   `db_flashCardBar`: É o nome do banco de dados que está sendo criado. Você pode substituir esse nome pelo nome que desejar para o seu banco de dados.
*   `CHARACTER SET utf8mb4`: É uma especificação do conjunto de caracteres que o banco de dados deve suportar. "utf8mb4" é um conjunto de caracteres que suporta todos os caracteres Unicode, incluindo emojis e outros caracteres multibyte.
*   `COLLATE utf8mb4_unicode_ci`: É uma especificação da collation, ou seja, a forma como os caracteres são comparados e ordenados. "utf8mb4\_unicode\_ci" é uma collation que trata os caracteres como case-insensitive (não diferencia maiúsculas de minúsculas) e suporta caracteres Unicode.

Referências
-----------

*   [Documentação oficial do MySQL - CREATE DATABASE](https://dev.mysql.com/doc/refman/8.0/en/create-database.html)
*   [Documentação oficial do MySQL - Character Sets and Collations](https://dev.mysql.com/doc/refman/8.0/en/charset-general.html)


# **✍️ CMD `USE`**

Descrição
---------

Este código é uma instrução SQL para selecionar o banco de dados "db\_flashCardBar" como o banco de dados atual a ser utilizado em uma aplicação PHP. A instrução "USE" é usada para especificar o banco de dados com o qual as próximas instruções SQL irão interagir.

Código
------

sql

```sql
USE db_flashCardBar;
```

Detalhes
--------

*   `USE`: É uma instrução SQL utilizada para selecionar o banco de dados que será utilizado como o banco de dados ativo. Todas as próximas instruções SQL executadas após essa instrução irão operar no banco de dados especificado.
*   `db_flashCardBar`: É o nome do banco de dados que será selecionado como o banco de dados atual. Você pode substituir esse nome pelo nome do banco de dados que você deseja utilizar em sua aplicação.

Referências
-----------

*   [Documentação oficial do MySQL - USE](https://dev.mysql.com/doc/refman/8.0/en/use.html)


# **✍️ CMD `CREATE TABLE IF NOT EXISTS`**

Descrição
---------

Este código é uma instrução SQL para criar uma tabela chamada "tb\_baralhos" em um banco de dados utilizando a linguagem PHP. A tabela é projetada para armazenar informações sobre baralhos de cartas, com colunas para o identificador do baralho (idBar), o nome do baralho (c\_bar), a data de criação do baralho (c\_dt), a data de criação do registro (c\_dtc), e a data de modificação do registro (c\_dtMod). A instrução também inclui definições de chave primária (PRIMARY KEY), tipo de armazenamento (ENGINE), conjunto de caracteres (CHARSET) e collation (COLLATE) para a tabela.

Código
------

sql

```sql
CREATE TABLE IF NOT EXISTS tb_baralhos (
    idBar VARCHAR(255) NOT NULL,
    c_bar VARCHAR(255) NOT NULL,
    c_dt DATE NOT NULL,
    c_dtc DATE NOT NULL DEFAULT DATE(NOW()),
    c_dtMod TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (idBar)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci COMMENT='Tabela de usuários do sistema';
```

Detalhes
--------

*   `CREATE TABLE`: É uma instrução SQL utilizada para criar uma nova tabela no banco de dados.
*   `IF NOT EXISTS`: É uma cláusula condicional que verifica se a tabela já existe antes de criar uma nova. Se a tabela já existir, a instrução é ignorada, evitando duplicações.
*   `tb_baralhos`: É o nome da tabela que está sendo criada. Você pode substituir esse nome pelo nome que desejar para sua tabela.
*   `idBar`: É o nome da primeira coluna da tabela, que é usada para armazenar o identificador do baralho. O tipo de dado é VARCHAR com tamanho máximo de 255 caracteres, e é definido como NOT NULL, ou seja, obrigatório.
*   `c_bar`: É o nome da segunda coluna da tabela, que é usada para armazenar o nome do baralho. O tipo de dado é VARCHAR com tamanho máximo de 255 caracteres, e é definido como NOT NULL, ou seja, obrigatório.
*   `c_dt`: É o nome da terceira coluna da tabela, que é usada para armazenar a data de criação do baralho. O tipo de dado é DATE e é definido como NOT NULL, ou seja, obrigatório.
*   `c_dtc`: É o nome da quarta coluna da tabela, que é usada para armazenar a data de criação do registro. O tipo de dado é DATE e é definido como NOT NULL por padrão, mas é definido como DEFAULT DATE(NOW()), ou seja, se nenhum valor for fornecido, será automaticamente preenchido com a data atual do sistema.
*   `c_dtMod`: É o nome da quinta coluna da tabela, que é usada para armazenar a data de modificação do registro. O tipo de dado é TIMESTAMP e é definido como NOT NULL por padrão, mas é definido como DEFAULT CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP, ou seja, será automaticamente atualizado com a data e hora atual do sistema sempre que o registro for modificado.
*   `PRIMARY KEY`: É uma definição da chave primária da tabela, que é usada para identificar de forma única cada registro



Vantagens de usar VARCHAR:
--------------------------

1.  Economia de espaço: A coluna VARCHAR é mais eficiente em termos de espaço de armazenamento em comparação com a coluna TEXT. Isso ocorre porque o VARCHAR armazena apenas a quantidade de caracteres inseridos, enquanto a coluna TEXT reserva um espaço fixo, independentemente do número de caracteres inseridos. Portanto, quando se espera que a quantidade de texto armazenado seja variável e geralmente menor do que o espaço reservado pela coluna TEXT, o uso de VARCHAR pode economizar espaço de armazenamento no banco de dados.
    
2.  Desempenho de busca: O uso de VARCHAR pode ter um melhor desempenho em operações de busca e comparação em comparação com a coluna TEXT. Isso ocorre porque o VARCHAR armazena apenas a quantidade de caracteres inseridos, enquanto a coluna TEXT reserva um espaço fixo, independentemente do número de caracteres inseridos. Portanto, em operações de busca e comparação de texto, a coluna VARCHAR pode ser mais rápida, pois tem menos dados para percorrer.
    
3.  Flexibilidade: O uso de VARCHAR oferece mais flexibilidade em relação ao tamanho máximo dos dados armazenados. É possível especificar o tamanho máximo de caracteres permitidos em uma coluna VARCHAR, o que pode ser útil em situações onde é necessário impor restrições de tamanho máximo de texto. Por outro lado, a coluna TEXT não possui um limite de tamanho máximo específico, o que pode resultar em problemas de desempenho e armazenamento se houver a necessidade de impor restrições de tamanho de texto.
    
4.  Compatibilidade: O uso de VARCHAR é mais compatível com diferentes sistemas de gerenciamento de banco de dados (SGBDs) e tipos de bancos de dados. A coluna TEXT é geralmente específica de alguns SGBDs e pode ter comportamentos diferentes em diferentes tipos de bancos de dados. Por outro lado, o uso de VARCHAR é mais padronizado e amplamente suportado em vários SGBDs, tornando-o uma opção mais versátil em diferentes ambientes de banco de dados.
    

Conclusão
---------

Em resumo, o uso de colunas VARCHAR pode ter vantagens significativas em termos de economia de espaço, desempenho de busca, flexibilidade e compatibilidade em comparação com o uso de colunas TEXT. É importante considerar as necessidades específicas do projeto e as características do banco de dados ao escolher entre VARCHAR e TEXT para armazenamento de texto.


Configurações básicas de Tabela
======================================


1.  ENGINE: A configuração "ENGINE" define o mecanismo de armazenamento a ser usado para a tabela. No caso do código fornecido, o valor "InnoDB" é especificado. O mecanismo InnoDB é um mecanismo de armazenamento transacional que é amplamente usado no MySQL e é conhecido por suportar recursos como transações ACID (Atomicidade, Consistência, Isolamento e Durabilidade), chaves estrangeiras e bloqueios granulares.
    
2.  DEFAULT CHARSET: A configuração "DEFAULT CHARSET" define o conjunto de caracteres padrão a ser usado para a tabela. No código fornecido, o valor "utf8mb4" é especificado. O conjunto de caracteres utf8mb4 é uma extensão do conjunto de caracteres UTF-8 que suporta uma gama mais ampla de caracteres, incluindo emoji e caracteres especiais de várias línguas.
    
3.  COLLATE: A configuração "COLLATE" define a ordem de classificação padrão a ser usada para a tabela. No código fornecido, o valor "utf8mb4\_unicode\_ci" é especificado. O "ci" no final significa "case-insensitive", o que indica que a ordenação de caracteres não é sensível a maiúsculas e minúsculas.
    

Conclusão
---------
As configurações de tabela, como ENGINE, DEFAULT CHARSET e COLLATE, são importantes para definir o comportamento e as características das tabelas em um banco de dados. É importante considerar as necessidades específicas do projeto e as características do banco de dados ao configurar uma tabela, para garantir o correto funcionamento e desempenho do sistema.

👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232827943-a20ebf2d-3a40-4041-aa26-9a5abfde1156.png)




# **✍️ CMD `SHOW COLUMNS FROM tb_baralhos`**

Descrição
---------

Este código é uma instrução SQL para exibir as colunas de uma tabela chamada "tb\_baralhos" utilizando a linguagem PHP. A instrução "SHOW COLUMNS" é usada para obter informações sobre as colunas de uma tabela existente no banco de dados.

Código
------

sql

```sql
SHOW COLUMNS FROM tb_baralhos;
```

Detalhes
--------

*   `SHOW COLUMNS`: É uma instrução SQL utilizada para obter informações detalhadas sobre as colunas de uma tabela existente no banco de dados.
*   `FROM tb_baralhos`: É a cláusula que especifica a tabela da qual se deseja obter informações das colunas. "tb\_baralhos" é o nome da tabela da qual as colunas serão exibidas. Você pode substituir esse nome pelo nome da tabela que deseja obter informações.

Resultados
----------

A instrução "SHOW COLUMNS" retorna um conjunto de resultados que contém informações detalhadas sobre as colunas da tabela especificada. Essas informações podem incluir o nome da coluna, o tipo de dado, o tamanho máximo do dado, se a coluna permite nulos (NULL), se é uma chave primária, se é uma chave estrangeira, entre outras informações relevantes sobre as colunas da tabela.

Referências
-----------

*   [Documentação oficial do MySQL - SHOW COLUMNS](https://dev.mysql.com/doc/refman/8.0/en/show-columns.html)

👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232831343-399f0226-455d-42c3-943f-cf5f3b44c538.png)


===========================================================

# **✍️ CMD `SET SQL_SAFE_UPDATES`**

Descrição
---------
Configuração do **SQL\_SAFE\_UPDATES;** Este código é composto por duas instruções SQL para configurar a variável de sistema `SQL_SAFE_UPDATES` no MySQL. A primeira instrução `SET SQL_SAFE_UPDATES = 0;` desativa o modo seguro de atualizações no banco de dados, permitindo a execução de atualizações sem a cláusula `WHERE`, o que pode ser arriscado em alguns casos. A segunda instrução `SET SQL_SAFE_UPDATES = 1;` reativa o modo seguro de atualizações, que é a configuração padrão do MySQL, tornando obrigatória a utilização da cláusula `WHERE` em atualizações.

Código
------

sql

```sql
SET SQL_SAFE_UPDATES = 0;
-- Realize as atualizações necessárias aqui
```
sql
```sql
-- Realize as atualizações necessárias aqui
SET SQL_SAFE_UPDATES = 1;
```

Detalhes
--------

*   `SET SQL_SAFE_UPDATES`: É uma instrução SQL utilizada para definir o valor da variável de sistema `SQL_SAFE_UPDATES` no MySQL. Essa variável controla se é permitido ou não realizar atualizações sem a cláusula `WHERE` em tabelas que não possuam uma chave primária ou única definida.
*   `0`: É o valor que define o modo inseguro de atualizações, onde atualizações sem cláusula `WHERE` são permitidas.
*   `1`: É o valor que define o modo seguro de atualizações, onde atualizações sem cláusula `WHERE` são bloqueadas.

Importante
----------

*   É recomendado utilizar o modo seguro de atualizações, com `SQL_SAFE_UPDATES` definido como `1`, para evitar atualizações acidentais ou indesejadas em todas as situações em que não há uma necessidade específica de desativá-lo.
*   Antes de desativar o modo seguro de atualizações com `SQL_SAFE_UPDATES` definido como `0`, é importante ter cuidado e garantir que as atualizações sejam realizadas com atenção e segurança, utilizando cláusulas `WHERE` adequadas para evitar atualizações indesejadas em registros incorretos.

Referências
-----------

*   [Documentação oficial do MySQL - SET Syntax for Variable Assignment](https://dev.mysql.com/doc/refman/8.0/en/set-variable.html)
*   [Documentação oficial do MySQL - Server SQL Modes](https://dev.mysql.com/doc/refman/8.0/en/sql-mode.html)


# **✍️ CMD `DROP TABLE tb_baralhos;`**


Descrição
---------

Este código é uma instrução SQL para excluir uma tabela chamada "tb\_baralhos" de um banco de dados utilizando a linguagem PHP. A tabela será permanentemente removida do banco de dados.

Código
------

sql

```sql
DROP TABLE tb_baralhos;
```

Detalhes
--------

*   `DROP TABLE`: É uma instrução SQL utilizada para excluir uma tabela de um banco de dados no sistema de gerenciamento de banco de dados (SGBD).
*   `tb_baralhos`: É o nome da tabela que está sendo excluída. Você pode substituir esse nome pelo nome da tabela que deseja excluir do seu banco de dados.

Atenção
-------

A exclusão de uma tabela é uma operação irreversível e todos os dados contidos na tabela serão permanentemente removidos. Certifique-se de ter um backup adequado dos dados antes de executar essa instrução em um ambiente de produção.

Referências
-----------

*   [Documentação oficial do MySQL - DROP TABLE](https://dev.mysql.com/doc/refman/8.0/en/drop-table.html)


# **✍️ CMD `DELETE FROM tb_baralhos WHERE idBar = 7;`**


Descrição
---------

Este código é uma instrução SQL para excluir um registro da tabela "tb\_baralhos" em um banco de dados, especificamente o registro que possui o valor "7" no campo "idBar". Essa instrução é utilizada para deletar dados de uma tabela em um sistema de gerenciamento de banco de dados (SGBD) usando a linguagem PHP.

Código
------

sql

```sql
DELETE FROM tb_baralhos WHERE idBar = 7;
```

Detalhes
--------

*   `DELETE FROM`: É uma instrução SQL utilizada para excluir registros de uma tabela em um banco de dados.
*   `tb_baralhos`: É o nome da tabela da qual o registro será excluído. Você deve substituir esse nome pelo nome da tabela que deseja excluir o registro.
*   `WHERE`: É uma cláusula condicional que permite especificar a condição para exclusão dos registros. Neste caso, a condição é "idBar = 7", ou seja, será excluído o registro cujo valor do campo "idBar" seja igual a 7. Você pode ajustar essa condição de acordo com os critérios de exclusão desejados.
*   `idBar`: É o nome do campo que será utilizado na condição de exclusão. Você deve substituir esse nome pelo nome do campo correto da sua tabela.
*   `7`: É o valor que será utilizado na condição de exclusão. Você pode substituir esse valor pelo valor correto que deseja utilizar para excluir o registro desejado.

Referências
-----------

*   [Documentação oficial do MySQL - DELETE Statement](https://dev.mysql.com/doc/refman/8.0/en/delete.html)



# **✍️ CMD `SELECT * FROM tb_baralhos`**

Descrição
---------

Este código é uma instrução SQL para realizar uma consulta de todos os registros da tabela "tb\_baralhos". A tabela "tb\_baralhos" é parte de um sistema de CRUD (Create, Read, Update, Delete) em PHP, seguindo a arquitetura de MVC (Model-View-Controller) para a organização do código-fonte.

Código
------

sql

```sql
SELECT * FROM tb_baralhos;
```

Detalhes
--------

*   `SELECT`: É uma instrução SQL utilizada para realizar consultas em um banco de dados, retornando dados específicos de uma tabela.
*   `*`: É um caractere curinga que representa todas as colunas da tabela. Neste caso, a consulta está retornando todas as colunas da tabela "tb\_baralhos".
*   `FROM`: É uma cláusula SQL utilizada para especificar a tabela da qual se deseja realizar a consulta.
*   `tb_baralhos`: É o nome da tabela da qual os dados estão sendo consultados. Você pode substituir esse nome pelo nome da tabela que deseja consultar em seu banco de dados.

Referências
-----------

*   [Documentação oficial do MySQL - SELECT](https://dev.mysql.com/doc/refman/8.0/en/select.html)
*   [Documentação oficial do PHP - PDO (PHP Data Objects)](https://www.php.net/manual/en/book.pdo.php)
*   [Documentação oficial do padrão MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)



# **✍️ CMD `INSERT INTO `**

Descrição
---------

Este código é uma instrução SQL para inserir dados em uma tabela chamada "tb\_baralhos". A instrução realiza a inserção de um novo registro na tabela com os valores especificados para as colunas "idBar", "c\_bar" e "c\_dt".

Código
------

sql

```sql
INSERT INTO tb_baralhos 
    (idBar, c_bar, c_dt) 
    VALUES 
    (1, 'Baralho #001', '2023-01-01');
```

Detalhes
--------

*   `INSERT INTO`: É uma instrução SQL utilizada para adicionar novos registros em uma tabela específica.
*   `tb_baralhos`: É o nome da tabela na qual os dados estão sendo inseridos. Você pode substituir esse nome pelo nome da tabela em que deseja inserir os dados.
*   `(idBar, c_bar, c_dt)`: São as colunas da tabela às quais os valores estão sendo atribuídos. Neste caso, são as colunas "idBar", "c\_bar" e "c\_dt".
*   `VALUES`: É uma cláusula que especifica os valores a serem inseridos nas colunas da tabela.
*   `(1, 'Baralho #001', '2023-01-01')`: São os valores que estão sendo inseridos nas colunas da tabela. Neste caso, é um novo registro com os valores "1" para "idBar", "Baralho #001" para "c\_bar" e "2023-01-01" para "c\_dt". Os valores devem estar na mesma ordem das colunas especificadas anteriormente.

Referências
-----------

*   [Documentação oficial do MySQL - INSERT INTO Statement](https://dev.mysql.com/doc/refman/8.0/en/insert.html)


👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232838004-9a789c55-145a-4814-a283-e3fbea11149f.png)



# **✍️ CMD `UPDATE SET WHERE`**


Este código é uma instrução SQL para atualizar os dados de uma tabela chamada "tb\_baralhos" em um banco de dados. A instrução "UPDATE" permite modificar os valores de colunas específicas em uma ou mais linhas de uma tabela. Neste exemplo, os valores das colunas "c\_bar" e "c\_dt" serão atualizados na linha onde o valor da coluna "idBar" for igual a 1.

Código
------

sql

```sql
UPDATE tb_baralhos
SET 
  c_bar = 'Baralho #001 update',
  c_dt = '2022-04-10'
WHERE idBar = 1;
```

Detalhes
--------

*   `UPDATE`: É uma instrução SQL utilizada para atualizar os dados em uma tabela.
*   `tb_baralhos`: É o nome da tabela que está sendo atualizada. Você pode substituir esse nome pelo nome da tabela que deseja atualizar os dados.
*   `SET`: É uma cláusula que especifica as colunas e os valores que serão atualizados na tabela. Neste exemplo, a coluna "c\_bar" será atualizada com o valor 'Baralho #001 update' e a coluna "c\_dt" será atualizada com o valor '2022-04-10'.
*   `WHERE`: É uma cláusula condicional que especifica a condição que as linhas devem atender para serem atualizadas. Neste exemplo, a condição é que o valor da coluna "idBar" seja igual a 1.
*   `idBar`: É o nome da coluna que está sendo utilizada como condição para atualização. Você pode substituir esse nome pelo nome da coluna que deseja utilizar como condição.
*   `1`: É o valor que está sendo comparado na condição. Você pode substituir esse valor pelo valor desejado para a condição de atualização.

Referências
-----------

*   [Documentação oficial do MySQL - UPDATE](https://dev.mysql.com/doc/refman/8.0/en/update.html)
*   [Documentação oficial do MySQL - WHERE Clause](https://dev.mysql.com/doc/refman/8.0/en/where-optimizations.html)

👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232910582-b782ee23-2f3d-4e56-b45d-397d2001cbf3.png)




# **✍️ CMD `ALTER TABLE ADD novaColuna AFTER colunaExistente`**


Descrição
---------

Este código é uma instrução SQL para alterar a tabela "tb\_baralhos" em um banco de dados. A instrução "ALTER TABLE" é usada para modificar a estrutura de uma tabela existente, adicionando uma nova coluna chamada "c\_descr" do tipo VARCHAR com tamanho máximo de 255 caracteres. A coluna é definida como opcional (NULL) e será adicionada após a coluna "c\_dt" na ordem das colunas da tabela.

Código
------

sql

```sql
ALTER TABLE tb_baralhos ADD c_descr VARCHAR(255) NULL AFTER c_dt;
```

Detalhes
--------

*   `ALTER TABLE`: É uma instrução SQL utilizada para modificar a estrutura de uma tabela existente em um banco de dados.
*   `tb_baralhos`: É o nome da tabela que está sendo alterada. Você pode substituir esse nome pelo nome da tabela que deseja modificar.
*   `ADD`: É uma cláusula do "ALTER TABLE" que indica que uma nova coluna está sendo adicionada à tabela.
*   `c_descr`: É o nome da nova coluna que está sendo adicionada à tabela. Você pode substituir esse nome pelo nome que desejar para a nova coluna.
*   `VARCHAR(255)`: É o tipo de dado da nova coluna. "VARCHAR" é um tipo de dado de texto que pode armazenar uma sequência de caracteres. "(255)" indica o tamanho máximo da coluna, que neste caso é de 255 caracteres. Você pode ajustar esse tamanho de acordo com suas necessidades.
*   `NULL`: É uma especificação da opcionalidade da coluna. Neste caso, a nova coluna "c\_descr" é definida como opcional, ou seja, pode conter valores nulos.
*   `AFTER c_dt`: É uma especificação da posição da nova coluna em relação às colunas existentes na tabela. Neste caso, a nova coluna "c\_descr" será adicionada após a coluna "c\_dt" na ordem das colunas da tabela.

Referências
-----------

*   [Documentação oficial do MySQL - ALTER TABLE](https://dev.mysql.com/doc/refman/8.0/en/alter-table.html)
*   [Documentação oficial do MySQL - Data Types](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)

👉Resultado
---------

![image](https://user-images.githubusercontent.com/93455937/232912257-613e99c8-6c24-4f19-89c4-f2a3ee900d67.png)
![image](https://user-images.githubusercontent.com/93455937/232912398-1b8b5f45-f7ab-447c-a1a4-1b751da3c7ad.png)

# **✍️ CMD `ALTER TABLE tabela MODIFY coluna`**

Este código é uma instrução SQL para alterar a definição de uma coluna em uma tabela chamada "tb\_baralhos" em um banco de dados. A coluna "c\_descr" está sendo modificada para permitir um tamanho máximo de 1545 caracteres e permitir valores nulos (NULL). Essa instrução é utilizada para alterar a estrutura de uma tabela já existente.

Código
------

sql

```sql
ALTER TABLE tb_baralhos MODIFY c_descr varchar(1545) NULL;
```


```sql
ALTER TABLE tb_baralhos MODIFY c_descr varchar(1545) NULL;
```

Detalhes
--------

*   `ALTER TABLE`: É uma instrução SQL utilizada para modificar a estrutura de uma tabela existente em um sistema de gerenciamento de banco de dados (SGBD).
*   `tb_baralhos`: É o nome da tabela que está sendo modificada. Substitua esse nome pelo nome da tabela que você deseja alterar na sua base de dados.
*   `MODIFY c_descr varchar(1545) NULL`: É a cláusula que especifica a alteração na coluna "c\_descr". Neste caso, a definição da coluna está sendo modificada para permitir um tamanho máximo de 1545 caracteres, com o tipo de dado "varchar", que é utilizado para armazenar strings de tamanho variável. Além disso, a cláusula "NULL" permite que essa coluna aceite valores nulos.



A sintaxe da cláusula `MODIFY` pode variar dependendo do sistema de gerenciamento de banco de dados (SGBD) que você está usando. Aqui estão alguns exemplos de como a cláusula `MODIFY` pode ser escrita em outros SGBDs populares:

1.  MySQL (versões anteriores ao MariaDB):

sql

```sql
ALTER TABLE tb_baralhos MODIFY c_descr varchar(1545) NULL;
```

2.  PostgreSQL:

sql

```sql
ALTER TABLE tb_baralhos ALTER COLUMN c_descr TYPE varchar(1545), ALTER COLUMN c_descr DROP NOT NULL;
```

3.  Microsoft SQL Server:

sql

```sql
ALTER TABLE tb_baralhos ALTER COLUMN c_descr varchar(1545) NULL;
```

4.  Oracle Database:

sql

```sql
ALTER TABLE tb_baralhos MODIFY c_descr varchar2(1545) NULL;
```

5.  SQLite: Não suporta a cláusula `MODIFY` diretamente. Para modificar uma tabela, é necessário criar uma nova tabela com a nova definição, copiar os dados da tabela antiga para a nova tabela e, em seguida, renomear a nova tabela para o nome original.

    É importante notar que a sintaxe exata da cláusula `MODIFY` pode variar entre diferentes versões dos SGBDs, por isso é sempre recomendável consultar a documentação oficial do SGBD específico que você está usando para obter a sintaxe correta.


***SGBD*** 
-----
SGBD é a sigla para Sistema de Gerenciamento de Banco de Dados. É um software projetado para gerenciar a criação, organização, armazenamento, recuperação, modificação e exclusão de dados em um banco de dados. O SGBD atua como uma interface entre os aplicativos de software e os dados armazenados em um banco de dados, permitindo que os usuários interajam com os dados de forma eficiente e segura.

Os SGBDs são amplamente utilizados em aplicações de software, desde sistemas empresariais complexos até aplicativos de desktop e aplicativos móveis. Eles são responsáveis por garantir a integridade, consistência e segurança dos dados armazenados, bem como por fornecer mecanismos para consultas e manipulação de dados.

Existem vários tipos de SGBDs disponíveis, incluindo bancos de dados relacionais, como MySQL, PostgreSQL, Microsoft SQL Server e Oracle Database, e bancos de dados não relacionais, como MongoDB e Cassandra. Cada tipo de SGBD possui suas próprias características e é adequado para diferentes tipos de aplicativos, dependendo dos requisitos específicos de armazenamento e acesso aos dados.

Referências
-----------

*   [Documentação oficial do MySQL - ALTER TABLE](https://dev.mysql.com/doc/refman/8.0/en/alter-table.html)
*   [Documentação oficial do MySQL - Data Types](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)



👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/232916898-f877fa84-df49-490b-bf29-a5acb05bb3f6.png)

# **✍️ Funções `DATE(NOW()); CURRENT_TIMESTAMP; CURRENT_DATE;`**


Descrição
---------

Este é um exemplo de código SQL que faz alterações em uma tabela chamada "tb\_baralhos" em um banco de dados. As alterações incluem a modificação da coluna "c\_dtc" para permitir valores nulos e definir um valor padrão para a data atual usando a função "NOW()", bem como adicionar uma coluna "TIMESTAMP" com restrições de não nulo, valor padrão e atualização automática.

Detalhes
--------

### 1\. Modificação da coluna "c\_dtc"

sql

```sql
ALTER TABLE tb_baralhos MODIFY c_dtc DATE NULL;
```

Esta consulta SQL modifica a tabela "tb\_baralhos" e altera a coluna "c\_dtc" para permitir valores nulos, ou seja, não obriga mais que seja informado um valor para esta coluna ao inserir ou atualizar registros na tabela.

### 2\. Modificação da coluna "c\_dtc" com valor padrão

sql

```sql
ALTER TABLE tb_baralhos MODIFY c_dtc DATE NULL DEFAULT DATE(NOW());
```

Esta consulta SQL modifica a tabela "tb\_baralhos" e define um valor padrão para a coluna "c\_dtc" como a data atual obtida pela função "NOW()". Isso significa que se nenhum valor for fornecido para "c\_dtc" durante a inserção de um novo registro, a data atual será automaticamente inserida como valor padrão.

### 3\. Adição de coluna "TIMESTAMP"

sql

```sql
ALTER TABLE tb_baralhos ADD c_timestamp TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP;
```

Esta consulta SQL adiciona uma nova coluna chamada "c\_timestamp" à tabela "tb\_baralhos". Essa coluna é do tipo "TIMESTAMP" e possui as seguintes características:

*   "NOT NULL": Não permite valores nulos, ou seja, é obrigatório informar um valor para esta coluna ao inserir ou atualizar registros na tabela.
*   "DEFAULT CURRENT\_TIMESTAMP": Define o valor padrão como a data e hora atuais quando um novo registro é inserido na tabela.
*   "ON UPDATE CURRENT\_TIMESTAMP": Atualiza automaticamente o valor da coluna para a data e hora atuais sempre que o registro é atualizado.

***👀 Atenção***
-----------

A sintaxe para obter a data atual pode variar dependendo do banco de dados que está sendo utilizado. O uso de `DATE(NOW())` é específico para o MariaDB (ou MySQL), onde a função `NOW()` retorna a data e hora atuais, e a função `DATE()` extrai apenas a parte da data.
Aqui estão alguns exemplos de como obter a data atual em outros bancos de dados populares:

*   PostgreSQL: Utilize a função `CURRENT_DATE` para obter apenas a data atual, ou `CURRENT_TIMESTAMP` para obter a data e hora atuais.

sql

```sql
-- Exemplo de uso do CURRENT_DATE:
ALTER TABLE tb_baralhos MODIFY c_dtc DATE NULL DEFAULT CURRENT_DATE;

-- Exemplo de uso do CURRENT_TIMESTAMP:
ALTER TABLE tb_baralhos ADD c_timestamp TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP;
```

*   Microsoft SQL Server: Utilize a função `GETDATE()` para obter a data e hora atuais, e a função `CAST` para extrair apenas a parte da data.

sql

```sql
-- Exemplo de uso do GETDATE():
ALTER TABLE tb_baralhos MODIFY c_dtc DATE NULL DEFAULT GETDATE();

-- Exemplo de uso do GETDATE() com CAST:
ALTER TABLE tb_baralhos ADD c_timestamp DATETIME NOT NULL DEFAULT CAST(GETDATE() AS DATE);
```

*   Oracle Database: Utilize a função `SYSDATE` para obter a data e hora atuais, e a função `TRUNC` para extrair apenas a parte da data.

sql

```sql
-- Exemplo de uso do SYSDATE:
ALTER TABLE tb_baralhos MODIFY c_dtc DATE NULL DEFAULT SYSDATE;

-- Exemplo de uso do SYSDATE com TRUNC:
ALTER TABLE tb_baralhos ADD c_timestamp DATE NOT NULL DEFAULT TRUNC(SYSDATE);
```

É importante verificar a documentação específica do banco de dados que está sendo utilizado para obter a sintaxe correta para obter a data atual.



<!--  -->

Documentação do Código - Adição de Coluna e Chave Estrangeira
=============================================================

# **✍️ CMD `FOREIGN KEY e Suas Especificações`**

Descrição
---------

Este código é uma série de instruções SQL para adicionar uma coluna chamada "fk\_Marcador" em uma tabela chamada "tb\_baralhos" e, em seguida, criar uma chave estrangeira (foreign key) que faz referência à coluna "idMarcador" da tabela "tb\_marca". A cláusula "NULL" indica que a coluna "fk\_Marcador" pode aceitar valores nulos. Além disso, são definidas as ações de "ON DELETE SET NULL" e "ON UPDATE CASCADE" para a chave estrangeira, indicando o que acontecerá quando registros forem deletados ou atualizados na tabela referenciada.

Código
------

sql

```sql
-- Adiciona coluna para chave estrangeira
ALTER TABLE tb_baralhos ADD fk_Marcador VARCHAR(255) NULL AFTER c_descr;

-- Cria chave estrangeira
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE SET NULL
ON UPDATE CASCADE;
```

Detalhes
--------

*   `ALTER TABLE`: É uma instrução SQL utilizada para alterar a estrutura de uma tabela existente.
*   `tb_baralhos`: É o nome da tabela à qual a coluna e a chave estrangeira estão sendo adicionadas. Você pode substituir esse nome pelo nome da tabela que desejar.
*   `ADD`: É uma cláusula que indica que uma nova coluna está sendo adicionada à tabela.
*   `fk_Marcador`: É o nome da nova coluna que está sendo adicionada, que irá armazenar a chave estrangeira. Você pode substituir esse nome pelo nome que desejar para a coluna.
*   `VARCHAR(255)`: É o tipo de dados da coluna, que é definido como uma string de até 255 caracteres. Você pode ajustar o tamanho máximo da string de acordo com suas necessidades.
*   `NULL`: É a especificação de que a coluna "fk\_Marcador" pode aceitar valores nulos.
*   `AFTER c_descr`: É uma cláusula que indica em qual posição a nova coluna será adicionada em relação às colunas existentes na tabela. Neste caso, a nova coluna será adicionada após a coluna "c\_descr".
*   `ADD CONSTRAINT`: É uma cláusula que permite adicionar uma restrição à tabela, como uma chave estrangeira.
*   `fk_tb_marca`: É o nome da nova chave estrangeira que está sendo criada. Você pode substituir esse nome pelo nome que desejar para a chave estrangeira.
*   `FOREIGN KEY (fk_Marcador)`: É a especificação da coluna "fk\_Marcador" como a chave estrangeira que faz referência à coluna "idMarcador" da tabela "tb\_marca".
*   `REFERENCES tb_marca(idMarcador)`: É a especificação da tabela e coluna que está sendo referenciada pela chave estrangeira.
*   `ON DELETE SET NULL`: É uma especificação de ação que será executada quando registros forem deletados na tabela referenciada. Neste caso, os registros na tabela "tb\_baralhos" terão o valor da coluna "fk\_Marcador" definido como nulo quando os registros correspondentes forem deletados na tabela "tb\_marca".
*   `ON UPDATE CASCADE`: É uma especific




Além das ações "ON DELETE SET NULL" e "ON UPDATE CASCADE", existem outras ações que podem ser usadas em chaves estrangeiras em instruções SQL. Aqui estão algumas delas, juntamente com suas descrições, códigos e detalhes:

1.  `ON DELETE RESTRICT`: Essa ação impede a exclusão de registros na tabela referenciada se houver registros relacionados na tabela que possui a chave estrangeira. Em outras palavras, não permite a exclusão de registros na tabela referenciada enquanto houver registros na tabela que possui a chave estrangeira que fazem referência a esses registros.

sql

```sql
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE RESTRICT
ON UPDATE CASCADE;
```

Detalhes: Se houver registros relacionados na tabela "tb\_baralhos" que possuam a chave estrangeira "fk\_Marcador" referenciando registros na tabela "tb\_marca", a exclusão desses registros na tabela "tb\_marca" será impedida.

2.  `ON DELETE CASCADE`: Essa ação deleta automaticamente registros na tabela que possui a chave estrangeira quando os registros correspondentes na tabela referenciada forem excluídos.

sql

```sql
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE CASCADE
ON UPDATE CASCADE;
```

Detalhes: Quando registros na tabela "tb\_marca" forem excluídos, os registros na tabela "tb\_baralhos" que possuam a chave estrangeira "fk\_Marcador" referenciando esses registros também serão excluídos automaticamente.

3.  `ON DELETE NO ACTION`: Essa ação não permite a exclusão de registros na tabela referenciada se houver registros relacionados na tabela que possui a chave estrangeira. É semelhante a "ON DELETE RESTRICT", mas é menos comum e pode ter comportamentos diferentes em alguns bancos de dados.

sql

```sql
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE NO ACTION
ON UPDATE CASCADE;
```

Detalhes: Se houver registros relacionados na tabela "tb\_baralhos" que possuam a chave estrangeira "fk\_Marcador" referenciando registros na tabela "tb\_marca", a exclusão desses registros na tabela "tb\_marca" será impedida.

4.  `ON DELETE SET DEFAULT`: Essa ação define os valores das colunas da tabela que possui a chave estrangeira como seus valores padrão quando os registros correspondentes na tabela referenciada forem excluídos. No entanto, o uso de valores padrão em chaves estrangeiras pode ser complicado e geralmente não é recomendado.

sql

```sql
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE SET DEFAULT
ON UPDATE CASCADE;
```

Detalhes: Quando registros na tabela "tb\_marca" forem excluídos, os valores das colunas da tabela "tb\_baralhos" que possuam a chave estrangeira "fk\_Marcador" referenciando esses registros serão definidos como seus valores padrão.



5.  `ON UPDATE CASCADE`: Essa ação atualiza automaticamente os valores das colunas na tabela que possui a chave estrangeira quando os valores correspondentes na tabela referenciada forem atualizados.

sql

```sql
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE SET NULL
ON UPDATE CASCADE;
```

Detalhes: Quando registros na tabela "tb\_marca" forem atualizados, os valores das colunas na tabela "tb\_baralhos" que possuam a chave estrangeira "fk\_Marcador" referenciando esses registros serão atualizados automaticamente.

6.  `ON UPDATE RESTRICT`: Essa ação impede a atualização dos registros na tabela referenciada se houver registros relacionados na tabela que possui a chave estrangeira. Em outras palavras, não permite a atualização dos registros na tabela referenciada enquanto houver registros na tabela que possui a chave estrangeira que fazem referência a esses registros.

sql

```sql
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE SET NULL
ON UPDATE RESTRICT;
```

Detalhes: Se houver registros relacionados na tabela "tb\_baralhos" que possuam a chave estrangeira "fk\_Marcador" referenciando registros na tabela "tb\_marca", a atualização desses registros na tabela "tb\_marca" será impedida.

7.  `ON UPDATE NO ACTION`: Essa ação não permite a atualização dos registros na tabela referenciada se houver registros relacionados na tabela que possui a chave estrangeira. É semelhante a "ON UPDATE RESTRICT", mas é menos comum e pode ter comportamentos diferentes em alguns bancos de dados.

sql

```sql
ALTER TABLE tb_baralhos ADD CONSTRAINT fk_tb_marca
FOREIGN KEY (fk_Marcador) REFERENCES tb_marca(idMarcador)
ON DELETE SET NULL
ON UPDATE NO ACTION;
```

Detalhes: Se houver registros relacionados na tabela "tb\_baralhos" que possuam a chave estrangeira "fk\_Marcador" referenciando registros na tabela "tb\_marca", a atualização desses registros na tabela "tb\_marca" será impedida.

8.  `ON UPDATE SET DEFAULT`: Essa ação define os valores das colunas na tabela que possui a chave estrangeira como seus valores padrão quando os registros correspondentes na tabela referenciada forem atualizados. No entanto, o uso de valores padrão em chaves estrangeiras pode ser complicado e 



Descrição
---------

Este código é uma instrução SQL para criar um banco de dados chamado "db\_flashCardBar" utilizando a linguagem PHP. A cláusula "IF NOT EXISTS" verifica se o banco de dados já existe antes de criar um novo, evitando duplicações. O conjunto de caracteres (character set) utilizado é o "utf8mb4" e a colação (collation) é "utf8mb4\_unicode\_ci", que são adequados para suportar caracteres Unicode, incluindo emojis e outros caracteres multibyte.

Código
------

sql

```sql
CREATE DATABASE IF NOT EXISTS db_flashCardBar CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Detalhes
--------

*   `CREATE DATABASE`: É uma instrução SQL utilizada para criar um novo banco de dados no sistema de gerenciamento de banco de dados (SGBD).
*   `IF NOT EXISTS`: É uma cláusula condicional que verifica se o banco de dados já existe antes de criar um novo. Se o banco de dados já existir, a instrução é ignorada, evitando duplicações.
*   `db_flashCardBar`: É o nome do banco de dados que está sendo criado. Você pode substituir esse nome pelo nome que desejar para o seu banco de dados.
*   `CHARACTER SET utf8mb4`: É uma especificação do conjunto de caracteres que o banco de dados deve suportar. "utf8mb4" é um conjunto de caracteres que suporta todos os caracteres Unicode, incluindo emojis e outros caracteres multibyte.
*   `COLLATE utf8mb4_unicode_ci`: É uma especificação da collation, ou seja, a forma como os caracteres são comparados e ordenados. "utf8mb4\_unicode\_ci" é uma collation que trata os caracteres como case-insensitive (não diferencia maiúsculas de minúsculas) e suporta caracteres Unicode.

Referências
-----------

*   [Documentação oficial do MySQL - CREATE DATABASE](https://dev.mysql.com/doc/refman/8.0/en/create-database.html)
*   [Documentação oficial do MySQL - Character Sets and Collations](https://dev.mysql.com/doc/refman/8.0/en/charset-general.html)


# **✍️ CMD `LEFT JOIN` parte 1.0**


Descrição
---------

Este código é uma instrução SQL para realizar uma consulta em um banco de dados utilizando a linguagem PHP. A consulta utiliza a cláusula JOIN para combinar informações de duas tabelas diferentes: "tb\_baralhos" e "tb\_marca". A consulta retorna todas as colunas (\*) das tabelas "tb\_baralhos" e "tb\_marca" para as linhas onde os valores das colunas "fk\_Marcador" em "tb\_baralhos" e "idMarcador" em "tb\_marca" são iguais.

Código+
------

sql

```sql
SELECT tb_baralhos.*, tb_marca.*
FROM tb_baralhos
LEFT JOIN tb_marca
ON tb_baralhos.fk_Marcador = tb_marca.idMarcador;
```

Detalhes
--------

*   `SELECT`: É uma instrução SQL utilizada para selecionar dados de uma ou mais tabelas em um banco de dados.
*   `tb_baralhos` e `tb_marca`: São os nomes das tabelas sendo consultadas. Você pode substituir esses nomes pelos nomes das tabelas reais do seu banco de dados.
*   `.*`: É um curinga que representa todas as colunas das tabelas sendo selecionadas. Neste caso, todas as colunas das tabelas "tb\_baralhos" e "tb\_marca" serão retornadas na consulta.
*   `LEFT JOIN`: É uma cláusula JOIN que combina registros de duas tabelas mesmo quando não há correspondência entre as colunas de junção. Neste caso, todos os registros de "tb\_baralhos" serão retornados, mesmo que não haja correspondência na tabela "tb\_marca".
*   `ON`: É uma cláusula que especifica a condição de junção entre as tabelas. Neste caso, a junção é feita comparando os valores das colunas "fk\_Marcador" em "tb\_baralhos" e "idMarcador" em "tb\_marca".
*   `tb_baralhos.fk_Marcador` e `tb_marca.idMarcador`: São os nomes das colunas sendo comparadas para a junção. Você pode substituir esses nomes pelos nomes reais das colunas de junção nas suas tabelas.

Referências
-----------

*   [Documentação oficial do MySQL - SELECT](https://dev.mysql.com/doc/refman/8.0/en/select.html)
*   [Documentação oficial do MySQL - JOIN Syntax](https://dev.mysql.com/doc/refman/8.0/en/join-syntax.html)


👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/233738686-dc960c16-dd72-4189-9926-10bbffd90dc2.png)


<!-- * -->

# **✍️ CMD `LEFT JOIN` parte 1.1**


Descrição
---------

Este código é uma consulta SQL que utiliza a cláusula "SELECT" para recuperar dados de duas tabelas, "tb\_baralhos" e "tb\_marca", em um banco de dados. A consulta inclui uma junção (JOIN) entre as duas tabelas, especificamente um LEFT JOIN, para combinar registros com base em uma coluna de chave estrangeira (fk\_Marcador) na tabela "tb\_baralhos" e uma coluna de chave primária (idMarcador) na tabela "tb\_marca". A consulta seleciona apenas algumas colunas específicas das tabelas, ou seja, "idBar", "c\_bar", "fk\_Marcador" da tabela "tb\_baralhos" e a coluna "idMarcador" da tabela "tb\_marca".

Motivo de usar apenas algumas colunas das tabelas
-------------------------------------------------

O motivo de selecionar apenas algumas colunas específicas das tabelas na consulta pode ser por questões de eficiência e desempenho. Quando se trabalha com bancos de dados grandes e complexos, selecionar apenas as colunas necessárias pode reduzir a quantidade de dados transferidos entre o banco de dados e a aplicação, economizando recursos de rede e melhorando a performance da consulta. Além disso, selecionar apenas as colunas necessárias pode simplificar o código e torná-lo mais legível.

Código
------

sql

```sql
SELECT tb_baralhos.idBar, tb_baralhos.c_bar, tb_baralhos.fk_Marcador, tb_marca.idMarcador
FROM tb_baralhos
LEFT JOIN tb_marca
ON tb_baralhos.fk_Marcador = tb_marca.idMarcador;
```

Detalhes
--------

*   `SELECT`: É uma instrução SQL utilizada para selecionar colunas específicas de uma tabela.
*   `tb_baralhos`: É o nome da primeira tabela (também conhecida como tabela da esquerda) que está sendo consultada.
*   `idBar`, `c_bar`, `fk_Marcador`: São os nomes das colunas da tabela "tb\_baralhos" que estão sendo selecionadas na consulta.
*   `tb_marca`: É o nome da segunda tabela (também conhecida como tabela da direita) que está sendo junta à tabela "tb\_baralhos".
*   `idMarcador`: É o nome da coluna da tabela "tb\_marca" que está sendo selecionada na consulta.
*   `LEFT JOIN`: É um tipo de junção (JOIN) que retorna todos os registros da tabela da esquerda (tb\_baralhos) e os registros correspondentes da tabela da direita (tb\_marca) com base na condição de junção "tb\_baralhos.fk\_Marcador = tb\_marca.idMarcador". Se não houver correspondências na tabela da direita, NULL será retornado.
*   `ON`: É uma cláusula que especifica a condição de junção entre as tabelas "tb\_baralhos" e "tb\_marca", no caso, a igualdade entre a coluna "fk\_Marcador" da tabela "tb\_baralhos" e a coluna "idMarcador" da tabela "tb\_marca".

Referências
-----------

*   [Documentação oficial do MySQL - SELECT](https://dev.mysql.com/doc/refman/8.0/en/select.html)
*   \[Documentação oficial do MySQL - JOIN Syntax\]([https://dev.mysql.com/doc/refman/8.0](https://dev.mysql.com/doc/refman/8.0)

👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/233739380-b45a21f0-4481-4f92-9274-dbb63117d1cf.png)

# **✍️ CMD `LEFT JOIN` parte 1.2**


Descrição
---------

Este código é uma consulta SQL que busca dados de duas tabelas relacionadas, "tb\_baralhos" e "tb\_marca", utilizando uma junção (JOIN) interna (inner JOIN). A consulta retorna as colunas "idBar", "c\_bar", "fk\_Marcador" da tabela "tb\_baralhos" e a coluna "idMarcador" da tabela "tb\_marca". Essa consulta é utilizada para obter dados de baralhos e seus respectivos marcadores em um sistema CRUD (Create, Read, Update, Delete) em PHP utilizando o padrão de arquitetura MVC (Model-View-Controller).

Código
------

sql

```sql
SELECT tb_baralhos.idBar, tb_baralhos.c_bar, tb_baralhos.fk_Marcador, tb_marca.idMarcador
FROM tb_baralhos
INNER JOIN tb_marca
ON tb_baralhos.fk_Marcador = tb_marca.idMarcador;
```

Detalhes
--------

*   `SELECT`: É uma instrução SQL utilizada para selecionar os dados a serem retornados pela consulta.
*   `tb_baralhos`: É o nome da tabela "tb\_baralhos" da qual os dados estão sendo selecionados.
*   `tb_marca`: É o nome da tabela "tb\_marca" que está sendo utilizada na junção (JOIN) com a tabela "tb\_baralhos".
*   `idBar`, `c_bar`, `fk_Marcador`: São as colunas da tabela "tb\_baralhos" que estão sendo selecionadas na consulta.
*   `idMarcador`: É a coluna da tabela "tb\_marca" que está sendo selecionada na consulta.
*   `INNER JOIN`: É um tipo de junção (JOIN) que retorna apenas os registros que têm correspondência em ambas as tabelas ("tb\_baralhos" e "tb\_marca") com base na condição de junção especificada.
*   `ON`: É uma cláusula que especifica a condição de junção entre as tabelas "tb\_baralhos" e "tb\_marca". Neste caso, a condição é que a coluna "fk\_Marcador" da tabela "tb\_baralhos" seja igual à coluna "idMarcador" da tabela "tb\_marca".

Referências
-----------

*   [Documentação oficial do MySQL - SELECT](https://dev.mysql.com/doc/refman/8.0/en/select.html)
*   [Documentação oficial do MySQL - JOIN Syntax](https://dev.mysql.com/doc/refman/8.0/en/join.html)

![image](https://user-images.githubusercontent.com/93455937/233740804-f44ec465-de24-4dd5-ad48-cf1587adfa24.png)



<!-- ** -->

# **✍️ CMD `LEFT JOIN` parte 1.3**

Descrição
---------

Este código é uma instrução SQL para criar um banco de dados chamado "db\_flashCardBar" utilizando a linguagem PHP. A cláusula "IF NOT EXISTS" verifica se o banco de dados já existe antes de criar um novo, evitando duplicações. O conjunto de caracteres (character set) utilizado é o "utf8mb4" e a colação (collation) é "utf8mb4\_unicode\_ci", que são adequados para suportar caracteres Unicode, incluindo emojis e outros caracteres multibyte.

Código
------

sql

```sql
CREATE DATABASE IF NOT EXISTS db_flashCardBar CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Detalhes
--------

*   `CREATE DATABASE`: É uma instrução SQL utilizada para criar um novo banco de dados no sistema de gerenciamento de banco de dados (SGBD).
*   `IF NOT EXISTS`: É uma cláusula condicional que verifica se o banco de dados já existe antes de criar um novo. Se o banco de dados já existir, a instrução é ignorada, evitando duplicações.
*   `db_flashCardBar`: É o nome do banco de dados que está sendo criado. Você pode substituir esse nome pelo nome que desejar para o seu banco de dados.
*   `CHARACTER SET utf8mb4`: É uma especificação do conjunto de caracteres que o banco de dados deve suportar. "utf8mb4" é um conjunto de caracteres que suporta todos os caracteres Unicode, incluindo emojis e outros caracteres multibyte.
*   `COLLATE utf8mb4_unicode_ci`: É uma especificação da collation, ou seja, a forma como os caracteres são comparados e ordenados. "utf8mb4\_unicode\_ci" é uma collation que trata os caracteres como case-insensitive (não diferencia maiúsculas de minúsculas) e suporta caracteres Unicode.

Referências
-----------

*   [Documentação oficial do MySQL - CREATE DATABASE](https://dev.mysql.com/doc/refman/8.0/en/create-database.html)
*   [Documentação oficial do MySQL - Character Sets and Collations](https://dev.mysql.com/doc/refman/8.0/en/charset-general.html)



# **✍️ CMD `LEFT JOIN` parte 1.4**


Descrição
---------

Este código é uma consulta SQL para recuperar dados de duas tabelas, "tb\_baralhos" e "tb\_marca", utilizando uma cláusula LEFT JOIN para combinar os dados com base em uma coluna de relação "fk\_Marcador" em "tb\_baralhos" e "idMarcador" em "tb\_marca". A consulta é filtrada usando uma cláusula WHERE para retornar apenas os registros onde o valor da coluna "c\_bar" em "tb\_baralhos" é igual a 'Baralho #001'.

Código
------

sql

```sql
SELECT tb_baralhos.idBar, tb_baralhos.c_bar, tb_baralhos.fk_Marcador, tb_marca.idMarcador
FROM tb_baralhos
LEFT JOIN tb_marca
ON tb_baralhos.fk_Marcador = tb_marca.idMarcador
WHERE tb_baralhos.c_bar = 'Baralho #001';
```

Detalhes
--------

*   `SELECT`: É uma instrução SQL utilizada para recuperar dados de uma ou mais tabelas de um banco de dados.
*   `tb_baralhos`: É o nome da primeira tabela ("tb\_baralhos") da qual os dados estão sendo recuperados.
*   `tb_marca`: É o nome da segunda tabela ("tb\_marca") que é combinada com "tb\_baralhos" usando a cláusula LEFT JOIN.
*   `idBar`, `c_bar`, `fk_Marcador`, `idMarcador`: São os nomes das colunas específicas que estão sendo selecionadas para recuperar os dados. Você pode adicionar ou remover colunas conforme necessário para atender aos requisitos de sua aplicação.
*   `LEFT JOIN`: É uma cláusula que combina as linhas de duas tabelas com base em uma coluna de relação ("fk\_Marcador" em "tb\_baralhos" e "idMarcador" em "tb\_marca"). Se não houver correspondência na tabela "tb\_marca", NULL será retornado.
*   `ON`: É uma cláusula que especifica a condição de junção entre as tabelas "tb\_baralhos" e "tb\_marca".
*   `WHERE`: É uma cláusula que filtra os resultados com base em uma condição específica. Neste caso, apenas os registros onde o valor da coluna "c\_bar" em "tb\_baralhos" é igual a 'Baralho #001' serão retornados.
*   `--`: É uma notação de comentário em SQL. Neste caso, a linha que inicia com "--" é um comentário que pode ser usado para adicionar notas ou observações ao código SQL.

Referências
-----------

*   [Documentação oficial do MySQL - SELECT](https://dev.mysql.com/doc/refman/8.0/en/select.html)
*   [Documentação oficial do MySQL - JOIN Syntax](https://dev.mysql.com/doc/refman/8.0/en/join.html)

👉Resultado
---------
![image](https://user-images.githubusercontent.com/93455937/233741913-31db7fde-9926-4adb-8090-47a6df5b6704.png)