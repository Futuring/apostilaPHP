# FOR

A instrução FOR oferece um mecanismo um pouco mais complexo do que o WHILE.
Segue sua sintaxe:

```php
for (expression1; expression2; expression3) {
    statements

}
```
Existem algumas regras para ter em mente quando usar o FOR do PHP:
* A primeira expressão, expression1, é avaliada por padrão na primeira iteração do
loop.
* A segunda expressão, expression2, é avaliada no início de cada iteração. Esta expressão determina se looping continuará.
* A terceira expressão, expression3, é avaliada no final de cada loop.
* Qualquer uma das expressões pode ser vazia, a sua finalidade substituída pela lógica embutido dentro do bloco para.
