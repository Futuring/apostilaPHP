# Sessões

Segundo Gilmore (2008), o Hypertext Transfer Protocol (HTTP) define as regras utilizadas para transferir texto, gráficos, vídeo e todos os outros dados através da World Wide Web. É um protocolo sem estado, o que significa que cada pedido é processado sem qualquer conhecimento de qualquer pedido anterior ou futuro, isto pode ser um problema para os desenvolvedores que desejam criar complexos aplicativos baseados na Web que deve se ajustar ao usuário específico comportamento e preferências.

Para remediar este problema, a prática de bits armazenamento de informações na máquina do cliente, rapidamente ganhou aceitação, oferecendo algum alívio para esse enigma. No entanto, limitações no tamanho do cookie, o número de cookies permitidos, e vários outros inconvenientes em torno de sua implementação, motivaram os desenvolvedores a elaborarem outra solução:

manipulação de sessões. A manipulação de sessões é essencialmente uma solução inteligente para este problema. Isto é realizado mediante a atribuição a cada visitante do site um atributo de identificação único, conhecido como o ID da sessão (SID), e depois correlacionar SID que com qualquer número de outras partes de dados, seja número de mensais visitas, cor favorita do fundo, ou nome do meio-you name it. Em termos de banco de dados relacional, você pode pensar no SID como a chave primária que une todos os atributos de outros usuários juntos.

Quase 30 diretrizes de configuração são responsáveis por ajustar o comportamento de gerenciamento de sessão em PHP, irei citar algumas delas abaixo, para maiores detalhes consultar capitulo 18 nas páginas 361 a 379:

Gerenciando a mídia de armazenamento de sessão
A diretriz session.save_handler determina como as informações da sessão será armazenado. Seu protótipo se parece assim:
```php
session.save_handler = arquivos | mm | sqlite | usuário
```
Os dados da sessão podem ser armazenados em quatro formas:

dentro de arquivos simples (arquivos), dentro de memória volátil (mm), usando
banco de dados SQLite (sqlite), ou através de funções definidas pelo usuário (user).

Configurando o Caminho de arquivos da sessão
Se session.save_handler está definido para a opção de armazenamento de arquivos, então a directiva deve ser `session.save_path` conjunto, a fim de identificar o diretório de armazenamento. Seu protótipo parecido com este:
```php
session.save_path = string
```
Por padrão session.save_handler é configurada em /tmp.

Ativando automaticamente Sessions
Por padrão, a sessão de uma página só será habilitada somente chamando a função `session_start()`. No entanto, se você planeja usar sessões em todo o site, você pode abrir mão de usar esta função definindo `session.auto_start a 1`.
Alterando o parâmetro abaixo:
`session.auto_start = 0 | 1`

Definindo o Nome da sessão
Por padrão, o PHP irá usar um nome de sessão de `PHPSESSID`. No entanto, você está livre para mudar esse valor para o nome que você deseja usar a diretiva `session.name`.
Alterando o parâmetro abaixo:
`session.name = string`

Para maiores detalhes consultar o capítulo 18 do livro DOMINANDO PHP E MySQL, páginas 361 a 379
