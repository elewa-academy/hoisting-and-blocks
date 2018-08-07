# Hoisting & Blocks

Vocab check:
* _declared_:  When you tell JS to make a new variable in memory.  
* _defined_:  When a value is first assigned to a new variable
* _visible_: A variable is _visible_ in a scope iff it can be used in that scope.
* _hoisted_:  When JS declares a variable and moves it to the global scope in the __creation phase__ .


___

## with "var"


```js
inner_var = "defined";
{
  var inner_var;
};
```
[puytut](https://goo.gl/2RQoQL)

0. JS declares "inner_var" and _hoists_ it to the global scope.  It is now _visible_ in all other scopes.
1. JS defines "inner_var" as {String, "defined"}.
2. JS executes reaches the statement where "inner_var" was declared.  But it was already declared in the __creation phase__, so there's nothing to do.
3. Final state. "inner_var" is still visible at the global scope, with final value {String, "defined"}.


___

## with "let"


```js
let outer_let = "global";
null;
{
  let inner_let = "block 1";
  null;
};
```
[pytut](https://goo.gl/AyNdoR) 

0. Nothing happens in the __creation phase__, there are no "var" variables or functions to hoist.
1. JS _declares_ & _defines_ "outer_let" in a single statement.
2. The new block scope is created, with "inner_let" declared but in the __temporal dead zone__. ("null" is a placeholder.)
3. "inner_let" is _defined_ as "block 1". Both "outer_let" and "inner_let" are _visible_ in the block scope.
4. The block scope is destroyed, "inner_let" no longer exists. ("null" is a placeholder.)
5. Final state.  "outer_let" is still there, it was _declared_ in the global scope.  "inner_let" is no longer there, it was _declared_ in the block scope and was not _hoisted_.


___

## helpful links

[hoisting - snippet study](https://github.com/elewa-academy/hoisting)

[block scope - snippet study](https://github.com/elewa-academy/block-scope-let-vs-var#index)

Creation vs Execution phases:
* _Creation phase_ is what happens before the first line is executed.  Mostly just hoisting. You can see what happened in the creation phase, it's what PythonTutor displays before you click the __forward__ button for the first time.
* _Execution phase_ is everything that happens after the creation phase.

temporal dead zone:
* only applies to "let" variables declared in blocks
* [why?](http://2ality.com/2015/10/why-tdz.html)
* [performance issues with let](https://medium.com/@sbakkila/javascript-es-6-let-and-the-dreaded-temporal-dead-zone-85b89314d168)



___
___
### <a href="http://elewa.education/blog" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/34921062-506450ae-f97d-11e7-875f-6feeb26ad72d.png" width="100" height="40"/></a>
