# Exceções

Segundo Gilmore (2008), exceções são usadas para mudar o curso normal de um script se um erro específico acontece. A execução do código será desviada para um tratador de exceções específico. Dependendo da situação, o tratador poderá então deixar que a execução continue a partir do estado em que ela se encontrava, terminar a execução ou continuar a execução de um local diferente no código.
Segue o quadro com as diretrizes de error_reporting que determinaram o nível de sensibilidade dos erros.
```
Nível de erro			Descrição
E_ALL 				Todos os erros e avisos
E_COMPILE_ERROR 		Fatal em tempo de compilação
E_COMPILE_WARNING 		Avisos em tempo de compilação
E_CORE_ERROR 		Erro fatal que acontece durante a execução inicial do PHP
E_CORE_WARNING 		Advertências que ocorrem durante a execução inicial do PHP
E_DEPRECATED 	Advertências sobre uso de recursos programados para a remoção de um futuro PHP release (introduzido no PHP 5.3)
E_ERROR 			Fatal erros em tempo de execução
E_NOTICE 			Notas em tempo de execução
E_PARSE 			Erros de parse em tempo de compilação
E_RECOVERABLE_ERROR 	Erros fatal (introduzido no PHP 5.2)
E_STRICT 			Sugestões versão PHP portabilidade (introduzido no PHP 5.0)
E_USER_DEPRECATED 	Utilização de recursos agendados para remoção no PHP futuro lançamento (introduzido no PHP 5.3)
E_USER_ERROR 		Usuário erros gerados
E_USER_NOTICE 		Gerado pelo usuário avisos
E_USER_WARNING 		Gerado pelo usuário advertências
E_WARNING 			Avisos de tempo de execução
```
Para tratar as exceções utilizaremos o `try / catch`, segue sua sintaxe básica:
```php
try {
    perform some task
    if something goes wrong
        throw exception("Something bad happened")
// Catch the thrown exception
} catch(exception) {
    output the exception message
}
```

Para maiores detalhes consultar o capítulo 8 do livro DOMINANDO PHP E MySQL, páginas 171 a 184
