---
layout: post
title:  "DexterJS e testes mais simples"
date:   2014-01-21 03:17:22
categories: pt-BR tests
---

Há mais de um ano eu escrevi o [DexterJS](https://github.com/leobalter/DexterJS), uma ferramenta em *JS* para me auxiliar em testes unitários. Até hoje eu utilizo bastante o DexterJS e admito que nunca foi muito fácil explicar do que se trata. Tudo fica mais difícil quando ainda temos uma grande massa de desenvolvedores que não tem muito contato com códigos testados. Pra acabar com mistérios vou escrever um pequeno histórico.

Eu precisava observar ou mockar totalmente chamadas internas em funções e não tinha isso diretamente utilizando o [QUnit](https://github.com/jquery/qunit), minha ferramenta favorita para testes até hoje. Foi quando tentei utilizar o *SinonJS*, ele continha algumas coisas que eu precisava, mas percebi que havia uma grande fatia de gordura, ou seja, havia muito mais do que eu queria utilizar. Muito mais.

### SinonJS e o excesso de API

O que eu queria do Sinon era fácil de encontrar já de cara: 'spy', 'stub' e 'mock'. Com isso eu poderia observar essas chamadas internas, inclusive alterando o retorno delas, com a opção de restaurar tudo depois. Foi nesse momento que vi que também era interessante _fakear/mockar_ o XHR (leia-se: Ajax). Uma das coisas mais enjoadas para execução de testes em JS é trabalhar com o assincronismo do XHR e contando com um servidor tosco para respostas pré-determinadas, placebos.

Em ambiente de testes não se conta com o mesmo servidor de desenvolvimento e nem produção, você faz um servidor tosco só para essas requisições XHR que estão contidas no seu JS a ser testado. Conta com o tempo de resposta das requisições, que não é agradável. E não conta com poder rodar os testes da forma mais estática possível, abrindo os testes em protocolo simples de arquivo `file://`. Se você não acredita no quanto é chato precisar de um servidor tosco, baixe o projeto do [jQuery no Github](https://github.com/jquery/jquery) e vá brincar de executar testes. 

Eu falei que encontrei mais do que gostaria no SinonJS, certo? Era justamente muita coisa que gostaria de não colocar no meu ambiente de testes, algumas que considero antipadrões de projetos, como inserir diversas variáveis no escopo Global, ou da ferramenta fazer a mesma coisa de diversas formas diferentes. Tão redundante como a frase anterior, o SinonJS tinha uma interface com excesso de recursos, não iria utilizar 5% e isso não é legal para ambiente de testes que precisa ser muito mais enxuto a aplicação que está sendo testada.

### Então começa o desenvolvimento do DexterJS

Parti pro desafio de escrever algo minimalista, algo que não me incomodasse, pois eu também não queria gastar mais tempo escrevendo uma documentação na wiki do projeto que seria testado para estabelecer uma convenção de como utilizar o SinonJS, já que ele poderia ser utilizado de _n_ formas diferentes.

Separei o que precisava, comecei com o `Dexter.spy` e `Dexter.fake`, antes chamado `.stub`. De forma simples, crio uma variável chamando uma dessas funções passando um objeto a ser tratado, com um segundo parâmetro sendo o nome do método que será espiado ou substituído por um objeto falso, que vai retornar o que eu quiser. Tudo isso com a opção de restaurar tudo ao normal, como se nada houvesse acontecido.

Por exemplo:

{% highlight JavaScript %}
// estou testando a função foo(), entre as coisas que ela faz, ela chama 
// internamente o `meuForm.reset()`, e quero observar chamadas feitas para 
// essa função
var spyReset = Dexter.spy( meuForm, 'reset' );

foo();

equal( spyReset.called, 1, 'spyReset foi chamado uma vez pelo foo()' );

// agora quero restaurar o meuForm.reset para não ser mais observado
Dexter.restore();
{% endhighlight %}

A grande diferença entre o `spy` e o `fake` é que o spy permite que a função original seja chamada, enquanto o fake vai substituir totalmente o seu funcionamento.

{% highlight JavaScript %}
var fakeCookies = Dexter.fake( meuApp, 'pegaCookies' );

// enquanto eu não atribuir um callback para o fakeCookies, a função
// `meuApp.pegaCookies` não vai retornar nenhum valor, logo:
fakeCookies.callback = function() {
	return 42;
};

// agora foo() é uma funcao que trabalha com o retorno de pegaCookies(),
// em uma lógica muito complexa, ele deveria retornar true
// se pegaCookies() retornar exatamente 42.
ok( foo(), 'foo() => true' );

// posso mudar o valor do callback a qualquer momento, inclusive incluir 
// asserções
fakeCookies.callback = function( type ) {
	strictEqual( type, 'bar', 'foo() chama pegaCookies("yay")' );

	return true;
};

// e agora vamos supor que foo() deveria chamar pegaCookies com um
// parâmetro específico, removendo os números de uma string
foo( '000yay000' );

Dexter.restore();
{% endhighlight %}


### São exemplos e não design patterns

Os exemplos de cima são apenas exemplos, não são design patterns. De longe eles não são exemplos que fiz pensando em explicar uma boa prática para o código. A minha preocupação era apenas mostrar como utilizar o DexterJS em tipos específicos de situações.

Há pouco tempo um amigo veio me pedir ajuda para testar algo bem específico. Ele tinha duas funções, uma que já estava testada e outra que seria testada, mas tudo que essa segunda função fazia era chamar uma série de outras funções. O exemplo dele foi exatamente um caso de uso ideal para usar o DexterJS. Logicamente eu removi nomes específicos da função dele e simplifiquei a lógica.

Aqui temos um trecho do código da ferramenta em si: 

{% highlight JavaScript %}
function Form( elem ) {
	this.elem = jQuery( elem );
}
 
// hide all errors
Form.prototype.hideErrors = function () {
	this.elem.find( '.js-validate' )
		.removeClass( 'error' );
};
 
// reset form
Form.prototype.resetForm = function () {
	this.elem[0].reset();
	 
	// hide errors
	this.hideErrors();
	 
	// hide message
	this.hideMessage();
};
{% endhighlight %}

Observando o exemplo acima, podemos ver que o resetForm apenas chama outras funções, o reset() do elemento, a hideErrors e a hideMessage, que está omitida no exemplo. Agora vamos aos testes (com QUnit):

{% highlight JavaScript %}
module( 'Form', {
	setup : function() {
		this.f = new Form( '.my-form' );
	}
}
 
test( 'hideErrors', function() {
	// simulação
	var elem = this.f.elem;
	elem.find( '.js-validate' ).addClass( 'error' );

	// chamando o método testado
	this.f.hideErrors();

	var errors = elem.find( '.js-validate.error' ).length;

	// asserções
	strictEqual( errors, 0, '0 .js-validate com classe .error' );
});
 
// agora vou testar o resetForm onde preciso observar a chamada 
// para outros métodos
test( 'resetForm', function() {
	var elem = this.f.$element,
		fakeReset = Dexter.fake( elem[0], 'reset' ),
		fakeHideErrors = Dexter.fake( this.f, 'hideErrors' ),
		fakeHideMessage = Dexter.fake( this.f, 'hideMessage' );

	this.f.resetForm();

	// a propriedade called indica quantas vezes cada uma das 
	// funções observadas foram chamadas.
	equal( fakeReset.called, 1, 'chamou form.reset()' );
	equal( fakeHideErrors.called, 1, 'chamou hideErrors()' );
	equal( fakeHideMessage.called, 1, 'chamou hideMessage()' );
	
	// restauro todos os objetos criados com Dexter.fake e Dexter.spy
	Dexter.restore();
});
{% endhighlight %}


### Integrável com outras ferramentas

O DexterJS só cria uma variável global, o `Dexter`. Ele é um objeto em forma de namespace e não vai encher o seu sistema de código extra, apenas 1 é o suficiente. Ao mesmo tempo, os métodos _observados_ com o Dexter não tem suas propriedades alteradas. Uma função espiada não vai ganhar uma propriedade `.called`, isso fica restrito à variável definida com o retorno da chamada do Dexter, a função espiada vai parecer e se comportar como se realmente fosse a original, e volta exatamente ao status de original quando restaurada.

Isso também possibilita que o Dexter seja facilmente utilizado com qualquer framework de testes, seja ele o QUnit, o Jasmine, Mocha, NodeUnit. Do browser ao node, o Dexter funciona em qualquer ambiente JS entre os mais populares, inclusive no IE7.

Além de baixar o código via Github ou no [site](http://dexterjs.com). O DexterJS também pode ser instalado via *bower* e *npm*, com um dos seguintes comandos:

{% highlight sh %}
bower install dexter
npm install dexter
{% endhighlight %}


### É um projeto Open Source

A parte mais incrível de escrever o DexterJS é justamente onde ele é Open Source, com licença que permite que ele seja utilizado livremente, inclusive para aplicações de fins comerciais, e com a ajuda expontânea de outras pessoas. Algumas colabararam com código, e faço questão de expor isso em forma de agradecimento: https://github.com/leobalter/DexterJS/graphs/contributors

No quesito responsabilidade, principalmente por ser Open Source e estar disponível a pessoas que criam expectativas de que tudo vai funcionar bem, o Dexter é mantido sob vários testes, com cobertura de código alta e utilizando o Travis-CI para integração contínua. Isso garante estabilidade, afinal, quem busca uma ferramenta para desenvolvimento quer se livrar de alguma dor de cabeça da rotina do trabalho no dia a dia, e não arrumar mais uma. Toda essa preocupação pela qualidade do código aumenta quando se trata de algo para auxiliar o ecossistema de testes unitários.