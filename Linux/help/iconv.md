iconv(1) -- Conversor de arquivos
===============================================

NOME
----

`iconv` - programa de conversão de codificação de texto.

SYNOPSIS
--------

`iconv` [`-bar`] [`-c` *config-file* ] *arquivo* ...

DESCRIÇÃO
---------

`iconv` é um programa para converter codificação de arquivos, exemplo UTF-8 ISO-8859-1 Western bla bla bla...

OPÇÕES
------

* `-f` *file-encode*:
  (from) Define tipo do arquivo de origem. -> utf-8 , iso-8859-1 
* `-t` *file-encode*:
  (to) Define o tipo que será converido -> utf-8 , iso-8859-1

* `-c` *file-name*

EXEMPLOS
--------

* converte o arquivo.txt para UTF-8

	`$> iconv -f utf-8 -t ucs-4 < arquivo.txt >/dev/null`

* limpa os caracteres estranhos no arquivo
	
	`$> iconv -f utf-8 -t utf-8 -c file.txt > novoarquivo-limpo.txt`

ARQUIVOS
--------

*arquivo.txt*
  O arquivo utilizado como entrnada.

AUTOR
-----

Rafael Quirino - <quirinobytes (a) gmail com>

VEJA SOBRE
----------

ronn(5), markdown(1), txt2tags(1) [Linux Man Page Howto](
http://www.schweikhardt.net/man_page_howto.html)
