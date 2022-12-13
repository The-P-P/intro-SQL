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
   
   
