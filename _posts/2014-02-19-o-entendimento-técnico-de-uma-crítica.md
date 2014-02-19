---
layout: post
title:  "O entendimento técnico de uma crítica"
date:   2014-02-19 20:26:00
categories: pt-BR jquery
---

Ainda hoje - ao momento em que escrevo - publiquei um [artigo][1] sobre ponderar o corte do jQuery em priorização a outras medidas que poderiam ser tomadas antes.
[1]: http://leobalter.github.io/pt-br/jquery/2014/02/19/o-hype-sobre-na%CC%83o-utilizar-jquery.html

Tive até o momento mais de 900 pageviews só nesse artigo e dezenas de comentários no [Twitter][twitter] e [Facebook][fb], alguns foram para reclamar que eu traduzi Vanilla JS como JS de baunílha. Vou evitar repetir essa tradução. :)
[twitter]: https://twitter.com/leobalter/status/436172584900521984
[fb]: https://www.facebook.com/leobalter/posts/10203381685847548

Quero deixar claro uma parte da minha opinião que não é diminuir ou ser agressivo à opinião contrária. Somos profissionais e não é ruim ser honesto. Houve comentários de algumas pessoas que leram o meu artigo e o do [Tableless](http://tableless.com.br/) que passaram dos limites técnicos e acabaram perdendo contexto.

Deixei inclusive um [tuite] comentando o assunto, lá dizia: "*Desenvolvedores, sejam educados, críticos e ponderados ao debater um assunto técnico, essa é a profissão de vocês e não um Hunger Games.*".
[tuite]: https://twitter.com/leobalter/status/436202956422397952

Dito isso, ressalto que **tenho muita adimiração pelo Tableless** e sou um leitor regular do site.

Bons efeitos
======

Além de desmistificar a interpretação errada de muita gente, que seria somente só remover o jQuery, foi ressaltado que a ideia era remover como uma opção, o que reiterei no meu artigo outras coisas que também poderiam ser priorizadas.

O [Diego Eis](https://twitter.com/diegoeis) aceitou alguns pontos do meu artigo e de imediato já tomou algumas medidas super bacanas em seu site.

Se lembra daquele gráfico de pizza que mostrei 4 fontes sendo carregadas e 618KB de imagens?

Agora o site carrega apenas 2 arquivos de fontes e está com menos da metade do tamanho das imagens carregadas.

[![Gráfico pizza](/images/tableless-pizza-2.png)](/images/tableless-pizza-2.png)

Em um total, o site (sem cache) passou a ter menos da metade de seu tamanho em KBs, foi algo em torno de 1120KB para 490KB, com fontes e imagens.

Isso foi incrível, tanto pela discussão respeitosa, quanto pela aceitação de uma crítica e implementação de uma melhoria que vai fazer bem a todos, desde o usuário ao tráfego de banda do site.