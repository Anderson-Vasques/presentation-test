@title[FrontEnd jQuery]
# FrontEnd
# jQuery

---
@title[jQuery ???]

###### jQuery é uma biblioteca que torna a manipulação de elementos, adição/remoção de eventos, animação e ajax muito mais simples. Tem uma API simples e funciona nos mais variados browsers.

![Press Down Key](assets/down-arrow.png)

+++
@title[javascritp x jQuery]


```javascript
var hiddenBox = document.getElementById("banner-message");
var button = document.querySelector("#button-container button");
button.addEventListener( "click", function( event ) {
  hiddenBox.style.display = "";
});
```

```javascript
var hiddenBox = $( "#banner-message" );
$( "#button-container button" ).on( "click", function( event ) {
  hiddenBox.show();
});
```

+++

### O jQuery permite o encadeamento de métodos para o mesmo alvo:

```javascript
$("#p1").css("color", "red")
    .slideUp(2000)
    .css("height", "auto")
    .show();
```
#### Os métodos **css**, **slideUp** e **show** - ainda veremos o que cada um faz, são aplicados todos no elemento com o id **p1**


---

### Efeitos

![Press Down Key](assets/down-arrow.png)

+++
@title[hide/show efect]

###### Escondendo elementos com o método **hide()**

```javascript
var paragraphs = $('p');
paragraphs.hide();
```

@[1](Selecionar todos as tags **p** do documento)
@[2](Esconder todas as tags **p**. O jQuery modifica o estilo do elemento adicionando um atributo **style** e adiciona o valor **none** para a propriedade **display**)

+++
@title[hide/show efect with time - explained]
###### O método hide (asssim como o método show e o método toggle) aceita dois parâmetros. O primeiro é o tempo (em milesegundos - 1000, por exemplo - ou uma string com 'slow' ou 'fast') que a animação vai durar. O segundo é uma função que vai ser chamada assim que a animação terminar.

+++
@title[hide/show efect with time]

```javascript
var container = $('#container');
container.hide(1000, function() {
    console.log('O efeito terminou!!!');
});
```

@[1](Selecionar o elemento com id **container**)
@[2-4](Esconder o elemento com id **container**. O jQuery modificará a opacidade do elemento atual - o valor é 1 por padrão -, o width atual será decrescido até 0 - ou min-width, se aplicável - e o height atual será decrescido até 0 - ou min-height, se aplicável. Após isso, o jQuery adicionará o valor **none** para a propriedade **display** do elemento e em seguida executará a função de callback. O tempo percorrido do inicio ao fim do efeito será de 1 segundo.)

+++
@title[show efect]
###### Mostrando elementos com o método **show()**

```javascript
var paragraphs = $('p');
paragraphs.show();
```
@[1](Selecionar todos as tags **p** do documento)
@[2](Mostrar todas as tags **p**. O jQuery modifica o estilo do elemento removendo o valor da propriedade **display** caso ela esteja com o valor **none** no atributo **style**. Caso o elemento esteja com o estilo **display: none** no css, o jQuery exibe o elemento adicionando o atributo **style="display: block;"**.)

+++
@title[show efect with time - explained]
###### O método show aceita dois parâmetros. O primeiro é o tempo (em milesegundos - 1000, por exemplo - ou uma string com 'slow' ou 'fast') que a animação vai durar. O segundo é uma função que vai ser chamada assim que a animação terminar.


+++
@title[show efect with time]

```javascript
var container = $('#container');
container.show(1000, function() {
    console.log('O efeito terminou!!!');
});
```

@[1](Selecionar o elemento com id **container**)
@[2-4](Mostrar o elemento com id **container**. O jQuery exibirá o elemento com width:0, height:0 e opacity:0, e aumentará esses valores progressivamente em 1 segundo. Ao final do efeito a mensagem **O efeito terminou!!!** será exibida no console.)

+++
@title[toggle efect with or without time explained]
###### O método toggle serve para alternar entre os estados de show e hide. Assim como os métodos já comentados, toggle aceita dois parâmetros (que são opcionais): um tempo e uma função para ser chamada ao final do efeito


+++
@title[toggle efect without time ]

```javascript
var container = $('#container');
container.toggle();
```

@[1](Selecionar o elemento com id **container**)
@[2-4](Troca entre show e hide. Se o elemento estiver sendo exibido ele será escondido. Se o elemento não estiver visível ele será exibido. Como o paramâetro de tempo não foi definido, a troca entre os estados ocorrerá instantaneamente)


+++
@title[toggle efect without time ]

```javascript
var container = $('#container');
container.toggle(1000, function() {
    console.log('O efeito terminou!!!');
});
```

@[1](Selecionar o elemento com id **container**.)
@[2-4](Alterar entre o estado **hide** e **show** aplicando o respectivo efeito. Ao final do efeito a mensagem **O efeito terminou!!!** deve ser exibida no console.)

+++
@title[fadeIn fadeOut fadeToggle ]
### fadeIn, fadeOut e fadeToggle

+++
@title[fadeIn fadeOut fadeToggle explained ]
###### A familia de métodos fade aplica um efeito de 'esvanecer' e tem a mesma assinatura dos metodos show/hide/toggle.
###### Nessa animação apenas a opacidade e o display do elemento mudam.

+++
@title[fadeOut example ]

```javascript
var container = $('#container');
container.fadeOut();
```
@[2](O elemento com id **container** terá sua opacidade reduzida a 0 em 400 milesegundos - tempo padrão caso nenhum outro valor seja especificado. Após 400 milesegundos, quando o elemento estiver com a **opacidade** igual a 0, o valor da propriedade **display** é modificado para **none** em um atributo **style**.)

+++
@title[fadeIn example ]

```javascript
var container = $('#container');
container.fadeIn(1000, function() {
    console.log('O efeito terminou!!!');
});
```
@[2-4](O **display** do elemento será modificado da mesma maneira que no método **show**. Após isso a **opacidade** será aumentada progressivamente do valor atual até 1 em 1 segundo, e então a mensagem **O efeito terminou!!!'** será exibida no console.)

+++
@title[fadeToggle example ]

```javascript
var container = $('#container');
container.fadeToggle(1000, function() {
    console.log('O efeito terminou!!!');
});
```
@[2-4](O estado irá alternar entre fadeIn e fadeOut, com animação de 1 segundo. Após o termino da animação a mensagem **O efeito terminou!!!'** será exibida no console.)

+++
@title[slideUp slideDown slideToggle ]
### slideUp, slideDown e slideToggle

+++
@title[slideUp slideDown slideToggle explained ]
###### A familia de métodos slide aplica um efeito de expandir ou recolher e tem a mesma assinatura dos metodos show/hide/toggle.
###### Nessa animação apenas a altura e o display do elemento mudam. A altura é modificada progressivamente durante a animação.

+++
@title[slideUp example ]

```javascript
var container = $('#container');
container.slideUp();
```
@[2](O elemento com id **container** terá sua altura reduzida a 0 em 400 milesegundos - tempo padrão caso nenhum outro valor seja especificado. Após 400 milesegundos, o valor da propriedade **display** é modificado para **none** em um atributo **style**.)

+++
@title[slideDown example ]

```javascript
var container = $('#container');
container.slideDown(1000, function() {
    console.log('O efeito terminou!!!');
});
```
@[2-4](O **display** do elemento será modificado da mesma maneira que no método **show**. Após isso a **altura** será aumentada progressivamente do valor atual até o valor máximo em 1 segundo, e então a mensagem **O efeito terminou!!!'** será exibida no console.)

+++
@title[slideToggle example ]

```javascript
var container = $('#container');
container.slideToggle(1000, function() {
    console.log('O efeito terminou!!!');
});
```
@[2-4](O estado irá alternar entre slideUp e slideDown, com animação de 1 segundo. Após o termino da animação a mensagem **O efeito terminou!!!'** será exibida no console.)

+++
@title[animate ]
### Animate
##### Com o método animate podemos criar animções ao fazer uma transição entre valores de várias propriedades css.

+++
@title[animate explained]
###### Uma das formas mais simples do método animate recebe 3 parametros. O primeiro é um objeto com as propridades css e seus respectivos valores que a animação irá efetuar,o segundo é um numero ou uma string informando a duração da animação e o terceiro parametro é uma função que vai ser executada quando a animação terminar.

+++
@title[animate example]
```javascript
var box = $('#box');
box.animate(
    {
        left: 140,
        width: '200px',
        opacity: .5
    },
    2000,
    function() {
        console.log('Animação concluída');
    }
);
```
@[3-7](Objeto com as propriedades css que devem ser modificadas até o fim da animação.)
@[8](Tempo de duração da animação.)
@[9-11](Função que vai ser executada quando a animação terminar.)

+++
@title[animate chain]
Diferentente dos outros efeitos vistos até agora, o método animate pode ser encadeado.

```javascript
var box = $(".box");
        box.animate({height: '300px',opacity: '0.4'}, "slow", function() {
            console.log('primeira fase completa')
        });
        box.animate({width: '300px', opacity: '0.8'}, 800, function() {
            console.log('segunda fase completa')
        });
        box.animate({height: '100px', opacity: '0.4'}, "slow",function() {
            console.log('terceira fase completa')
        });
        box.animate({width: '100px', opacity: '0.8'}, "slow",function() {
            console.log('quarta fase completa')
        });
```

+++
@title[animate chain explained]
###### Quando a primeira fase da animação for concluída, a segunda fase começará. Ao final da segunda fase, a terceira fase será iniciada...


+++
@title[stop]
#### O método stop serve para parar um efeito ou animação em um ou mais elementos. A animação do elemento selecionado encerrará no momento em o método stop for executado.
###### Esse método funciona com todos efeitos vistos até agora.

+++
@title[stop example html]

```html
    <div id="container"></div>
    <button id="stop-efect">Interromper efeito</button>
```
+++
@title[stop example javascript]

```javascript
    var container = $('#container');
    var button = $('#stop-efect');
    container.fadeOut(10000);
    button.on('click', function() {
        container.stop();
    });
```
@[3](Disparando efeito de fadeOut no elemento de id **container**.)
@[4-6](Adicionando evento de click no elemento de id **stop-efect**. Dessa maneira o efeito será encerrado no momento em que o button for clicado.)
@[5](Parando o efeito de fadeOut.)

+++
@title[stop animation example html]
```html
    <div id="container"></div>
    <button id="stop-animation">Interromper animação</button>
```

+++
@title[stop animation example javascript]

```javascript
    var container = $('#container');
    var button = $('#stop-animation');
    container.animate({left: '400px'}, 10000);
    button.on('click', function() {
        container.stop();
    });
```
@[3](Disparando animação no elemento de id **container**.)
@[4-6](Adicionando evento de click no elemento de id **stop-animation**. Dessa maneira animação será encerrada no momento em que o button for clicado.)
@[5](Parando animação. O elemento vai ficar no estado que estava quando o button foi clicado.)

---
### HTML

![Press Down Key](assets/down-arrow.png)


+++
@title[text html append prepend ... methods]
##### o jQuery possui métodos para interagir com o DOM. Com jQuery é possivel adicionar, editar e remover texto, elementos e atributos.

+++
@title[text method]
###### Para adicionar ou pegar o texto de um elemento podemos utilizar o método text.

+++
@title[text method get mode html]
```html
...
<p id="paragraph">Hello World</p>
...
```
+++
@title[text method get mode javascript]
```javascript
var paragraph = $('#paragraph');
console.log(paragraph.text());
```
@[1](Selecioar o elemento com id **paragraph**.)
@[2](O texto **Hello World** será exibido no console.)

+++
@title[text method get mode 2 html]
```html
...
<p id="paragraph">
    Hello World
    <a target="_blank" href="http://wwww.google.com"> Acesse o google</a>
</p>
...
```

+++
@title[text method get mode 2 javascript]

```javascript
var paragraph = $('#paragraph');
console.log(paragraph.text());
```
@[1](Selecioar o elemento com id **paragraph**.)
@[2](O texto **Hello World Acesse o google** será exibido no console.)

+++
@title[text method set mode]
### Também é possível adicionar texto em um elemento com o método text, basta passarmos o uma string como parâmetro


+++
@title[text method set mode example]

```html
...
<p id="paragraph">Hello World</p>
...
```

```javascript
var paragraph = $('#paragraph');
paragraph.text("Esse texto foi adicionado via javascript");
```

+++
@title[text method set mode example continued]
###### Resultará no seguinte: 

```html
...
<p id="paragraph">Esse texto foi adicionado via javascript</p>
...
```

+++
@title[text method set mode example 2]

```html
...
<p id="paragraph">
    Hello World
    <a target="_blank" href="http://wwww.google.com">Acesse o google</a>
</p>
...
```

```javascript
var paragraph = $('#paragraph');
paragraph.text("Esse texto foi adicionado via javascript");
```

+++
@title[text method set mode example 2 continued]
###### Resultará no seguinte: 

```html
...
<p id="paragraph">Esse texto foi adicionado via javascript</p>
...
```

+++
@title[html method]
###### Sem quiser pegar o html de dentro de um elemento, basta usar o método html. Também é possivel passar um parâmetro se quiser adicionar conteúdo html para uma página.

+++

@title[html method get mode html]
```html
...
<p id="paragraph">
    Hello World
    <a target="_blank" href="http://wwww.google.com">Acesse o google</a>
</p>
...
```

+++
@title[html method get mode javascript]

```javascript
var paragraph = $('#paragraph');
console.log(paragraph.html());
```
@[2](A seguinte mensagem deve aparecer no console:)

+++

```html
@title[html method get mode result]
Hello World 
 <a target="_blank" href="http://wwww.google.com">Acesse o google</a>
```


+++
@title[html method set html]
```html
...
<p id="paragraph">
    Hello World
    <a target="_blank" href="http://wwww.google.com">Acesse o google</a>
</p>
...
```

+++
@title[html method set mode javascript]

```javascript
var paragraph = $('#paragraph');
paragraph.html('<span>Esse texto foi adicionado via javascript<span>');
```

resultará em

```html
...
<p id="paragraph">
    <span>Esse texto foi adicionado via javascript<span>
</p>
...
```

+++
@title[attr]
### É possivel acessar os atributos dos elementos com o método attr. O método, em suas formas mais simples, aceita como parametros um objeto ou duas strings

```html
...
<a id="pudim" href="http://www.pudim.com.br">O melhor site de todos os tempos</a>
...
```

+++
@title[attr continued]
Ao passar somente uma string, o método retornará o valor do atributo.

```javascript
var pudimLinkElement = $('#pudim');
console.log(pudimLinkElement.attr('href'));
```
@[1](Selecionando o elemento e armazenando-o em uma variável.)
@[2](Mostrando no navegador a string **http://www.pudim.com.br**.)

+++
@title[attr object example html]
Também é possivel adicionar ou modificar um ou mais attributos de um elemento
```html
...
<a id="pudim" href="http://www.pudim.com.br">O melhor site de todos os tempos</a>
...
```

+++
@title[attr object example javascript]
```javascript
var pudimLinkElement = $('#pudim');
pudimLinkElement.attr('href', 'http://instantrimshot.com/');
pudimLinkElement.attr({
        target: '_blank',
        title: 'Acesse aqui'
    });
```
@[2](Trocando o valor do atributo href por http://instantrimshot.com/.)
@[3-6](Também é possivel adicionar ou modificar mais de um atibuto ao mesmo tempo. Nesse caso passamos um objeto onde a chave vai ser o nome do atributo e o valor será seu novo valor.)

+++
@title[attr object example result]

###### o resultado será:
```html
<a id="pudim" target="_blank" title="Acesse aqui" href="http://instantrimshot.com/">O melhor site de todos os tempos</a>
```

+++
@title[val method]
#### O método val nos permite pegar ou editar o atributo value de um elemento.

+++
@title[val html example]
```html
<div>
    <form id="nameForm" action="api/sendName">
        <label for="name">Digite seu nome</label>
        <input id="name" type="text" name="username" value="Anderson" />
    </form>
</div>
```
+++
@title[val javascript example]
```javascript
var input = $('#name');
var inputValue = input.val();
console.log(inputValue);
input.val('Fulano');
console.log(inputValue);
```
@[1](Selecionando o elemento com id **name**.)
@[2](Armazenando o conteúdo do atributo value - ou seja, o valor do input - em uma variável.)
@[3](No console do navegador aparecerá a mensagem **Anderson**.)
@[4](Modificando o conteúdo do atributo value do elemento para **Fulano**.)
@[5](No console do navegador aparecerá a mensagem **Fulano**.)

+++
@title[class]
##### Outro atributo especial é o atributo class. Temos métodos especificos para adicionar classes, remover classes, alternar classes e testar classes

+++
@title[addClass html]

```html
<div class="content">
    <div class="box el"></div>
    <div class="circle el"></div>
</div>
```

+++
@title[addClass javascript]

```javascript
$('.el').addClass('green');
$('.circle').addClass('pi ball');
```
@[1](Adicionando a classe **green** em todos elementos com classe **el**)
@[2](Adicionando as classes **pi** e **ball** em todos elementos com classe **circle**)

+++
@title[addClass html result]
O resultado será uma mudança no html:

```html
<div class="content">
    <div class="box el green"></div>
    <div class="circle el pi ball"></div>
</div>
```

+++
@title[removeClass javascript]

```javascript
$('.el').removeClass('green');
$('.circle').removeClass('pi ball');
```
@[1](Removendo a classe **green** em todos elementos com classe **el**)
@[2](Removendo as classes **pi** e **ball** em todos elementos com classe **circle**)

+++
@title[removeClass html result]
O resultado será uma mudança no html:

```html
<div class="content">
    <div class="box el"></div>
    <div class="circle el"></div>
</div>
```

+++
@title[toggleClass]
###### Podemos alternar as entre remover e adicionar classes com o método toggleClass

```html
<div class="content">
    <div class="box el"></div>
    <div class="circle el"></div>
</div>
```

+++
@title[toggleClass javascript]

```javascript
$('.el').toggleeClass('green');
$('.circle').toggleeClass('pi ball');
```

+++
@title[toggleClass html]
O resultado será uma mudança no html:

```html
<div class="content">
    <div class="box el green"></div>
    <div class="circle el pi ball"></div>
</div>
```

+++
@title[toggleClass javascript 2]
```javascript
$('.el').toggleeClass('green');
$('.circle').toggleeClass('pi ball');
```
+++
@title[toggleClass html 2]
O resultado será uma mudança no html:
```html
<div class="content">
    <div class="box el"></div>
    <div class="circle el"></div>
</div>
```

+++
@title[hasClass]
###### Podemos testar se um elemento tem uma determinada classe com o método hasClass. O método recebe como parâmetro uma string e retorna true se o elemento tiver uma classe com o mesmo valor da string e false caso contrário.

```html
<div class="content">
    <div class="box el"></div>
    <div class="circle el green"></div>
</div>
```

+++
@title[hasClass javascript]
```javascript
var box = $('.box');
var isGreen = box.hasClass('green');
if(isGreen) {
    console.log('O elemento .box é verde.');
}else {
    console.log('O elemento .box NÃO é verde.');
}
```
@[1](Selecionando o elemento com classe **box**.)
@[2](O elemento não tem a classe **green**, portanto o método **hasClass** retorna **false**. O valor é armazenado na variavel **isGreen**.)
@[5-7](**isGreen** é false, portanto a somente o que tem no bloco **else** é executado. A mensagem **O elemento .box NÃO é verde.** deve aperecer no console.)

+++
@title[append]
###### O método append permite a adição de conteúdo no final de um elemento

+++
@title[append html]

```html
<div id="main-content">
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
</div>
```

+++
@title[append javascript]

```javascript
var mainContent = $('#main-content');
mainContent.append('Esse texto deve aparecer no final da elemento <a href="#"> bem como esse link</a>');
```
@[2](Adicionando conteúdo no final da div. Esse conteúdo pode ser uma string ou um elemento.)

+++
@title[append html result]

O resultado será:
```html
<div id="main-content">
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
    Esse texto deve aparecer no final da elemento <a href="#"> bem como esse link</a>
</div>
```

+++
@title[prepend]
###### O método prepend permite a adição de conteúdo no inicio de um elemento

+++
@title[prepend html]

```html
<div id="main-content">
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
</div>
```

+++
@title[prepend javascript]

```javascript
var mainContent = $('#main-content');
mainContent.prepend('Esse texto deve aparecer no inicio da elemento <a href="#"> bem como esse link</a>');
```
@[2](Adicionando conteúdo no inicio da div. Esse conteúdo pode ser uma string ou um elemento.)

+++
@title[prepend html result]

O resultado será:
```html
<div id="main-content">
    Esse texto deve aparecer no inicio da elemento <a href="#"> bem como esse link</a>
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
</div>
```

+++
@title[before]
###### O método before permite a adição de conteúdo no antes de um elemento

+++
@title[before html]

```html
<p>Um parágrafo antes da div</p>
<div id="main-content">
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
</div>
<p>Um parágrafo depois da div</p>
```

+++
@title[before javascript]

```javascript
var mainContent = $('#main-content');
mainContent.before('Esse texto deve aparecer antes da elemento <a href="#"> bem como esse link</a>');
```
@[2](Adicionando conteúdo no antes da div. Esse conteúdo pode ser uma string ou um elemento.)

+++
@title[before html result]

O resultado será:
```html
<p>Um parágrafo antes da div</p>
Esse texto deve aparecer antes da elemento <a href="#"> bem como esse link</a>
<div id="main-content">
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
</div>
<p>Um parágrafo depois da div</p>
```

+++
@title[after]
###### O método after permite a adição de conteúdo no depois de um elemento

+++
@title[after html]

```html
<p>Um parágrafo antes da div</p>
<div id="main-content">
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
</div>
<p>Um parágrafo depois da div</p>
```

+++
@title[after javascript]

```javascript
var mainContent = $('#main-content');
mainContent.after('Esse texto deve aparecer depois do elemento <a href="#"> bem como esse link</a>');
```
@[2](Adicionando conteúdo depois da div. Esse conteúdo pode ser uma string ou um elemento.)

+++
@title[after html result]

O resultado será:
```html
<p>Um parágrafo antes da div</p>
<div id="main-content">
    <h1>Apenas um cabeçalho</h1>
    <p>Uma tag p</p>
</div>
Esse texto deve aparecer antes da elemento <a href="#"> bem como esse link</a>
<p>Um parágrafo depois da div</p>
```

---
### Dimensões
@title[dimensions]
![Press Down Key](assets/down-arrow.png)

+++
@title[dimensions explained]
###### O jQuery possui um conjunto de métodos para trabalharmos com as dimensões dos elementos. Com esses métodos é possivel pegar ou editar o tamanho de elementos.

+++
@title[dimensions explained image]
###### [Dimensões](https://www.w3schools.com/Jquery/jquery_dimensions.asp)

![Dimensões dos elementos](assets/img_jquerydim.gif)

---

### Aprenda mais:
###### Links de referência [w3c jquery](https://www.w3schools.com/Jquery/default.asp), [jQuery](https://jquery.com/ ), [CSS](https://www.w3schools.com/css/default.asp), [CSS Maujor](http://www.maujor.com/tutorial/intrtut.php), [Exemplos](https://github.com/Anderson-Vasques/Realiza-exemplos) e [NOTAS DE AULA](https://github.com/Anderson-Vasques/Realiza-exemplos/blob/master/Notas%20de%20aula.txt)