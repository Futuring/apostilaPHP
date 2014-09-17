# Objetos

Uma vez que a classe é definida podemos então criar infinitos objetos baseados na estrutura de uma mesma classe. Dentro da nossa aplicação podemos ter 100 objetos Produto que possuem a mesma estrutura, mas com informações diferentes.
A criação de um objeto a partir de uma classe é chamada de instanciação, então todo objeto é uma instancia de alguma classe. Para criar um objeto utilizamos o operador new.
```php
<?php
$produto = new Produto();
$produto2 = new Produto();
$produto3 = new Produto();
?>
```
Isso informa ao interpretador do PHP que um novo objeto está sendo criado. Então internamente o PHP reserva um espaço na memória onde aquele objeto vai ser armazenado. Por causa disso quando trabalhamos com objetos (a partir do PHP 5) todos os valores são passados por referencia, ou seja:
```php
<?php
$produto = new Produto();
$produto->preco = 1;

echo $produto->preco; // imprime 1

$produto_copia = $produto;
$produto_copia->preco = 3;

echo $produto->preco; // imprime 3
?>
```
Explicando todo o processo por trás: quando instanciamos a classe Produto dentro da variável $produto, é criado um espaço na memória onde o objeto fica armazenado e a variável $produto guarda a referência para aquele espaço, ou seja, a variável aponta diretamente para a memória. Quando dizemos que `$produto_copia` é igual a `$produto`, `$produto_copia` irá copiar a referência para a memória e não o objeto. Assim qualquer alteração feita em `$produto_copia` afetará `$produto`, pois ambos apontam para o mesmo objeto na memória.
É possível que seu navegador não suporte a exibição desta imagem.
