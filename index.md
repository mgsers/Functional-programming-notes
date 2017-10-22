## 函数式编程笔记

##### 简称 FP 即 Founctional programming

### 第一章：为什么使用函数式编程如何访问那些超出声明的参数？

1， 置信度
<p>指你通过读代码，不仅是跑代码，就能理解这段代码能干什么事，而不只是停留在它可能是干什么的层面。正是得益于函数式编程已经被证实的原则，能够写出可读性高和可验证的代码，来达到他们想要的目的。</p>

2，交流渠道
<p>代码的主要作用是方便人与人交流，应该更多的关注一下代码的可读性。一旦我们知道这些原则，它们将在代码中被识别和熟悉，这意味着当我们读取一段代码时，我们将花费更少的时间来进行定位。我们的重点将在于如何组建所有已知的“乐高片段”，而不是这些“乐高片段”是什么意思。函数式编程是编写可读代码的最有效工具之一</p>

### 第二章：函数基础

1，什么是函数
<p>在数学中，函数总获取一些输入值，然后给出一个输出值。你能听到过一个叫‘态射’的术语。在某种程度上，函数式编程就是使用在数学意义上的方程作为函数。或许你认为函数就是程序。但是他们之间的区别就是：程序是一个任意功能集合，也就是说他或许有输入值，或许没有，输出也一样。而函数，则是明确接受输入值，并明确<code>return</code>值。所以使用函数式编程，编写的<code>function</code>应该都是接收输入值，并且返回输出值的。</p>

2，函数输入
<p>什么是<code>arguments</code>或者<code>parameters</code></p>
<p><code>arguments</code>是你输入的值，也就是实参。<code>parametres</code>则是函数中的命名变量,用于接收函数的输入值，也就是形参。例子如下</p>

```javascript
  function foo(x, y) { // x， y 是parameters, 用于接收参数值
    // do something
  }
  var a = 3

  foo( a, a * 3) // a 和 a*3 是foo调用的arguments
```
<p>在 js 中，实参的个数没有必要完全符合形参的个数。当 实 > 形时，这些值仍然会原封不动地被传入，可以用比如arguments访问这些值。当 实 < 形时，所有缺少的参数将会被赋予 undefined 变量，意味着你仍然可以在函数作用域中使用它，但值是 undefined。</p>

3，输入计数
<p>一个函数所“期望”的实参个数是取决于已声明的形参个数，即你希望传入多少参数。专业术语又称Arity。

```javascript
function foo(x, y, z) {
  // ...
}
```

foo() 期望三个实参,因为它声明了三个形参。
你可能需要在程序运行时获取函数的 Arity，使用函数的 length 属性即可。

```javascript
function foo(x,y,z) {
    // ..
}

foo.length;                // 3
```

我们又可以用<code>arguments</code>的length值来找出多少传入的参数。

```javascript
function foo(x,y,z) {
    console.log( arguments.length );    // 2
}

foo( 3, 4 );
```

不过还是尽量不要用arguments来访问传入变量。

此外有一种特殊情况，如何访问那些超出声明的参数？不过这种情况并不是编写函数时必须关注的。甚至这种情况是函数式编程所要避免的。

此时，让我们用 ... 操作符声明我们的函数，也被当做 “spread”、“rest” 或者 “gather” 提及。

```javascript
function foo(x,y,z,...args) {
    console.log( x, y, z, args );
}

foo();                    // undefined undefined undefined []
foo( 1, 2, 3 );            // 1 2 3 []
foo( 1, 2, 3, 4 );        // 1 2 3 [ 4 ]
foo( 1, 2, 3, 4, 5 );    // 1 2 3 [ 4, 5 ]
```


</p>