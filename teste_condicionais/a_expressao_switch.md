# A expressão SWITCH

Você pode pensar da instrução switch como uma variante da combinação if-else, muitas vezes usado quando você necessidade de comparar uma variável contra um grande número de valores:
```php
<?php
    switch($category) {
        case "news":
            echo "<p>What's happening around the world</p>";
            break;
        case "weather":
            echo "<p>Your weekly forecast</p>";
            break;
        case "sports":
            echo "<p>Latest sports highlights</p>";
            break;
        default:
            echo "<p>Welcome to my web site</p>";
    }
?>
```
Para maiores detalhes consultar o capítulo 3 do livro DOMINANDO PHP E MySQL, páginas 76 a 79
