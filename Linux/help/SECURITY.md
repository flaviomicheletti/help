model(1) -- Tecnicas e recomendações de Security
===============================================


SYNOPSIS
--------

`model` [`-bar`] [`-c` *config-file* ] *file* ...

DESCRIÇÃO
---------


Usar melhorias de segurança no HTTP headers(ver página da `OWASP` sobre *Content-Security-Policy*:
Content-Security-Policy
X-Content-Security-Policy
X-WebKit-CSP


Ficar atendo ao OWASP top 10



ATAQUES
-------

Clickjacking
Cross Site Request Forgery (CSRF)
Denial of Service(DoS)
Server Site Request Forgery (SSRF)
CORS ( Cross Origin Resource Sharing)



FALHAS EM CONFIGURAÇOES
-----------------------
Esquecer o debug ligado, pode retornar informações importantes para o atacante.
Falta de Monitoramento
Principle of least privilege
Rate limiting & Captchas
Senhas e segredos de projeto em arquivos


DOCKER
------
Minimo de privilegio possivel.
Usar imagens oficiais.
Automatizar build evita falhas e erros humanos.
Dockerfile -> não rodar como root.
Least Privilege
Read only se for o caso!


PENTESTING
----------

OWASP 10 - Tentar automatizar pentest para falhas de segurança.
Conhecer as ferramentas que podem Automatizar - OWASP ZAP - Kali - Blach Arch


CONTINUOUS SECURITY HYGIENE
---------------------------
Fazer levantamentos rotineiros para procurar problemas de segurança.
Manter os padrões de segurança.
Segunrança x Usabilidade.
fazer Threat Modeling - Procurar sobre, tem um documento bom da Microsoft.













`model` é um documento escrito para facilitar a crição de documentos a partir de um template.
Com a MARCAÇÃO *markup* é possível gerar Man Pages usando o comando **ronn**. Veja mais em ronn(1).
Necessita Ruby >= 2.0 com Mustache para funcionar..

OPÇÕES
------

* `-b`:
  Do not write "busy" to stdout while processing.

* `-c` *config-file*:
  Use the alternate system wide *config-file* instead of */etc/foo.conf*. This
  overrides any `FOOCONF` environment variable.

* `-a`:
  In addition to the baz segments, also parse the blurfl headers.

* `-r`:
  Recursive mode. Operates as fast as lightning at the expense of a megabyte
  of virtual memory.

EXEMPLOS
--------

Coloque os exemplos aqui:

   `$> date '%Y/%m/%d'`


ARQUIVOS
--------


*/etc/foo.conf*
  The system wide configuration file. See foo(5) for further details.

*~/.foorc*
  Per user configuration file. See foo(5) for further details.

ENVIRONMENT
-----------

`FOOCONF`
  If non-null the full pathname for an alternate system wide */etc/foo.conf*.
  Overridden by the `-c` option.

DIAGNOSTICS
-----------

The following diagnostics may be issued on stderr:

**Bad magic number.**
  The input file does not look like an archive file.

**Old style baz segments.**
  `foo` can only handle new style baz segments. COBOL object libraries are not
  supported in this version.

COMENTARIOS
-----------

Coloque seus comentários aqui...
<- Tag para comentários na Man Page, juro, não sai nada.>

BUGS
----

The command name should have been chosen more carefully to reflect its
purpose.

AUTOR
-----

Rafael Quirino - <quirinobytes (a) gmail com>

VEJA SOBRE
----------

ronn(5), markdown(1), txt2tags(1) [Linux Man Page Howto](
http://www.schweikhardt.net/man_page_howto.html)
