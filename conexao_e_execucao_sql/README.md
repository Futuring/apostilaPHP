# Conexão e Execução SQL

Podemos realizar a conexão e execução de nossas query criando uma classe como demonstrado por Bruno Russo ou utilizando a extensão MYSQLI, observem que Bruno utilizasse da OO com as funções padrões de conexão PHP / MySQL e que para utilização da extensão mysqli teremos que alterar configurações do arquivo `php.ini`.
Vamos aos exemplos:
Para demonstramos a conexão do PHP com o MySQL dentro de OO com funções nativas de conexão PHP / MySQL, utilizaremos o código de Bruno Russo disponível em:
http://www.brunorusso.eti.br/dicas/mysql/classe-para-conectar-php-com-mysql.

**Arquivo da classe: conecta.php**
```php
<?php
  class CONEXAO
  {
          var $usuario = "user";
          var $senha = "password";
          var $sid = "localhost";
          var $banco = "database";
          var $consulta = "";
          var $link = "";
function CONEXAO()
  	{
 		$this->Conecta();
  	}
  	function Conecta()
  	{
  		$this->link = mysql_connect($this->sid,$this->usuario,$this->senha);
  		if (!$this->link)
  		{
  			die("Problema na Conexão com o Banco de Dados");
  		}
  		elseif (!mysql_select_db($this->banco,$this->link))
  		{
  			die("Problema na Conexão com o Banco de Dados");
  		}
  	}

function Desconecta()
  	{
  		return mysql_close($this->link);
  	}
function Consulta($consulta)
  	{
          	$this->consulta = $consulta;
  		if ($resultado = mysql_query($this->consulta,$this->link))
  		{
  			return $resultado;
} else {
  			return 0;
  		}
  	}
  }
  ?>
```

Arquivo que chama a classe para conexão:

**consulta.php**
```php
  <?php
  include 'conecta_banco.php';
  $Obj_Conexao = new CONEXAO();
  $pega_dados = $Obj_Conexao->Consulta("select * from CADASTRO");
$retorno = mysql_num_rows($id);
  if($retorno == 0 )
  {
          print("<center>Erro ao carregar as informações !!<br>");
          return 0;
  }  else  {
for ($i = 0; $i < $retorno; ++$i)  {
                  $linha = mysql_fetch_array($pega_dados);
                  $id = $linha[1];
                  $nome = $linha[1];
                  print("$id - $nome");
          }
  }
  $Obj_Conexao->Consulta;
?>
```
Já para utilização do MySQLi primeiramente abriremos o arquivo php.ini e iremos descomentar a linha referente a extenção do mysqli ou caso não a encontremos iremos adicioná-la.

`Extension = php_mysqli.dll`

Agora que já editamos o arquivo php.ini é imprescindível que reiniciamos o Apache e o MySQL afim de que possamos começar a utilizar os recursos da extensão mysqli ou a classe mysqli, para uma listagem de todos os métodos consultar o site oficial do PHP (php.net) http://php.net/manual/pt_BR/book.mysqli.php.

Vamos utilizar alguns destes métodos agora, começaremos por estabelecer e terminar uma conexão, para isso precisa-se instanciar a classe mysqli por meio de um construtor o que é bem parecido com o da função `mysql_connect()`, e que ficará assim:

```php
//instacia a classe mysqli
$mysqli = new mysqli();
//conectando apenas ao servidor
$mysqli = new mysqli(“SERVIDOR”, “USUARIO”, “SENHA”);
//Selecionando uma base de dados
$mysqli->select_db(“BASE_DE_DADOS”);
//conectando ao servidor e a base de dados
$mysqli->connect(“SERVIDOR”, “USUARIO”, “SENHA”, “BASE_DE_DADOS”);
//fechando a conexão
$mysqli->close();
````

Vamos ver um pouco de como trabalhar com possíveis erros na interação com a base de dados, para isso utilizaremos o método `error()` que retorna a mensagem de erro gerada no banco ou retornara vazia caso não haja erro na interação com o banco.

Segundo GILMORE (2008), o idioma dependerá do servidor de banco de dados MySQL pois o Servidor de Banco utilizara o idioma do Servidor ao qual está instalado.
Vamos ao exemplo de utilização do método:

```php
<?php
	// conectando a base
	$myslqi = new mysqli (“SERVIDOR”, “USUARIO”, ”SENHA”, “BASE_DE_DADOS”);
	if ($mysqli -> errno){
		echo (“Não é possível conectar ao banco de dados: <br /> ”. $mysqli->error);
		exit();
	}
?>
```

O exemplo acima retornará quando a senha fornecida não for à correta e ficará assim na tela, caso o servidor tenha como língua o inglês:

Não é possível conectar ao banco de dados:
`Access denied for user ‘catalog_user’ @ ‘localhost’ (using password: YES)`

Vamos ver agora um pouco de consulta, inserção, atualização e deleção. Ao fazer uma consulta na base de dados temos que ter conscientes de que o retorno pode ser grande caso nossa query não tenha clausulas “where” para filtrar no banco o conjunto a ser retornado, isso consumirá muitos recursos no servidor e tornará a aplicação lenta. Então como controlaremos isto? A resposta esta no parâmetro opcional do método query que pode ser o `MYSQL_STORE_RESULT` (padrão) este retorna todas as linhas da consulta, ou o `MYSQLI_USE_RESULT` que retornará apenas uma parte do resultado da query assim aumentando o desempenho da aplicação.

**UTILIZANDO MYSQL_STORE_RESULT**

```php
<?php

    $mysqli = new mysqli('SERVIDOR', 'USUARIO', 'SENHA', 'BASE_DE_DADOS');

    // Criando a query
    $query = 'SELECT * FROM produtos ORDER by nome';

    // enviando a query para MySQL
    $result = $mysqli->query($query, MYSQLI_STORE_RESULT);

    // Escrevendo o resultado na tela
    while(list($codigo, $nome, $preco) = $result->fetch_row())
        printf("(%s) %s: \$%s <br />", $codigo, $nome, $preco);

?>
```

**UTILIZANDO MYSQLI_USE_RESULT**

```php
<?php
$mysqli = new mysqli("localhost", "my_user", "my_password", "world");

/* utilizando o parametro MYSQLI_USE_RESULT */
if ($result = $mysqli->query("SELECT * FROM produto", MYSQLI_USE_RESULT)) {
    if (!$mysqli->query("SET @a:='ainda está trabalhando'")) {
        printf("Erro: %s\n", $mysqli->error);
    }
    $result->close();
}

$mysqli->close();
?>
```

Criando uma inserção na base de dados:

```php
<?php
    // Criando a conexao com o banco
    $mysqli = new mysqli('SERVIDOR', 'USUARIO', 'SENHA', 'BASE_DE_DADOS');

    // Criando o insert
    $query = "INSERT INTO produtos SET id=NULL, codigo=?, nome=?, preco=?";

    // Criando o objeto de preparação
    $stmt = $mysqli->stmt_init();

    // Preparando o objeto para execucao
    $stmt->prepare($query);

    // passando os paramentros
    $stmt->bind_param('ssd', $codigo, $nome, $preco);

    // atribuindo o codigo a matriz codigo
    $codigoarray = $_POST['codigo'];

    // atribuindo o nome a matriz nome
    $nomearray = $_POST['nome'];

    // atribuindo o preco a matriz preco
    $precoarray = $_POST['preco'];

    // iniciando o contador $x
    $x = 0;

    // Percorre o array e executa a query iterativamente
    while ($x < sizeof($codigoarray)) {
        $codigo = $codigoarray[$x];
        $nome = $nomearray[$x];
        $preco = $precoarray[$x];
        $stmt->execute();

    }

    // Recupera os recursos da execução
    $stmt->close();

    // Fechando a conexao
    $mysqli->close();

?>
```

**Criando um UPDATE:**

```php
$query = "UPDATE produtos SET preco = '39.99' WHERE preco = '34.99'";
$result = $mysqli->query($query);
```

**Criando uma deleção:**

```php
<?php

    $mysqli = new mysqli('SERVIDOR', 'USUARIO', 'SENHA', 'BASE_DE_DADOS');

    // Criando a query
    $query = "DELETE FROM produtos WHERE codigo = 'TY232278'";

    // enviando a query para o MySQL
	    $result = $mysqli->query($query, MYSQLI_STORE_RESULT);
    // Informar ao usuário quantas linhas foram afetadas
    printf("%d linhas foram excluídas.", $mysqli->affected_rows);
?>
``
