# javascript answers 

1. explain event delegation. 
    - its a way you can add an event listener once for multiple elements with support for adding extra children later on. 
- Explain how this works in JavaScript.
```Html
<!-- example -->
<ul id='myList'>
<li>Apple</li>
<li>Orange</li>
<li>Tomato</li>
</ul>

<script>
const myList = document.getElementByid('myList');
myList.addEventListener('click', function (e) {
    // e can be inspect when e gets clicked on
    console.log(e)
    const target = e.target
    // this bases if the target matches li
    if(target.matches("li")){
        // do something
        target.style.backgroundColor = "red"
        // if go to browser and click on anyone of the list the background will be red.
    }
})
// support for adding extra children
// if adding extra children to the list itself the event delegation will still work
const  newLi = document.createElement('li')
newLi.textContent = "decode"
myList.appendChild(newLi)
// save it and when refreshing the browser will see decode be added to the list
</script>
```
- more reference [event delegation](https://javascript.info/event-delegation)

2. Explain how prototypal inheritance works.
- "In programming, we often want to take something and extend it.

For instance, we have a user object with its properties and methods, and want to make admin and guest as slightly modified variants of it. We’d like to reuse what we have in user, not copy/reimplement its methods, just build a new object on top of it." (will refactor when I can better put in my own words)
- example:
```Js
function Bear(type){
    this.type = type
}
Bear.prototype.growl = function(){
    console.log('The' + this.type + 'bear says grrr')
}
 function Grizzly(){
     Bear.call(this, 'grizzly')
 }
 Grizzly.prototype = Object.create(Bear.prototype)
 Grizzly.prototype.growl = function(){
     consooe.log('on the Grizzly.prototype')
 }

let grizzly = new Bear('grizzly')
let grizzly = new Grizzly()
let polar = new Bear('polar')

grizzly.growl = function() {console.log('overide')}
console.log(grizzly.growl())
```
- in es6 or equa script 6 they added more for classes or keywords and extends keywords in doing so, gives you more of a class inheritance feel such ass java c++
- reference [protoypal inheritance](https://javascript.info/prototype-inheritance#:~:text=When%20we%20want%20to%20read,techniques%20are%20based%20on%20it.)

![alt text](image.jpg)

3. What's the difference between a variable that is: null, undefined or undeclared?
    - `undefined` is a variable that has been declared but no value exists and is a type of itself ‘undefined’.
    - `null` is a value of a variable and is a type of object." Also, heard that null and undefined are kind of the same. 
    - `undeclared` variables is a variable that has been declared without ‘var’ keyword.
    ```Js 
    testVar = ‘hello world’;
    //as opposed to 
    let testVar = ‘hello world’;
    //When former code is executed, undeclared variables are created as global variable and they are configurable (ex. can be deleted).

    ```
- How would you go about checking for any of these states?
    - can use ‘console.log();’ and ‘type of’ to check if a variable is undefined or null.
- reference [null, undefined, undeclared](https://medium.com/@rlynjb/js-interview-question-what-s-the-difference-between-a-variable-that-is-null-undefined-or-bf7233cef1c2)

4. What is a closure, and how/why would you use one?
    - "A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time."
    

- reference (closure)[https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36#:~:text=In%20other%20words%2C%20a%20closure,another%20function%20and%20expose%20it.]