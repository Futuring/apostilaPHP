# Variáveis estáticas

Segundo Gilmore (2008), o último tipo de escopo de variáveis para discutir é conhecido como estática. Em contraste com as variáveis declaradas como parâmetros da função, que são destruídas na saída da função, uma variável estática não perde seu valor quando sai da função e ainda sustentam que o valor se a função é chamada novamente. Você pode declarar uma variável como static simplesmente colocando a palavra-chave static na frente do nome da variável, assim:

```php
STATIC $somevar;
```

Considere o exemplo:

```php

function keep_track() {
    static $count  = 0;
    $count++;
    echo $count;
    echo "<br />";
}

keep_track();
keep_track();
keep_track();
```

Resultado do script acima, com a variável $count não sendo static:

1 <br />
1 <br />
1 <br />

Resultado do script acima, com a variável $count sendo static:

1 <br />
2 <br />
3 <br />
