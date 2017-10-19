# Debugging JavaScript 101

## Repo for the presentation @ BadCamp 2017

- [1_0_whoAmI:](#1_0_whoami)
- [1_1_console.log](#1_1_consolelog)
- [1_2_other_console_methods](#1_2_other_console_methods)
- [2_0_expressions](#2_0_expressions)
- [2_1_watch_and_breakpoints](#2_1_watch_and_breakpoints)
- [2_2_conditional_breakpoints](#2_2_conditional_breakpoints)
- [3_1_scopes](#3_1_scopes)
- [3_2_call_stack](#3_2_call_stack)
- [4_0_dom_breakpoints](#4_0_dom_breakpoints)
- [4_2_ajax](#4_2_ajax)

# 1_0_whoAmI

```javascript
function whoAmI() {
    var name = 'My Name';
    var company = 'My Company';
    var string = 'I am ' + name + ' and I work @ ' + company;
    return string;
}

// jQuery
//$('h1').text(whoAmI());

// Plain JavaScript
// var h1s = document.getElementsByTagName('h1');
// h1s[0].innerText = whoAmI();
```

# 1_1_console.log

```javascript
// I stoped relaying on console logging a few months ago. :) for my local development.

// console.log(1 + 1);

// console.log(jQuery);

// var name = 'Israel Morales';
// var numero = 1;

// console.log(name);

// console.log(typeof name);

// console.log(numero);

// console.log(typeof numero);

// there's a better way.

// numero;
// name;
```
# 1_2_other_console_methods

```javascript
// example of object.

var Person = {
    name: 'Israel',
    lastname: 'Morales',
    sayName: function() {
         // return this.name + ' ' + this.lastname;
         return `${this.name} ${this.lastname}`
    }
}

console.info('Important info information');

console.log(Person);

console.dir(Person);

console.warn('Warning');

console.error('Error');
```
# 2_0_expressions

```javascript
var numero = 1;

// console.log(typeof numero === 'number')

// console.log(numero >= 1);

// console.log(numero > 5);
```

# 2_1_watch_and_breakpoints

```javascript
// basic breakpoint.

var numero;
numero = 1;
numero = 2;
numero = 3;

// click on line 5 and execute code.
```

# 2_2_conditional_breakpoints

```javascript
var numeros_array = [1,2,3,4,5];

numeros_array.forEach(function(numero) {
    numero;
})

// jQuery version.
// $(numeros_array).each(function(numero) {
//    numero;
// });

// clean format.
// numero === 3 in line 5
```

# 3_1_scopes

```javascript
var a_scope_description = 'Outer scope';

a_scope_description;

function simpleFunction() {

    var a_scope_description = 'Inner scope';

    a_scope_description;

};

simpleFunction();

// Breakpoint: in line 3 and 9.
// Watch: a_scope_description
```

# 3_2_call_stack

```javascript
function firstCall() {
    secondCall();
}

function secondCall() {
    thirdCall();
}

function thirdCall() {
    console.log('wooow');
}

firstCall();
```

# 4_0_dom_breakpoints

```javascript
// we add the dom breakpoint in Elements

// the following code is going to change the color of the text.

$(document).on('click', 'h1', function(evt) {
    evt.stopPropagation();
    evt.preventDefault();
    $(this).css('color', 'blue');
});
```

# 4_2_ajax

```javascript
// Dogs API

$.ajax({
    url: 'https://dog.ceo/api/breeds/list',
    type: 'GET'
}).done(function(data) {
//     data;
    if (data.status === 'success') {
        console.log(data.message);
        listBreeds(data.message);
    }
}).fail(function(data) {
//     data;
    if (data.status !== 'success') {
        console.error('Huge error');
    }
});

function listBreeds(dataArray) {
    var items = '';

//     dataArray.forEach(function(item) {
//         items = items + `<li>${item}</li>`;
//     });

    var result = dataArray.map(function(item) {
        return `<li>${item}<\/li>`;
    });

    // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map
    // http://es6-features.org/#StringInterpolation

    $('.dog-list').append(result);
}
```

# Extra resources
- https://developer.mozilla.org/en-US/docs/Web/JavaScript
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects
- https://github.com/getify/You-Dont-Know-JS/
- http://es6-features.org/
- http://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=DYUwLgBAFizA9hAvBAFAOwIYFsQEpkA-CAbwCgIIBjedAZ3lADoEBzVAAwAlYEIASEllwBfDnjIiyoSMJDIIAcgCWdAE6ZYigNxkyMOPAw58egG6Y1EOmDXL0rBR2wBPCHIiqAXAKEmxQA&debug=false&circleciRepo=&evaluate=true&lineWrap=false&presets=es2015%2Creact&targets=&version=6.26.0
