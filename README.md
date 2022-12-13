# intro-SQL
Estudo sobre SQL com MySQL, manipulando e consultado dados - instrutor Victorino Vila
##

🎈 introducao

* Banco de dados 
  > diversas entidades 
    * tabelas (main) 
      * campos e registros 
      * chaves e primaria
      * chaves estrangeiras (*)
      * indice
    * esquemas
    * view
      * consulta
    * procedures
      * funcoes
        ``` if a > 0 then
            X = x + y
            Z = instr ( z+1 )
            select * from apha
            put alpha in tablex
        ```
    * trigger
  ##
   > comandos iniciais 
   
   ```
   SELECT * FROM CITY;
   SELECT * FROM COUNTRY;
   
   ```
   ##
    > exemplo de criacao de um BD
    
   ```
   CREATE {DATABASE | SCHEMA} [IF NOT EXISTS] db_name
      [create_specification]

   create_specification:
            [DEFAULT] CHARACTER SET [=] charset_name
            [DEFAULT] COLLATE [=] collation_name
            DEFAULT ENCRYPTION [=] { 'Y' | 'N'}
   
   ```
   ##
   
   > criando e deletando
   
   ```
   CREATE SCHEMA `sucos2` DEFAULT CHARACTER SET utf8;
   DROP {DATABASE | SCHEMA} [IF EXISTS] db_name
   DROP DATABASE SUCOS;
   ```
   ##
   
   > acessando o mysql pelo cmd
   
   ```
   C: \program files>cd “mysql server 8.0>cd bin>dir mysql.exe
   mysql -h localhost -u root -p
   ```
   ##
   > criando tabelas
   
    |tipo |valor em bytes|menor valor (-)|menor valor|maior valor (-)|maior valor|
    |---|---|---|---|---|---|
    |TINYINT|  1 |-128| 0  |127|255|
    |SMALLINT|  2 |-32768| 0  |32767	|65535 |
    |MEDIUMINT| 3  |-8388608	| 0  |8388607| 16777215|
    |INT| 4  |  -2147483648	| 0 |2147483647|4294967295 |
    |BIGINT| 8  | -2xE63	| 0  | 2xE63 |2xE64-1 |

    * ponto float 
      * FLOAT : precisao simples ( 4bytes )
      * DOUBLE : precisao dupla ( 8 bytes )
      * exemplo: float (7,4) =  999,00009 --> 999,0001 ( arrendonda )
    * fixos
      *  decimal ou numeric: (5,2) = -999,99 between 999,99
    * BIT
      * bit 1 = 1 ou 0
      * bit 2 = 01, 10, 00, 11
      * tamho ate 64 bits
    * signed ou unsigned
      * possui ( - ) ou nao 
    * zerofil
      * preenche com 0 os espacos 
    * auto_increment 
      * sequencia auto incrementada  
    * erros de out of range
      * ocorre quando os valores estouram os limites
    * data e hora
      * date = AA/MM/DD
      * datetime = 1000-01-01 00:00:00 ate 9999-12-31 23:59:59
      * timestamp = 1970-MM-DD H:M:S ate 2038-01-19 (UTC)
      * time --  -838:59:59 e 839:59:59
      * year - 1901 - 2155 ( 2 ou 4 digitos )
    * strings
      * char - valor fixo de caracteres
      * varchar - valor variado
      * binary - caracteres fixos de binarios
      * varbinary - caracteres variados de binarios
      * blob - tinyblob; blob; mediumblob; longblob; ( binarios )
      * text - tinytext; text; mediumtext; longtext; ( textos )
      * enum - armazena lista pre-definidas de valores
      * set e collate - conjunto de caracteres suportados 
    * spacial
      * geometry
      * point
      * linestring
      * polygon
##

  > primeiro banco de dados
  ```
CREATE TABLE tbcliente
( CPF VARCHAR (11) ,
NOME VARCHAR (100) ,
ENDERECO1 VARCHAR (150) ,
ENDERECO2 VARCHAR (150) ,
BAIRRO VARCHAR (50) ,
CIDADE VARCHAR (50) ,
ESTADO VARCHAR (2) ,
CEP VARCHAR (8) ,
IDADE SMALLINT,
SEXO VARCHAR (1) ,
LIMITE_CREDITO FLOAT ,
VOLUME_COMPRA FLOAT ,
PRIMEIRA_COMPRA BIT (1));
  ```
