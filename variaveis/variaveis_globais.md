# Variáveis globais
Segundo Gilmore (2008), em contraste com variáveis locais, uma variável global pode ser acessada em qualquer parte do programa. Para modificar uma variável global, porém, deve ser explicitamente declarada como global na função em que está a ser modificado. Isto é conseguido, convenientemente o suficiente, colocando a palavra-chave global na frente da variável que deve ser reconhecida como global. Colocar esta palavra-chave na frente de uma variável já existente diz ao PHP para utilizar a variável de ter esse nome. Considere um exemplo:

```php
$somevar = 15;
function addit() {
    global $somevar;
    $somevar++;
    echo "Somevar is $somevar";
}
addit();
```
