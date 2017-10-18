# Debugging JavaScript 101

## Repo for the presentation @ BadCamp 2017

- [1_0_whoAmI:](#1_0_whoami)
- [1_1_console.log](#1_1_consolelog)


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


