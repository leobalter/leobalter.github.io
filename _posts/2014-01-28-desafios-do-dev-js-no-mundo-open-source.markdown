---
layout: post
title:  "Os desafios do desenvolvedor JS no mundo Open Source"
date:   2014-01-28 02:00:00
categories: pt-BR entrevistas
---

Há mais de um mês foi publicado na versão digital da [Revista Wide][1] uma entrevista que fiz - e saiu enorme - sobre os desafios do mundo open source.
[1]: http://www.revistawide.com.br/tecnologia/js-no-mundo-open-source

Acho legal compartilhar a ideia por aqui, já tendo passado um tempo que o artigo já publicado na revista. 

--------
**WIDE: Em sua opinião, quais são os principais desafios do desenvolvedor JavaScript (JS) quando falamos de open source?**

**LEO BALTER** O principal desafio para um desenvolvedor começar a contribuir para projetos abertos é justamente começar. Existe um medo de começar e - em muitas vezes - não fica muito claro sobre como a pessoa pode ajudar ou como ela deveria ajudar. Assim, tudo parece muito mais complexo do que na verdade é. É mais fácil e simples contribuir com projetos abertos do que parece.

Há outra barreira para essa colaboração inicial, que é a ideia de que só atualizações muito complexas têm valor. Na verdade, uma correção de um erro de tipografia - às vezes um acento esquecido - já é importante para os projetos abertos.

Um dica para quem quer colaborar e não sabe o que fazer, é pesquisar os projetos do Github pelas listas de issues - algumas são coisas simples que talvez o desenvolvedor já tenha passado por uma experiência similar e seja fácil resolver. As listas de Pull Requests nesses projetos também são - muitas vezes - o outro lado do arco-íris. Percebo em alguns casos que o desenvolvedor esqueceu de testar ou não soube como testar; pego as mudanças de código dele, aplico os testes, refatoro o código que ele escreveu para se adaptar aos testes e crio um novo pull request ao projeto. Assim, nós dois acabamos colaborando juntos. Isso mostra que projetos abertos têm em sua veia justamente o espírito colaborativo, mesmo que seja apenas para ajudar a quem quer colaborar, e isso é muito rico em experiência.

Existem também os desafios para quem mantém um projeto e quer levá-lo para o mundo open source. Assim como as startups, nossos projetos open source correm risco de extinção por desuso, nosso e do público. Eu mesmo mantenho um projeto - o [DexterJS](https://github.com/leobalter/DexterJS) - que não consegui fazer emplacar como um sucesso; atualmente o mantenho pois ele é muito utilizado na empresa onde trabalho, a Estante Virtual.

Logo, a primeira ideia que precisa ser passada aos desenvolvedores é que nem todo projeto vai ser um sucesso em termos de quantidade de pessoas que vão utilizar, mas às vezes pode ser super útil a poucas pessoas. Isso pode e deve ser considerado também como um fator de sucesso.

O segundo desafio para manter um projeto é que nem sempre as pessoas vão surgir espontaneamente para criar correções, sugerir coisas novas etc. Por muito tempo, o desenvolvedor precisa se dedicar continuamente ao seu projeto para mostrar seu esforço, e claro, fazer divulgação pela internet. Tem que fazer barulho para o projeto aparecer e encontrar as pessoas que vão se interessar pela ferramenta que você criou. Hoje o desenvolvedor JS pode ir além de Github, Twitter e Facebook para essa divulgação. Há, por exemplo, listas que divulgam projetos gratuitamente e são muito utilizadas nas comunidades; seguem algumas dicas: [BrazilJS Weekly][BrazilJS Weekly], [JavaScript Weekly][JSW], [Open Web Platform Digest][OWPD] - minha favorita etc. O terceiro desafio para manter um projeto aberto é também o mais importante - a responsabilidade.

[BrazilJS Weekly]: http://us5.campaign-archive.com/?u=77b6594f10bba05dcc722c80e&id=017e091dc7
[JSW]: http://javascriptweekly.com/
[OWPD]: http://webplatformdaily.org/


**"É mais fácil e simples contribuir com projetos abertos do que parece".**


--------
**WIDE: E quais são os maiores perigos/cuidados que ele deve saber em relação ao código aberto?**

**LEO BALTER** Eu aprendi muito sobre cuidados e responsabilidade durante um almoço que tive com o Richard D. Worth, desenvolvedor core do jQuery. Ele me contou como é importante perceber que quem vai pegar o código pronto tem uma estima de que aquilo funciona conforme declarado, seja em documentação ou em uma apresentação. As pessoas muitas vezes não vão buscar a ferramenta para um simples experimento, mas sim para uma funcionalidade final de um projeto importante e que envolve a vida profissional delas. É só imaginar quantas pessoas já baixaram o próprio jQuery ou um framework e não se preocuparam com o fator "será que vai quebrar?".

Parte dessa responsabilidade é fazer garantir que a sua ferramenta funciona, evitar quebras e ser honesto na documentação. A desculpa que menos cola é a de dizer que "na minha máquina funciona". Uma das melhores soluções, nesse caso, é criar testes automatizados. Quem me conhece sabe o quanto sou chato com isso, mas a minha ideia é justamente não passar frustração. O lado da honestidade é tentar ser claro ao dizer o que está funcionando, o que está testado e onde foi testado. Muitos desenvolvedores têm a tendência de testar apenas em um ambiente. No caso do desenvolvedor JS, esse ambiente é o navegador, e muitos têm a preguiça de só testar naquele que prefere. Isso é assim desde sempre. Há dez anos, era assim para o mais utilizado na época, o Internet Explorer 6, e a comunidade lutou muito pela interoperabilidade e que não existisse mais o texto "funciona melhor no navegador xyz". Hoje, o problema se repete; a diferença é que cada um escolhe o seu favorito e se limita a testar tudo ali. A responsabilidade não é do navegador, por mais que sejam interoperáveis, eles são diferentes e cada um tem seus bugs em particular, logo, a responsabilidade é do desenvolvedor. Dizer que odeia o navegador x ou y, é um conceito caído, perdeu a validade.

Teste suas ferramentas open source no maior número de ambientes, enquanto eles forem razoáveis. Por exemplo, em desktop temos o Chrome, o Firefox e o Internet Explorer como os mais utilizados. Vá além e teste em outras versões alternativas de cada um, como em versões a serem lançadas, como o Chrome Canary, o Firefox Nightly e o Internet Explorer 11. Eles vão te ajudar a identificar se há alguma funcionalidade nova que pode mudar o comportamento da sua ferramenta. Explore também versões mais antigas de alguns navegadores. O Internet Explorer 8 ainda é muito utilizado pois muitos usuários que ainda utilizam o Windows XP, limitado a essa versão. Não tenha medo, se fizer seu aplicativo com testes em todos os navegadores desde o início, eles não vão dar tanto trabalho. Lembre-se que ferramentas open source podem ser utilizadas em todo tipo de projeto, inclusive os de e-commerce, onde essa estabilidade faz toda a diferença.

Não se esqueça também dos navegadores mobile. O usuário não se importa que está usando um celular, ele quer a experiência comum. Nem sabemos onde vai parar a nossa ferramenta open source, às vezes em um projeto mobile, aí é mais importante ainda também testarmos performance, área muito delicada nessa categoria. Não se limite ao iOS. Usuários mobile não são apenas os de iPhone ou iPad - temos muita gente usando o Android, seja pelo Chrome, Firefox ou Opera Mini (acredite, é um dos mais utilizados no mundo) e o Firefox OS está chegando com tudo - nos primeiros países em que foi lançado ele já tem 12% da fatia de dispositivos móveis.

Para esses navegadores você consegue normalmente encontrar simuladores que vão ajudar consideravelmente na hora de rodar esses testes.

Outro perigo importante é, de certa forma, um mantra: não alimente os trolls. Sempre há pessoas com níveis diferentes de criticismo. Algumas vão te julgar como pessoa por causa de um projeto sem saber que você dedicou boas horas, normalmente fora do seu horário de trabalho remunerado, para fazer uma funcionalidade super bacana. Elas poderiam apontar, algumas pessoas vão se limitar a isso, já outras vão apenas te fazer sentir pequeno, vão tentar te botar para baixo. Infelizmente essas pessoas fazem mais barulho e chamam mais atenção que as outras que vão elogiar ou criarem críticas construtivas. Tente inverter o jogo e ignore. Não desista do seu projeto open source por causa dos trolls, se eles não chamarem atenção, eles acabam desistindo e se afastando.

Outro cuidado é o fator tempo. Cada um tem o seu. Não fique na paranóia de que você só será útil se colaborar o tempo inteiro com projetos abertos. Às vezes falta tempo, talvez meses, para conseguir fazer algum tipo de colaboração, e ainda será necessário priorizar qual projeto demandará mais tempo. Existe um conceito errado imposto por algumas pessoas de que se você não pode colaborar com um projeto x naquela época, você estará sentado no sofá sem fazer nada. O mundo gira além do código, e normalmente precisamos pagar contas, declarar imposto de renda, ir à praia ou até trabalhar em um projeto que não é open source mas é remunerado e vai te dar condições de conforto suficientes para ter o tempo livre que lhe falta.

Lembre-se também de não ser um troll, não humilhe ninguém. Se outra pessoa errou, incentive ela a tentar outra vez da forma certa. Se não for possível ajudar, não julgue-a pelos erros, considere que mesmo errando, essa pessoa dedicou tempo e esforço para chegar a algo que falhou. Isso por si só já é frustrante, mas lembre-se que de grandes frustrações surgem grandes soluções e outras ferramentas.

Há pessoas com muito destaque nas comunidades e que participam de vários projetos. Normalmente elas têm o que muitos consideram um sonho, que é o fato de serem pagas para trabalharem com projetos open source. De fato é um sonho válido, mas é utópico ver todos os projetos assim. Essas pessoas servem de exemplo e temos que aprender com elas, mas não ache que, por causa disso, o seu trabalho é menor. Acredite, o maior esforço é ainda o de quem consegue se dedicar mais de 40 horas semanais com um trabalho de projeto fechado e ainda dedicar mais umas 10 a 20 horas nas mesmas semanas com projetos open source. Louvável quando elas ainda conseguem equilibrar isso tudo mantendo um bom ambiente familiar. A minha conclusão é que você pode colaborar em projetos abertos, mas no seu tempo.

Das ferramentas utilizadas em projetos open source, faço um destaque para três categorias muito importantes nessa área: ferramentas de testes, cobertura de testes e integração contínua



--------
**WIDE: Levando em consideração o leque de ferramentas livres existentes, quais são as mais utilizadas pelos desenvolvedores?**

**LEO BALTER** A mais importante das ferramentas a se aprender é a de controle de versão. Brincar no mundo open source com JS empurra você para conhecer o Git, apesar de existirem outras boas como o Mercurial HG. Conhecer Git hoje é fundamental por causa do Github e da quantidade de projetos relacionados ao JS que estão lá. O Git ajuda a marcar as mudanças de forma temporal nos pontos exatos do código de cada projeto, além de indicar quem fez essa mudança. O Github é uma plataforma aberta na web onde você pode publicar e colaborar livremente com projetos open source. E ele tem ferramentas de interface gráfica para utilizar o Git, mas não podemos esquecer da linha de comando.

Os desenvolvedores JS estão cada vez mais migrando para o CLI, em português e não abreviado como interface de linha de comando. No início, parece feio, complexo e menos intuitivo. No início tudo isso é verdade, mas quando se aprende tal fato vai se desmistificando.

Através da linha de comando temos a oportunidade de experimentar diversas ferramentas úteis. Entre elas, o Grunt, que é o automatizador mais popular nos projetos web no último ano. Ele é um verdadeiro canivete suíço para os nossos projetos. Ele automatiza de forma muito simples processos comuns como concatenação e minimização de arquivos JS e CSS, lint de JS com JSHint, execução de testes unitários, observa mudanças em arquivos do projeto para rodar algumas dessas tarefas etc. Podemos instala-lo com o NodeJS, que é muito útil para executar rotinas JS fora do browser e assim trivializar processos rotineiros que antes tomavam tempo ou precisavam de uma tecnologia diferente e complexa para cada uma delas.

Das ferramentas utilizadas em projetos open source, faço um destaque para três categorias muito importantes nessa área: ferramentas de testes, cobertura de testes e integração contínua.

Entre as ferramentas de testes temos como exemplo o [QUnit](http://qunitjs.com) - minha favorita; [Jasmine](http://pivotal.github.io/jasmine) - talvez o mais popular, e o [Mocha](http://visionmedia.github.io/mocha/) - o mais democrático. Se você está utilizando aplicações que rodam em NodeJS, eu recomendo a nova versão do QUnit ou o [Nodeunit](https://github.com/caolan/nodeunit), meu favorito nesse tipo de ambiente.

As ferramentas de cobertura são as que vão medir quanto do seu código está testado; às vezes experimentamos uma função que tem, por exemplo, um bloco de if e else dentro, e geralmente só testamos um retorno da função passando pelo if, sem passar por um else. Esse tipo de ferramenta aponta que essa parte do código ainda não foi testado, e também mostra um percentual de quanto já foi testado, por linhas, instruções, blocos e funções. Dicas básicas: não se preocupe em cobrir com testes 100% do código, 80% já é um excelente número; e nem sempre 100% de cobertura de testes garante que a sua ferramenta está 100% testada, muito menos que ela faz exatamente o que deveria fazer. Lembre-se disso toda vez que for tomar um café para refletir, não se exija tanto.

Atualmente utilizo para cobertura de código o [Istanbul](http://gotwarlost.github.io/istanbul) integrado no Grunt, e eu estou gostando muito.

Para completar, as ferramentas de integração contínua são perfeitas para projetos populares e com muitas pessoas colaborando. O Travis CI é uma das mais populares, assim como o Jenkins CI. Eu adoro a primeira delas, que tem integração muito simples com projetos que estão no Github. A integração contínua serve para identificar que cada nova versão do código está passando nos testes; se não ela sugere uma "bandeira vermelha" para a versão e você tem que consertar aquilo para dar prosseguimento. É claro que essa é uma explicação rudimentar da ferramenta, mas normalmente ela é muito utilizada para evitar deploys que quebrem todo o sistema em produção. Se algum erro passou direto aos olhos humanos, não vai passar pela integração contínua.

O DexterJS, que já citei, pode servir como um exemplo de projeto aberto que está no Github, utilizando QUnit, Istanbul e Travis-CI. Além deles ainda comecei a experimentar o Karma, que é uma ferramenta que executa testes em diversos navegadores que estejam à disposição na máquina do desenvolvedor. Eu integro todas essas ferramentas com o Grunt, que me proporciona tempo para me concentrar em outras partes do projeto ou em outros trabalhos.

Já que falei do DexterJS, vou citar ele como um bônus. Ele é basicamente uma ferramenta para auxílio em testes com mocks. Mocks são - de forma rudimentar - formas de alterar provisoriamente o estado de algumas funções, observando quando elas são chamadas, alterando os seus retornos ou até desligando-as. No trabalho eu tenho um objeto que sempre precisa ser mockado, o window.location. Em outras funções que, por ventura, precisam provocar o redirecionamento de uma página, eu acabo abstraindo o window.location para uma outra função - normalmente chamada de redirect - e assim posso testar a função que chamaria redirect, sem de fato, redirecionar a tela para outro destino no meio de um procedimento de testes, pois durante essa rotina o redirect está mockado e não vai de fato provocar uma mudança no window.location. E é também um ótimo exemplo onde já não vou conseguir 100% de cobertura de testes, pois não vou testar de fato essa redirect.

Exemplo de como ficariam essas funções:

{% highlight JavaScript %}
function redireciona( url ) {
	window.location = url;
}

function redirecionaSeForPrimo( numero ) {
	var primo = /* bloco que calcula se o numero é primo */;
	if ( primo === true ) {
		redireciona( 'http://example.org#primo' );
	}
}
{% endhighlight %}

E o Dexter mockando ela, considerando que ela estaria em um escopo global:

{% highlight JavaScript %}
test( 'redirecionaSeForPrimo', function () {
	var mock = Dexter.stub( window, 'redireciona' );
	mock.callback = function ( url ) {
		equa( url, 'http://example.org#primo', 'redireciona => http://example.org#primo' );
	};

	redirecionaSeForPrimo( 7 );

	// restauro a funcionalidade original do redirect quando acabo meus testes
	mock.restore();
});
{% endhighlight %}

Os exemplos acima são apenas com a intenção de ilustrar um cenário real.


--------
**WIDE: Para você, qual o papel do JS no desenvolvimento de aplicações mobile - um mercado que não para de crescer?**

**LEO BALTER** O JS é o que está mais presente no grande "tsunami" de tecnologias para mobile em 2014. O Firefox OS é um empurrãozinho da Mozilla para ajudar nesse processo. O Google já fez suas provas de conceito com o Chrome OS e ChromeCast, e agora com a Oracle cada vez mais tendendo a incomodar o Android por causa dos direitos do Java. Há uma tendência fortíssima para que o Google apareça por aí com uma espécie de Chrome OS para dispositivos móveis, que invista em aplicativos 100% web, ou seja, apontamos para HTML 5, mas na verdade estamos falando de muito código JS por trás dos panos.

O Firefox OS tem em sua interface uma tecnologia 100% web, todas as aplicações para o sistema são feitas em cima de HTML, CSS e JS. E enquanto aplicações normalmente exigem muita lógica que está exatamente no JS. Há muito tempo ele já deixou de ser apenas uma simples linguagem para validação de formulários ou troca de classes no DOM.

O iPhone foi - em seu lançamento - uma grande promessa de levar a web para os dispositivos móveis. A ideia inicial era de que os aparelhos só servissem aplicativos web, com HTML, CSS e JS; eles investiram forte no HTML5, mas não foram muito além em implementar APIs para comunicação completa com o hardware, como, por exemplo, usar a câmera. Eles voltaram atrás por conveniências comerciais e resolveram lançar a SDK para publicação de aplicativos nativos, que fazem o maior sucesso, até que você troque o aparelho. Com o empurrão de outras empresas, pois até a Blackberry está investindo na web para sua nova geração de aparelhos, não vai ser difícil para a Apple entrar no jogo e permitir que suas aplicações inteiramente web tenham APIs que estão se tornando padrões do HTML5.

Eu ainda não falei que todas as APIs de integração com hardware no Firefox OS se tornam propostas de padrões na W3C, certo? Isso significa que estamos indo a um futuro onde a web por si só estará totalmente integrada com câmera, áudio, bluetooth, cartão de memória etc.

**O JS não é tendência. JS é o mercado, é o presente e também o futuro.**

No último mês - ao tempo em que escrevo - eu vi o Daniel Filho fazer um air drone - um quadricóptero ser totalmente controlado por JS, com vários tipos de interações, desde a velocidade ao sensor de movimentos através da câmera. Se alguém falar que isso é um futuro remoto, lembre-se que a Amazon acabou de lançar a nova modalidade de entrega de produtos via AirDrones. Isso é o presente, já vivemos nessa época.

Eu mesmo também estava brincando com esses experimentos e fiz um carro a pilhas ser controlado por um controle de Playstation 3 através da API do meu navegador. E foi incrível. Da mesma forma estava brincando com um projeto no Github chamado [MeatSpaces](http://chat.meatspac.es) onde uso várias APIs de JS para bater papo em tempo real, gravar histórico no navegador e para cada mensagem gerar uma gif animada de dois segundos com a imagem da minha câmera. Tudo via JS e funcionando também em aparelhos móveis, como o Android e iPhone.


--------
**WIDE: Em sua opinião, existe algum detalhe que ainda pode ser aperfeiçoado na linguagem JS?**

**LEO BALTER** Há muita coisa que pode ser feita, uma delas é pura vaidade minha, mas gostaria que o nome mudasse. Adoro o primeiro nome da linguagem, na verdade é o nome do projeto: Mocha. Assim como preciso chamar apenas de JS ou ECMAScript. Ok, ECMA é um nome feio e acabo adotando o JS. Acontece que o nome "JavaScript" pertence como propriedade a uma empresa com interesses comerciais; esses outros nomes citados têm a liberdade de não terem ninguém com esses tipos de interesses por trás. A ideia de que o JS é livre é um fator importantíssimo para ele ter sucesso em um cenário de uma web de múltiplas tecnologias e dispositivos.

Há também muita coisa que poderia ser melhorada na API do DOM, que são as integrações do JS com os navegadores. Os problemas mais recorrentes se encontram muito mais nessa camada do que na linguagem em si.

Tem muita novidade também pra aparecer no ECMAScript 6. Eu mesmo estou assustado com a quantidade de assuntos novos que estou aprendendo e ainda preciso aprender. Mesmo assim, gosto desse desafio, pois sei que o JS está cada vez mais poderoso e tem tudo para prosperar por muito tempo. Uma questão interessante é que o ECMAScript 6 também toma como base muitos aperfeiçoamentos feitos em outras linguagens, inclusive aquelas experimentais de pré-processamento do JS, como o CoffeeScript e o Dart. Muitas experiências boas são tomadas do que é feito lá para trazer para o JS. Eu já fiz algumas sugestões ao pessoal do ES6, principalmente por ter contato com Perl e algumas de suas características.

**O JS está cada vez mais poderoso e tem tudo para prosperar por muito tempo**


Lembra quando falei anteriormente que qualquer sugestão é bem-vinda? Lembre-se que o pessoal do ES6 também aceita sugestões e estão abertos às opiniões públicas. Mas aí fica uma última dica preciosa: deixe a vaidade de lado. Nem tudo será aceito no mundo open source, por mais esforço que possamos ter, alguns Pull Requests vão ser recusados e sugestões ao ES6 também. Nem por isso é algo sem valor, pois essas decisões são tomadas por um escopo completo, maior do que a sugestão ou aquela única implementação. Além de tomar um saboroso café, ouça um pouco de Raul e lembre-se das suas sábias palavras: tente outra vez.
