# javascript-interview-asking-output-questions


1. ###  Find out output

    #### 1 Example:

        ```
            var a = 5; // Block scope
            let b = 15; 
            const c = 20
            function print() {
                var a = 10;
                let b = 30;
                const c = 40;

                console.log(a); // 10 take last value
                console.log(b) // 30 inside block
                console.log(c) // 40 inside block
            }
            print();
            console.log("a ",a); // 10 take last value
            console.log("b ",b) // 15 outside block
            console.log("c ",c) // 20 outside block

        ```
    #### 2. Example: 

        ```
            console.log( 2 === 2 ); // true
            console.log( 2 === "2"); // false
            console.log( 2 == 2 ); // true
            console.log( "2" == 2 ); // true
            console.log( "2" == "3" ); // false
            console.log( 2 === 2 ); // true
            console.log( "1" === true); // false

        ```

    #### 3. Example:  

        ```
            console.log(1 +  "2" + "2"); // "122"
            console.log(1 +  +"2" + "2"); // "32"
            console.log(1 +  -"1" + "2"); // "02"
            console.log(+"1" +  "1" + "2"); // "112"
            console.log( "A" - "B" + "2"); // "NaN2"
            console.log( "A" - "B" + 2); // "NaN2"
            console.log(0.1 + 0.2); // 0.30000000000000004
            console.log(0.1 + 0.2 == 0.3); // false

        ```
    #### 4. Example: Hosting program to display value

        ```
            a = 5;
            console.log(a);
            var a; // 5
            
        ```

    #### 5. Example: 

        ```
            console.log(typeof "John Doe"); // Returns "string"
            console.log(typeof 3.14); // Returns "number"
            console.log(typeof true); // Returns "boolean"
            console.log(typeof 234567890123456789012345678901234567890n );// Returns bigint
            console.log(typeof undefined); // Returns "undefined"
            console.log(typeof null); // Returns "object" (kind of a bug in JavaScript)
            console.log(typeof Symbol('symbol')); // Returns Symbol

        ```

    #### 6. Example:

        ```
            (function(){
                var a = b = 3;
            })();

            console.log("a defined? " + (typeof a !== 'undefined')); // "a defined? false"
            console.log("b defined? " + (typeof b !== 'undefined')); // "b defined? true"

        ```
    #### 7. Example:

        ```
            var bar = null;
            console.log(typeof bar === "object");  // logs true!

            console.log((bar !== null) && (typeof bar === "object"));  // logs false

            console.log((bar !== null) && ((typeof bar === "object") || (typeof bar === "function"))); // false

            console.log((bar !== null) && (bar.constructor === Object)); // false

            console.log((bar !== null) && (typeof bar === "object") && (! $.isArray(bar)));  // false

            console.log(Array.isArray(bar));  // false

        ```

    #### 8. Example:

        ```
            var myObject = {
                foo: "bar",
                func: function() {
                    var self = this;
                    console.log("outer func:  this.foo = " + this.foo); //"outer func:  this.foo = bar"

                    console.log("outer func:  self.foo = " + self.foo); //"outer func:  self.foo = bar"

                    (function() {
                        console.log("inner func:  this.foo = " + this.foo); //"inner func:  this.foo = undefined"

                        console.log("inner func:  self.foo = " + self.foo); //"inner func:  self.foo = bar"

                    }());
                }
            };
            myObject.func();
            
        ```

    #### 9. Example:

        ```
            function foo1()
            {
                return {
                    bar: "hello"
                };
            }

            function foo2()
            {
                return
                {
                    bar: "hello"
                };
            }
            console.log(foo1()); //{  bar: "hello" }
            console.log(foo2()); //undefined

        ```

    #### 10. Example:

        ```
            var arr1 = "Ramesh".split('');
            var arr2 = arr1.reverse();
            var arr3 = "Ramesha".split('');
            arr2.push(arr3);
            console.log("array 1: length=" + arr1.length + " last=" + arr1.slice(-1)); 
            // "array 1: length=7 last=R,a,m,e,s,h,a"

            console.log("array 2: length=" + arr2.length + " last=" + arr2.slice(-1)); 
            // "array 2: length=7 last=R,a,m,e,s,h,a"

        ```

    #### 11. Example:

    ```
        function isPalindrome(str) {
            str = str.replace(/\W/g, '').toLowerCase();
            return (str == str.split('').reverse().join(''));
        }

        console.log(isPalindrome("level"));                   // logs 'true'
        console.log(isPalindrome("levels"));                  // logs 'false'
        console.log(isPalindrome("A car, a man, a maraca"));  // logs 'true'
        
    ```




console.log("============================");




console.log("============================");

function areTheNumbersAlmostEqual(num1, num2) {
	return Math.abs( num1 - num2 ) < Number.EPSILON;
}
console.log(areTheNumbersAlmostEqual(0.1 + 0.2, 0.3));

console.log("============================");
(function() {
    console.log(1); 
    setTimeout(function(){console.log(2)}, 1000); 
    setTimeout(function(){console.log(3)}, 0); 
    console.log(4);
})();

console.log("============================");

console.log(sum(2,3));   // Outputs 5
console.log(sum(2)(3));  // Outputs 5

///METHOD 1
function sum(x) {
  if (arguments.length == 2) {
    return arguments[0] + arguments[1];
  } else {
    return function(y) { return x + y; };
  }
}

///METHOD 2

function sum(x, y) {
  if (y !== undefined) {
    return x + y;
  } else {
    return function(y) { return x + y; };
  }
}
console.log("============================");

for (var i = 0; i < 5; i++) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  btn.addEventListener('click', (function(i) {
    return function() { console.log(i); };
  })(i));
  document.body.appendChild(btn);
}

['a', 'b', 'c', 'd', 'e'].forEach(function (value, i) {
  var btn = document.createElement('button');
  btn.appendChild(document.createTextNode('Button ' + i));
  btn.addEventListener('click', function() { console.log(i); });
  document.body.appendChild(btn);
});
console.log("============================");





```
let arr3 = [1,4,[3,5,7,2],[[5,8,3]],[5,9,1],8];
console.log(arr3.flat(2));


const arr = [...new Set(arr3.flat(2))]

const soretedarr = arr.sort((a,b) => a-b);
console.log(soretedarr);

```

2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###
2. ###