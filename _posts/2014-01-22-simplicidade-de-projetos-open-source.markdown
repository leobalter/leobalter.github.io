---
layout: post
title:  "Simplicidade de projetos Open Source"
date:   2014-01-22 10:26:00
categories: pt-BR open
---

Estava falando com um amigo sobre um sentimento de frustração que desenvolvedores acabam adquirindo por só trabalhar com projetos privados, mesmo que utilizem o Github, resolvi compartilhar aqui para não ficar esquecido, uma vez que tenho insistido nos meus argumentos ao conversar com várias pessoas.

Não é todo mundo que tem a chance de ser pago pra trabalhar com projetos abertos, normalmente a maioria dos projetos são privados e há muita gente fazendo coisa incrível.

O que pode ser feito é aproveitar o argumento de que nesses projetos privados já usamos ferramentas abertas e tentar desacoplar e externar pequenas partes de um projeto fechado e torná-las abertas.

Por exemplo: eu já fiz um plugin simples de mostrar estrelas preenchidas de acordo com uma porcentagem. Extraí só aquela parte como um plugin jQuery e consegui facilmente a autorização pra publicar. 

Assim como fiz boa parte do DexterJS dentro da empresa em que trabalho, pois ele é muito utilizado lá. Se ele não tivesse publicado, eu não teria metade das melhorias que já recebeu com a colaboração espontanea de pessoas que não trabalham na mesma empresa. Eu acabei melhorando a qualidade de um produto da empresa, sem abrir nenhuma regra de negócio ou confidencialidade. O custo dessa melhoria foi *0* para empresa. 

---

Se ainda não for possível desacoplar e externar pequenos projetos, a outra dica é tentar mirar na colaboração de projetos abertos que sejam o simples possível. Nem toda correção é um patch gigante ou complexo, às vezes é só um typo ou algo pequeno que resolvemos em 5 minutos.

Veja, por exemplo, esse [pull request](https://github.com/jquery/jquery/pull/1493/files) que eu fiz. Se for aceito eu vou poder dizer que tenho commit no repositório do [jQuery](http://jquery.com). Sério, olha o tamanho disso.

Só é preciso focar em um detalhe: toda colaboração é bem vinda, até as mais simples, até as que não forem aceitas por questão de não estarem em conformidade com um projeto. Esteja pronto para pedirem pra corrigir as suas alterações, seus commits, ajustar o código para ficar adequado a convenções, ou não aceitarem por algum motivo ou outro.

Se você agir educadamente e cordialmente, não há desculpa para alguém achar errada a sua sugestão em um projeto open source. Acredite, as pessoas são mais receptivas do que parecem e as correções de bugs em projetos open source as vezes são mais ridículas do que parecem, só faltou você aparecer por lá.
