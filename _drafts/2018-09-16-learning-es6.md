
### Introduction

JavaScript is the language to learn if you want to build interative webpages that run on the browser. JavaScript is 
one of the most popular languages and it runs pretty much everywhere. It's used for developing desktop application
(ex. Electron), for creating mobile applications(ex. React Native) and can even be found on the server(such as nodeJS).

### Webpack

#### Setup

##### Install NodeJs

Download NodeJs from [https://nodejs.org/en/](https://nodejs.org/en/).

##### Install Git

Most Linux or Mac OS systems should have git by default, if not you can install it using the brew or apt command.

On Mac OS:

```bash
brew install git
```

On a Linux system:

```bash
sudo apt install git
```

##### Clone the web starter pack

Clone or download the [webpack-starter](https://github.com/wbkd/webpack-starter) code.

```bash
git clone https://github.com/wbkd/webpack-starter.git
```

Then cd into the directory webpack-starter and run:

```bash
npm install
```

And then to run the development server with auto refresh do:

```bash
npm run start
```

Open up `index.js` to start coding in JS.

### Constants, Let and Var

![ES6 and JS](/public/images/2018-09-16-learning-es6/es6_cover.png)

After refreshing the basics of JavaScript, I decided to learn ES6 which is a newer version of JavaScript released in 2015. 
ES6 is the sixth major release of the ECMAScript language specification that adds significant new syntax for writing 
complex applications like classes, modules and arrow functions.

Most modern browsers have implemented these features, thus we don't need a transpiler like Babel to user any of these new
language features.

### Let, Const

Let allows you to create variable declaration with block scoping(A block here is the code inside`{}`). 
Instead of using var which provides function scope. It is a good practise to use block scoped 
variables(`let` and `const`) in Es6.

{% highlight html %}

  <p id="output"> </p>

  <script>
  let output = document.getElementById("output");
  {
    let a = 3;
    let b = 4;
    display(a + b); // output 7
  }

  display(a + b); // Uncaught ReferenceError: a is not defined

  function display(val) {
    output.innerHTML += val + "<br>";
  }
  </script>

{% endhighlight %}

`Const` is also block scoped, but unlike `let` it makes the variable a constant pointer to an `Object`. Once 
declared you cannot assign it to a new Object or value, but can add to the content of an `Array` or `Object`. 
Only the reassignment of a `const` variable is prevented.

{% highlight javascript %}
{
    const a = 5;
    a = 6;          // Uncaught TypeError: Assignment to constant variable.
    const arr = [1, 2, 3]
    console.log(arr);   // [1, 2, 3]
    arr.push(4)
    console.log(arr);   // [1, 2, 3, 4]
}
{% endhighlight %}

Template strings
Spread(...) operator

Functions:

- Default parameters
- Rest paramaters(...)
- Arrow functions

Destructuring assignment
Ex: map, filtering
Classes
Modules, export, default
