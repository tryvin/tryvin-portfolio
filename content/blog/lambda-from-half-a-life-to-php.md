---
title: "Λ (λ) - From Half-a-Life, to PHP"
date: 2018-10-08T20:54:26-03:00
draft: false
icon: "http://aux.iconspalace.com/uploads/1561617333.png"
image: "https://fawove.com/wp-content/uploads/2018/04/Download-1.jpg"
---

From Wikipedia:

is the 11th letter of the [Greek alphabet](https://en.wikipedia.org/wiki/Greek_alphabet "Greek alphabet"). In the system of [Greek numerals](https://en.wikipedia.org/wiki/Greek_numerals "Greek numerals") lambda has a value of 30.&nbsp;

From Half-life wikia:

In the original _Half-Life_, [Gordon Freeman](http://half-life.wikia.com/wiki/Gordon_Freeman "Gordon Freeman")'s trademark [HEV Suit](http://half-life.wikia.com/wiki/HEV_Suit "HEV Suit") was marked with a Lambda Logo on the chest, as were other [HEV Suits](http://half-life.wikia.com/wiki/HEV_Suit "HEV Suit"). A section of Black Mesa dedicated to teleport research was also called the "Lambda Complex", and is identifiable by the Lambda logo at its entrance.

But what does this symbol has to do with PHP?

Well, it’s the name we at computer programming gives to anonymous functions, which, again with the definitions, from Wikipedia:

In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), an **anonymous function** (also **function literal** or **lambda abstraction**) is a [function](https://en.wikipedia.org/wiki/Function_(computer_science) "Function (computer science)") definition that is not [bound](https://en.wikipedia.org/wiki/Name_binding "Name binding") to an [identifier](https://en.wikipedia.org/wiki/Name_(computer_science) "Name (computer science)"). Anonymous functions are often:

1 - arguments being passed to [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function "Higher-order function"), or
2 - used for constructing the result of a higher-order function that needs to return a function.

We all know that computer languages has functions, and if it’s a OOP language, has classes, interfaces, packages, and the list goes on. But with all these organizations, how can we make simple functions, that are used only in a piece of the code? Rapid functions, rapid development (ain’t that what the web is all about? Rapid, rapid, rapid)

The anonymous functions came to help. Imagine the situation (i’m gonna give the example in PHP, but you would port it to any language you imagine):

I have an template, and this template uses a function, which gets an array, and transforms it in a HTML select, this function, runs this array and use the key as the HTML option value, and the value, as the HTML option text. (I’m talking about html_options from Smarty here), but my original array, which cames from the database is a multidimensional array, like this one here:

Array( Array(&nbsp;‘databaseId’ =&gt; 1,&nbsp;‘databaseValue’ =&gt;&nbsp;‘Hello’) )

How could I transform this into:

Array(1 =&gt;&nbsp;‘Hello’)

You could make something like this:

https://gist.github.com/tryvin/430e0e74a50d8b8bd03b

But we could revamp this a while, and use [array_map](http://php.net/manual/en/function.array-map.php), it takes a PHP callback as first argument, and an array as the second (and so on) argument. Then this function starts executing the callback for every element in the input arrays. But how could this use lambda functions? Well, as we all know, PHP callbacks are functions, whatever they are from a class, a main function, or even a **LAMBDA!**&nbsp;See the code above, using lambda, and see it became more readable:

https://gist.github.com/tryvin/8c00e95e2775ed4ad757

Yes, I know, it’s the same&nbsp;“size”, but now imagine, you have some processing to do. You need to insert some filters into your array, change some values, execute something while it’s mapping, the uses are endless. And this is only one use of lambda with array_map. Lamdbas can be used for anything, it’s a function for god sake.

Say yes to lamdba, and no to creating __functionToMapping, or __mySecretFunctionWhichOnlyAddUserCalls and so on!

Oh, and don’t forget, even if it’s a pretty oldie game, you could give Half-life a try, even if playing it in a big screen gives me headaches =/
