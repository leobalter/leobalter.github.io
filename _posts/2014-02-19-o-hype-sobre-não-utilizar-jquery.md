---
layout: post
title:  "O hype sobre não utilizar jQuery"
date:   2014-02-19 12:03:00
categories: pt-BR jquery
---

Eu vejo um hype pelos desenvolvedores em criticar o jQuery, acho que o ideal é sermos críticos e equilibrar os pesos na balança. Obviamente vão perceber que meus argumentos não favorecem que simplesmente ignore o uso do jQuery e troque por qualquer outra coisa, inclusive por JS puro.

Esse artigo é essencialmente motivado a partir de um outro [artigo recém lançado][1] - no momento em que escrevo - pelo Tableless. No artigo demonstra que removeu quase 100KB que seriam só para rodar poucas funçoes e passaram a usar JS puro. 
[1]: http://tableless.com.br/considere-nao-usar-jquery

O primeiro ponto que precisamos considerar é remover uma biblioteca JS e não um framework. Não há inversão de controle, usamos a lib somente quando precisamos dela e torna até fácil desplugar ela e usar outra coisa, como JS de baunilha.

Se o motivo for somente peso e tempo de carregamento do site, eu recomendo colocar uma série de prioridades no site. Vamos listar alguns problemas que encontrei no mesmo site onde o jQuery foi removido.

1. Considere não abusar de fontes. 
========

É muito bacana poder adaptar o layout do seu site para utilizar fontes diferentes do que encontramos por padrão nos navegadores. Mesmo assim, carregar fonte pode sair muito mais custoso que carregar os 100KB do jQuery.

Veja o exemplo:

[![Fontes](/images/tableless-fontes.png)](/images/tableless-fontes.png)

Aqui mostra que o site carrega **mais de 320KB em fontes**, com 4 versões diferentes - regular, bold, light e medium - que normalmente se utilizam apenas 2 (regular e bold). Se o site abrisse mão da light e da medium, seria uma economia de 160KB.

2. Considere não carregar imagens.
========

Em um outro exemplo o mesmo site carrega mais de 600KB de imagens, é o grande peso no site. Vejamos nesse gráfico pizza como o site é equilibrado no peso:

[![Gráfico pizza](/images/tableless-pizza.png)](/images/tableless-pizza.png)

Ou seja, de 694KB carregados do site - sem as fontes - temos 618KB só de imagens.

Mas fica a dúvida se elas estão sendo utilizadas. Eu fiz esse teste de carregamento na home do site, então fui verificar quais seriam essas imagens. Terminei na primeira imagem que observei, a mais pesada delas:

[![Imagens](/images/tableless-imagens.png)](/images/tableless-imagens.png)

A imagem mais pesada que era carregada, inclusive com mais de 100KB, simplesmente não era utilizada na home, onde fiz a medição e checagem.

3. Considere usar GZIP.
========

Muitos sites simplesmente não utilizam compactação em seus arquivos estáticos. Isso é algo além de minimizar um arquivo JS, mas simplesmente complementar essa minimização com um GZIP, por exemplo. Com isso o jQuery inteiro custaria 32KB para ser carregado.

Lembre-se que JS - por ser em sua essência um arquivo de texto - tem um ganho incrível de compactação pelo GZIP em relação às imagens.

4. Considere fazer uma montagem personalizada do jQuery.
========

Uma das vantagens mais interessantes e não muito recente do jQuery é justamente permitir montar uma versão personalizada, utilizando apenas os itens necessários.

Não custa nada dar uma lida no [readme que há no Github][2] para ver como obtemos uma versão só com o que precisamos da biblioteca.
[2]: https://github.com/jquery/jquery#how-to-build-your-own-jquery

5. Considere rodar testes unitários.
=======

Testes unitários são importantes e deveriam fazer parte da rotina de todos os desenvolvedores JS que pretendem manter seus projetos no dia a dia. Eles diminuem erros adversos e permitem que os mesmos erros não aconteçam mais de uma vez. 

O jQuery está todo testado. Logo, mesmo que você pegue uma parte menor da biblioteca, você vai pegar um código que já foi testado e pode contar que futuros erros podem ser fora da biblioteca.

Quantas vezes já implementaram algo com jQuery e o bug estava lá na biblioteca e não no seu código? 

Se realmente achar um bug no jQuery, aproveite para reportar no [Issue Tracker][3] oficial. Vai haver todo um time para consertar o bug e criar testes para que o mesmo não aconteça novamente. É como se fosse um outsourcing gratuito para parte do seu código.
[3]: http://bugs.jquery.com/

6. Considere a compatibilidade cross-browser
========

Há pouco tempo apareceu o artigo "You might not need jQuery", declarando o auge para o hype que mencionei. O interessante que ele mostrava como substituir alguns pontos do jQuery para JS puro, com alguns ms de performance a mais.

O problema é que muitas vezes nos deparamos com maçantes problemas de compatibilidade.

Diferente de desenvolver algo que rode em um servidor, seja em Node, Perl, Python, Ruby, PHP, etc, é que trabalhamos com vários ambientes diferentes, pois cada navegador é um ambiente. Cada um tem o seu motor, sua estrutura e seus bugs.

De todo o código que você pode abstrair no jQuery, considere uma redução de tempo incrível para testar apenas o mínimo que já foi feito após o carregamento da biblioteca para garantir que tudo funciona em qualquer browser que você queira dar suporte. Lembre-se que o jQuery 1.x ainda dá suporte ao quase extinto IE6, enquanto o jQuery 2.x da suporte a IE9+ e outros navegadores considerados modernos. É um tempo que não precisamos perder.

Ainda considerando o jQuery 2.x, vale lembrar que só nessa versão temos mais de 100 itens marcados para soluções de compatibilidade crossbrowser. O [Rick Waldron](https://twitter.com/rwaldron) compilou [uma lista com esses itens][4]. Se quiser criar seu próprio JS puro, vale a pena conferir para não cair em algumas das pegadinhas já observadas e corrigidas no jQuery.
[4]: https://gist.github.com/rwaldron/8720084#file-reasons-md


7. Considere seu tempo
=======

Há uma frase comum entre desenvolvedores que conheço: "*Optimized for Development*". Isso deve ser um mantra. Antes de super otimizar a performance do seu site, lembre-se que ela sempre pode ser feita gradualmente e sem ocupar o seu tempo com coisa já resolvida.

Se você levar a sério que não é bom utilizar uma biblioteca JS - e isso vale para jQuery, Dojo, YUI, etc - você pode perder um tempo precioso onde poderia resolver problemas mais importantes para o seu projeto.

Precisa de uma sugestão? Invista esse tempo livre criando testes unitários para as suas funções. Vale mais deixar seu projeto mais estável, sem reinventar a roda.