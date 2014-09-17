# Formulários HTML

Segundo Gilmore (2008), o que torna a web tão interessante e útil é a capacidade de disseminar informações, bem como recolher ela, o que é realizado principalmente através de um formulário baseado em HTML. Estes formulários são utilizados para encorajar o feedback site, facilitar conversas fórum, coletar endereços de correspondência e de faturamento on-line ordens, e muito mais. Mas a forma de codificação HTML é apenas uma parte do que é necessário para efetivamente aceitar entrada do usuário; um componente do lado do servidor deve estar pronto para o processo de entrada, este por sua vez será o PHP que estamos aprendendo.
O script a seguir solicita ao usuário seu nome e e-mail. Uma vez preenchido e enviado, o script (nomeado subscribe.php) exibe essas informações de volta para a janela do navegador.

```php
<?php
    // If the name field is filled in
    if (isset($_POST['name']))
    {
       $name = $_POST['name'];
       $email = $_POST['email'];
       printf("Hi %s! <br />", $name);
       printf("The address %s will soon be a spam-magnet! <br />", $email);
    }
?>
```

```html
<form action="subscribe.php" method="post">
    <p>
        Name:<br />
        <input type="text" id="name" name="name" size="20" maxlength="40" />
    </p>
    <p>
        Email Address:<br />
        <input type="text" id="email" name="email" size="20" maxlength="40" />
    </p>
    <input type="submit" id="submit" name = "submit" value="Go!" />
</form>
```

Para maiores detalhes consultar o capítulo 13 do livro DOMINANDO PHP E MySQL, páginas 281 a 286

###GET ou POST

O GET é um dos métodos do HTTP, é acionado por meio de um formulário HTML através da diretiva method=get incluída na tag `<form>`. Por meio desse método, os dados constantes no formulário são primeiramente transmitidos ao servidor, que por sua vez, armazena os dados temporariamente numa variável denominada `QUERY_STRING.

Quando um formulário HTML utiliza o método GET, o fluxo de dados é separado no endereço URL por um ponto de interrogação (?). Esta forma de endereçamento e separação pode ser observada no campo de endereços do navegador do usuário, logo após o formulário ter sido enviado. Você verá algo como:
http://www.meusite.com/meuscript.cgi?nome=Maria&amp;id=123

Para recuperar os dados utilizara-se o método `$_GET` como abaixo:

```php
$nome = $_GET[“nome”]; // a variável nome receberá o nome Maria
$codigo = $_GET[“id”]; // a variável código receberá o id 123
```

O POST, também um método do HTTP, é acionado por meio de um formulário HTML através da diretiva method=post incluída na tag <form>. Este método faz com que os dados do formulário sejam diretamente transmitidos ao endereço que constar da diretiva “action=”. Que informará o script php que processará os dados do form, este script irá extrair os dados através do método `$_POST`.
