# Herança

O que torna a orientação a objetos única é o conceito de herança que no inglês significa inheritence.
Herança é um mecanismo que permite que características comuns a diversas classes com comportamentos comuns ou parecidos, sejam abstraídas e centralizadas em uma classe base, ou superclasse. Tem uma relação “É um”.
A partir dessa superclasse outras classes podem ser especificadas. Portanto uma subclasse que é uma classe herdada da superclasse recebe sem codificação extra as características da superclasse. Ainda podemos adicionar elementos particulares a está subclasse.
A palavra extends caracterizará a herança da classe CARRO com a classe VEICULO, como podemos ver abaixo:

```php
<?php
class Veiculo
{
	public $marcha;

	public $quantidadeRodas;

	public function passarMarcha()
	{
		// código
	}

	public function andar()
	{
		// código
	}
}

class Carro extends Veiculo
{
	public function __construct()
	{
		$this->quantidadeRodas = 4;
	}
}

$carro = new Carro();
$carro->andar();
?>
```
