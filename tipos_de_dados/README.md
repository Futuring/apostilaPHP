# Tipos de Dados

Os tipos de dados em PHP são boolean, string, integer, float e array.
Segundo Gilmore (2008), boolean – tipo verdadeiro, este tipo retornará o valor VERDADEIRO ou FALSO (true / false), pode-se ainda usar valores numéricos. Qualquer valor diferente de ZERO é considerado verdadeiro e o Zero assume o valor de falso.
```php
$testa = 1;	 // então retornara verdadeira
$testa =-1;	 // então retornara verdadeira
$testa = 0;	 // então retornara falsa
$testa = true;	 // então retornara verdadeira
$testa = false;	 // então retornara verdadeira
```
Segundo Gilmore (2008), integer – tipo numérico inteiro, ou seja, números que não contenham casas decimais. O PHP poderá trabalhar com números inteiros em base decimal, octal ou hexadecimal. Comumente trabalharemos na base decimal. O tamanho máximo de inteiro suportado irá variar com a versão já que até o PHP5 era de 231 positivo ou negativo e a versão PHP6 trouxe os valores inteiros de 64 bit que compreende os valores de 263 positivo ou negativo.

```php
$valor = 9;		//decimal
$valor = 157;	//decimal
$valor = 0755;	//octal
$valor = 0xC4E;	//hexadecimal
```

Segundo Gilmore (2008), float – Números que contem partes fracionadas, também conhecidos como números de ponto flutuante, podem ser chamados também de doublés ou real.

```php
$real = 1.23;
$real = 5.0;
$real = 8.7e4;
$real = 1.23E+11;
```
Segundo Gilmore (2008), string – são determinadas por aspas simples ou duplas, que determinam uma seqüência de caracteres.

```php
$palavra = ‘PHP é uma ótima linguagem’;
$palavra = ‘*9subway\n’;
$palavra = “123$%^789”;
```

Segundo Gilmore (2008), o PHP trata uma string como um array, assim pode-se acessar uma determinada parte da string através de uma notação offset no array, segue exemplo:

```php
$frase = ‘marron’;
$parte = $frase[2]; //A variável $parte receberá a letra “r”;
```

Segundo Gilmore (2008), array – pode ser um vetor ou matriz, este usualmente utilizado para agregar valores do mesmo tipo, os indexando num vetor ou matriz. Por exemplo, se você estiver interessado em criar uma lista de estado do Brasil indexado numericamente ficaria assim:

```php
$estada[0] = ‘Rio Grande do Sul’;
$estado[1] = ‘Santa Catarina’;
$estado[2] = ‘Paraná‘;
...
$estado[26] = ‘Pará’;
```

Ou indexada pela capital do estado:

```php
$estada[“Porto Alegre”] = ‘Rio Grande do Sul’;
$estado[“Florianópolis”] = ‘Santa Catarina’;
$estado[“Curitiba”] = `Paraná`;
...
$estado[“Belém”] = ‘Pará’;
````

Segundo Gilmore (2008), objeto – conceito central do paradigma de programação OO, este ao contrario dos demais tipos encontrados no PHP deve ser explicitamente declarado. Esta declaração se dará dentro da classe com todas as características que objeto virá a ter.

```php
Class cabelo{
    Private $_cor;
    Function setCor($coloracao){
	    $this->_cor = $coloracao;
    }
}
...
$liso = new cabelo;
````

Falaremos mais de Objetos na parte de PHP com OO.
Para maiores detalhes consultar o capítulo 3 do livro DOMINANDO PHP E MySQL, páginas 49 a 52.
