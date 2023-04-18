
Documentação do Código - Criação de Banco de Dados
==================================================

Comando básico para criação e manipulação de um banco de dados com imagens ilustrativas

# **CREATE DATABASE IF NOT EXISTS**

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


# **CMD `USE`**

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