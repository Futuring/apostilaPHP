# Variáveis locais

Segundo Gilmore (2008), uma variável declarada em uma função é considerada local. Ou seja, ele pode ser referenciado apenas nessa função. Qualquer atribuição fora dessa função será considerada como uma variável totalmente diferente da uma contida na função. Segue exemplo abaixo:

```php
$x = 4;
function assignx () {
    $x = 0;
    printf("\$x inside function is %d <br />", $x);
}
assignx();
printf("\$x outside of function is %d <br />", $x);
```

Resultado a seguir:

$x dentro da função é 0
$x fora da função é de 4
