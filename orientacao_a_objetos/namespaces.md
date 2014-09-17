# Namespaces

Segundo Gilmore (2008), você pode criar bibliotecas de classes, bem como utilizar as bibliotecas de classe de terceiros, criada por outros desenvolvedores, sendo assim, inevitavelmente encontrara uma situação onde duas bibliotecas utilizam nomes de classes idênticas, produzindo resultados inesperados no aplicativo.
Para ilustrar o desafio, suponha que você criou um site que ajuda você a organizar seu livro e permite aos visitantes comentar sobre todos os livros encontrados em sua biblioteca pessoal. Para gerenciar este dados, você cria uma biblioteca chamada Library.inc.php, e dentro dele uma classe chamada Clean. esta classe implementa uma variedade de filtros de dados gerais que você pode aplicar aos dados não só o livros-relacionados, mas também comentários dos usuários. E em outra biblioteca você tem outra classe Clean que realiza outros métodos, sendo assim haverá duas classes com o mesmo nome, gerando erro.
Para solucionar isto é necessário a utilização de namespace, para isto basta abrir cada biblioteca e na primeira linha dar um nome a ela único, assim: namespace `NOME_DA_BIBLIOTECA`.

Para maiores detalhes consultar o capítulo 6 e 7 do livro DOMINANDO PHP E MySQL, páginas 131 a 169
