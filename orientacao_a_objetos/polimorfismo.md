# Polimorfismo

Analisando a palavra Polimorfismo, ela significa muitas formas. Ou seja, para uma árvore de herança, temos muitas formas de objetos e métodos a partir de uma superclasse e suas subclasses. Polimorfismo é o princípio pelo qual usamos objetos construídos a partir de uma árvore de herança, através de referências do tipo de uma superclasse da hierarquia.

Formas de polimorfismo:
* Subclasses;
* Sobrescrita de método;
* Sobrecarga de método ou construtor
* Sobrescrita de métodos – Overriding

Esta utilidade nos permite escrever numa subclasse um ou mais métodos presentes numa das superclasses podendo alterar o comportamento da superclasse.
Quando numa subclasse reescrevemos um método já existente numa superclasse, chamamos de sobrescrita de método ou reescrita de método, mas o termo técnico é Method Overriding. Lembrando que a sobre-escrita de métodos só é valida quando o método reescrevido na subclasse tem exatamente a mesma identificação (nome, tipos, etc.) do método da superclasse.
Abaixo temos uma classe para cheque comum que possui um método para calcular juros de 25% e logo após teremos uma classe para cheque especial que terá o mesmo método para calcular juros de 10%.
```php
<?php
class ChequeComum
{
	private $valor;

	//outros métodos da classe que sejam necessários

	public function setValor( $valor )
	{
		$this->valor = $valor;
	}

	public function getValor()
	{
		return $this->valor;
	}

	public function calculaJuros()
	{
		return $this->valor * 1.25; // soma 25% em cima do valor
	}
}
?>
```

Sobre escrevendo o método CALCULAJUROS.

```php
<?php
class ChequeEspecial extends ChequeComum
{
	public function calculaJuros()
	{
		return $this->valor * 1.10; // soma 10% em cima do valor
	}
}
?>
```
Sobrecarga de métodos – Overloading

O Polimorfismo ainda permite que numa mesma classe tenhamos métodos com o mesmo nome, desde que o número ou tipos de parâmetros passados sejam diferentes.
A sobrecarga de métodos é uma ferramenta poderosa, pois nos permite criar vários métodos com o mesmo nome, isso facilita o entendimento de problemas mais complexos, pois não é necessária a criação de nomes de funcionalidades sem sentido aparente.
Para exemplificar a sobrecarga de método utilizarei o exemplo de Pedro Padron disponível na integra no site http://imasters.com.br/artigo/5350/php/simulando-sobrecarga-de-metodos-no-php

```php
class Teste {
    // armazenará um array contendo as informações dos usuários.
    // em uma situação real, esses dados poderão vir de qualquer outra fonte.
    private $_users;

    function __construct() {
        // inicializa o array, onde a chave é o ID e o valor é o NOME DO USUÁRIO
        $this->_users = array(0 => "Max Stirner",
                              1 => "Emma Goldman",
                              2 => "Aldous Huxley",
                              3 => "George Orwell",
                              4 => "Noam Chomsky");

    }

    function getUser($param) {

        if (is_string($param)) {
            // se for string, busca por nome
            $user = $this->_getUserByName($param);
        } else if (is_int($param)) {
            // se for int, busca por id
            $user = $this->_getUserById($param);
        } else {
            // se nenhuma condição for satisfeita, retorna um array vazio
            $user = array();
        }
        return $user;
    }

    private function _getUserById($id) {
        if (isset($this->_users[$id])) {
            // se existir o índice (id), monta o array do usuário
            $user = array("id" => $id, "username" => $this->_users[$id]);
        } else {
            // se não existir, retornará um array vazio
            $user = array();
        }
        return $user;
    }

    private function _getUserByName($name) {
        // busca pelo nome no array de usuários
        $id = array_search($name, $this->_users);

        if ($id != null) {
            // se encontrou, monta o array do usuário
            $user = array("id" => $id, "username" => $this->_users[$id]);
        } else {
            // se não encontrou, retornará null
            $user = array();
        }
        return $user;
    }
}
```
