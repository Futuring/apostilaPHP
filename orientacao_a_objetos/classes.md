# Classes

Entendido todos os conceitos acima fica fácil entender o que é uma classe. Como na vida real existem diversos objetos do mesmo tipo, nos softwares também é assim. Imagine o sistema de gerenciamento de veículos do Detran. Quantos objetos do tipo carro este sistema deve manipular por dia? Se fosse feita uma descrição para cada um, o sistema jamais iria funcionar.

Assim, podemos descrever um mesmo tipo de objetos uma única vez e cada vez que um novo objeto precise ser criado, é só utilizar a mesma fôrma. Esta fôrma é chamada classe.

Pense em uma padaria, quando você vai escolher bolos se depara com muitos bolos idênticos. Ai você se pergunta, seria o padeiro capaz de produzir tantos bolos com a mesma forma apenas usando as mãos?NÃO! Ele usou uma fôrma para fazer estes bolos, a fôrma foi o molde que ele queria para seus bolos. Com os objetos não é diferente, as classes são os moldes (modelos, fôrmas, plantas) para criação dos os objetos em tempo de execução dos programas.

Ainda tem mais, uma classe é a descrição de um conjunto de objetos que possuem os mesmos atributos, operação e semântica. Dizemos que um objeto é uma instância de uma classe, quando ele é criado a partir dela, seguindo sua especificação.

Para que um objeto seja criado é necessário definirmos sua estrutura. A estrutura de um objeto são todas as suas características e possíveis ações que também são baseadas na vida real. Por exemplo, um carro possui como características: Cor, ano, modelo, marca, etc, e possui como ações: andar, parar, dar ré, ligar e desligar.

###Classe

Para definirmos essa estrutura criamos algo que chamamos de Classe. Ela é a estrutura fundamental para a criação de objetos. É como se fosse um template para os objetos, onde todas as suas características e ações são especificadas e com isso ser possível criar N objetos diferentes. Diferente no sentido de dados e informações armazenadas, mas sua estrutura (definida na classe) é sempre igual.

Dentro de uma classe todas as suas características são chamadas de propriedades, enquanto suas ações são chamadas de métodos.
Para se definir uma classe é preciso basicamente utilizar a seguinte estrutura:
```php
<?php
class Produto
{
	// propriedades
	public $codigo;

	public $nome;

	public $preco;

	// métodos
	public function calculaDezporcento()
	{
		return $this->preco * 0.10;
	}
}
?>
```

Note que dentro de uma classe as propriedades são como variáveis e os métodos são como funções. A palavra chave public é utilizada para definir o tipo de acesso das propriedades e dos métodos (Veja o capitulo 5, Encapsula mento).
Usamos também a palavra chave $this, que serve para dentro de um método chamar uma propriedade da classe.
Para acessarmos as propriedades e os métodos dessa classe é simples. É só seguir o exemplo:
```php
<?php
$produto = new Produto();
$produto->preco = 1200;
echo $produto->calculaDezPorcento(); // imprime 120
?>
```
