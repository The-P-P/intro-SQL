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

  > tabela cliente
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
  
  >tabela produtos
  ![tabela produtos](https://user-images.githubusercontent.com/86755845/207202160-ff12fe62-1aff-40ef-8668-c67bb2965d08.png)
  
  > apagando tavela 
  ```
  DROP TABLE (nome da tabela);
  ```
  >inserir um registro na tabela
  ``` 
  USE sucos;

  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES (
  '1040107', 'Light - 350 ml - Melância',
  'Lata', '350 ml', 'Melância', 4.56);
  ```
  >inserir diversos produtos na tabela
  ``` 
  USE sucos;

  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES (
  '1037797', 'Clean - 2 Litros - Laranja',
  'PET', '2 Litros', 'Laranja', 16.01);

  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES (
  '1000889', 'Sabor da Montanha - 700 ml - Uva',
  'Garrafa', '700 ml', 'Uva', 6.31);

  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES (
  '1004327', 'Videira do Campo - 1,5 Litros - Melância',
  'PET', '1,5 Litros', 'Melância', 19.51);

  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES
  ('544931', 'Frescor do Verão - 350 ml - Limão', 'PET', '350 ml','Limão',3.20);

  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES
  ('1078680', 'Frescor do Verão - 470 ml - Manga', 'Lata', '470 ml','Manga',5.18);
  ```
  >alterar algumas informações dos registros acima
  ```
  USE sucos;

  UPDATE tbproduto SET EMBALAGEM = 'Lata', PRECO_LISTA = 2.46
  WHERE PRODUTO = '544931';

  UPDATE tbproduto SET EMBALAGEM = 'Garrafa'
  WHERE PRODUTO = '1078680';
  ```
  
  >excluir registros já existentes na tabela
  ```
  USE sucos;

  DELETE FROM tbproduto WHERE PRODUTO = '1078680';
  ```
  >criar uma chave primária
  ```
  USE sucos;

  ALTER TABLE tbproduto ADD PRIMARY KEY (PRODUTO);
  ```
  >Execute o comando abaixo duas vezes
  ```
  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES
  ('1078680', 'Frescor do Verão - 470 ml - Manga', 'Lata', '470 ml','Manga',5.18);

  INSERT INTO tbproduto (
  PRODUTO,  NOME, EMBALAGEM, TAMANHO, SABOR,
  PRECO_LISTA) VALUES
  ('1078680', 'Frescor do Verão - 470 ml - Manga', 'Lata', '470 ml','Manga',5.18);
  ```
* Note que, da segunda vez, o comando não pode ser executado apresentando erro porque viola a chave primária.
  >Caso você deseje mudar algo neste registro deve altera-lo
  ```
  UPDATE tbproduto SET EMBALAGEM = 'Garrafa'
  WHERE PRODUTO = '1078680';
  ```
  >inclua uma chave primária na tabela de clientes
  ```
  USE sucos;

  ALTER TABLE tbcliente ADD PRIMARY KEY (CPF);
  ```
  
  >incluir novas colunas 
  ```
  ALTER TABLE tbcliente ADD COLUMN (DATA_NASCIMENTO DATE);
  ```
  > inclusão de um campo do tipo data (DATA_NASCIMENTO) e do tipo lógico (PRIMEIRA_COMPRA)
  ```
  INSERT INTO tbcliente (
  CPF, NOME, ENDERECO1, ENDERECO2, BAIRRO, CIDADE, ESTADO, CEP, IDADE, SEXO, 
  LIMITE_CREDITO, VOLUME_COMPRA, PRIMEIRA_COMPRA, DATA_NASCIMENTO)
  VALUES ('00388934505','João da Silva','Rua projetada A número 10','',
  'VILA ROMAN', 'CARATINGA', 'AMAZONAS','2222222',30,'M', 10000.00, 2000,
  0, '1989-10-05');
  ```
