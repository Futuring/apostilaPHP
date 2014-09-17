# PDO - Introdução e Conceitos

Segundo Nunes (2007) PDO é uma extensão do PHP 5 para formalizar conexões com uma base de dados de maneira uniforme. Assim o programador cria um código portátil através de várias bases de dados e plataformas, ou seja, é possível alterar a base de dados mudando apenas uma linha de código, lembrando que para utilização desta extensão é necessário alterar configurações no arquivo `php.ini`.

Vamos aos exemplos:
Para demonstramos a conexão com o banco de dados através da extensão PDO do PHP utilizaremos o código de Adilson Santos Rocha disponível em:
http://www.htmlstaff.org/ver.php?id=18411.

Para conexão com a base de dados são necessários os parâmetros básicos: host, usuário, senha e nome do banco. Isto tanto para MySQL, PostgreSQL ou outros bancos.

A conexão é feita através da instância da classe PDO. Passando para seu construtor os parâmetros necessários para a conexão. Ex:
```php
<?php
try {
// Instanciando objeto com dados de conexão
$db = new PDO("pgsql:host=localhost dbname=sistema user=postgres password=bananaamassada");
} catch (PDOException  $e) {
print $e->getMessage();
}
?>
```
No exemplo acima a variável `$db` recebe uma instância de um objeto PDO, e através dele pode-se executar vários métodos, trabalhar com transações, preparar e executar "queries", modificar alguns atributos da classe, etc.
Executando query:

Após ter se conectado a base de dados podemos utilizar alguns dos métodos da PDO para executar nossas "queries", o próprio método "query" pode ser utilizado, porém opções como prepare e execute tornam seu uso muito mais flexível e inteligente.

A execução de uma query vai retornar um outro objeto o Statement.

Segundo Adilson Santos Rocha os objetos Statements são o resultado da execução ou da preparação para execução de uma query e provêem vários métodos para obter-se informações sobre a query e sua execução. Métodos para "fetch", pegam informações sobre as colunas, linhas entre outros. Recursos semelhantes com os que utiliza-se nas funções nativas mysql e pgsql nas quais um resultset é passado como parâmetro, ex:

```php
mysql_num_rows($resultset).
```
Segundo Adilson Santos Rocha compor “queries” exige um esforço grande em concatenar e "escapar" strings, formatar valores de acordo com o tipo do campo entre outros. Ex:

```php
<?php
	// Query de inserção
$sql= "INSERT INTO produtos (produ_nome, grupo_id, categ_id, produ_detalhe, produ_fotos) VALUES ( ". addslashes("Teclado ABNT2 mobil 'T" )".",'2','1',addslashes($detalhe),"tec.png")";
// Executando a query
$rs = $db->query($sql);
?>
````

No exemplo acima a query utilizada pode ser executada normalmente no mysql, mas em outros bancos pode ocorrer problemas com os campos `grupo_id` e `categ_id`, que são inteiros e estão entre apóstrofes. Além de o programador ter que preocupar-se com o escape das strings e outros fatores.

Uma medida que ameniza e evita muitos problemas é a utilização dos prepared statements através do uso do método prepare da PDO. Ex:

```php
<?php
try {
$res = $db->prepare(INSERT INTO produtos (produ_nome, grupo_id, categ_id, produ_detalhe, produ_fotos)  VALUES  (?, ?, ?, ?, ?);
$valores = array("Teclado ABNT2 mobil 'T",2,1,$detalhe, tec.png');
$res->execute($valores);
} catch ( PDOException  $e) {
print "Erro: Código:" . $e->getCode() . "Mensagem" . $e->getMessage();
}
?>
```
Note que no exemplo acima não houve nenhuma preocupação em cuidar de apóstrofes e nem se o valores são strings, inteiros ou reais. Apenas preparamos uma query para a execução e passamos 5 parâmetros "?" e logo em seguida a query é executada com o método execute onde um array com os valores na ordem dos campos a ser inseridos "?". Dessa forma a query funcionaria independente do banco, a PDO cuidaria de tratar os dados. O desenvolvedor preocupa-se apenas para que os dados sejam enviados na ordem correta para o método execute.
O mesmo procedimento pode ser utilizado em outras instruções sql como Update e Selects.

Executando uma consulta no banco de dados:

A técnica citada anteriormente também facilita na recuperação de dados, uma vez que não há a necessidade de verificar tipos de dados escapes, etc. Ex:

```php
<?php
	// Query de consulta
$sql = "SELECT * FROM produtos WHERE produ_id = ?";
try {
   		$res  = $db->prepare($sql);
   		$res->execute(array($produ_id));
} catch ( PDOException  $e) {
print "Erro: Código:" . $e->getCode() . "Mensagem" . $e->getMessage();
}
?>
```
No exemplo acima o `$res` é um objeto da classe Statement com métodos e atributos. Normalmente esse tipo de objeto nos desperta apenas alguns interesses, os dados retornados, o número de linhas e as colunas retornados.
Para acessar os dados retornados podemos utilizar os métodos `fetch`, `fetchObjetc` ou `fetchAll`.
O método `fetch retorna a linha ativa do statement na forma de um array onde os valores podem ser acessados pelo número da coluna iniciando em 0 (zero) ou o nome da coluna.
O método `fetchAll` que retorna um array indexado de 0 ao número de linhas retornadas, e cada item desse array é um outro array exatamente como o retornado pelo método fetch.
Já o método `fetchObject` retorna um objeto com a linha ativa do resultset tendo as colunas como propriedades.
