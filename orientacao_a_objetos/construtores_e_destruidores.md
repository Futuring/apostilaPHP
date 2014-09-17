# Construtores e Destruidores

Em certos momentos precisamos executar algo no momento em que uma classe é instanciada. Às vezes é necessário setar valores padrões a algumas propriedades, realizar cálculos, etc.
Para isso existe o método construtor, que no PHP é chamado através da palavra chave `__construct`. Toda vida que uma classe é instanciada o PHP busca pelo método `__construct` e o chama caso seja encontrado. O método construtor não é obrigatório, por tanto sua classe instanciará normalmente se você não declará-lo.
Ao instanciar classes é possível passar para ela parâmetros. Esses parâmetros são repassados para o construtor. Veja o exemplo:
```php
<?php
class Produto
{
	public $codigo;

	public $nome;

	public $quantidade;

	/**
           * Construtor
           */
	public function __construct( $codigo, $nome, $quantidade )
	{
		$this->codigo = $codigo;
		$this->nome = $nome;
		$this->quantidade = $quantidade;
	}
}

$produto1 = new Produto( 1, "CD Nine Inch Nails " With Teeth", 4 );
$produto2 = new Produto( 2, "CD A Perfect Circle " Mer De Noms", 3 );
?>
```
Também temos os destrutores que no PHP são chamados através da palavra chave __destruct. Ao contrario dos construtores, os destrutores são chamados quando um objeto é destruído, por exemplo:

```php
<?php
class MinhaClasse
{
	public function __destruct()
	{
		trigger_error( 'Por favor, não me destrua!!!!' );
	}
}

$objetoMinhaClasse = new MinhaClasse();

unset( $objetoMinhaClasse ); // dispara o erro
?>
```
