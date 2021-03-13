![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/no1cx6yq1701r252j88c.png)

## The problem
JavaScript has a limitation it only allows precision of about 16 digits for the number format.

Minimum & maximum value that a number can go to without losing precision is `-2^53<= x <=2^53`, _where 2^53 = 9007199254740992_.

If we go beyond this limit then we'll lose precision.
```
console.log(1000000000000011112); // => 1000000000000011100
```

This impreciseness affect arithmetic operations as well.
```
console.log(10000000000000001+1) // => 10000000000000000
console.log(10000000000000002-1) // => 10000000000000000
console.log(10000000000000002*3) // => 30000000000000010
console.log(10000000000000001==10000000000000000) // => true
```
It is difficult to get answers from arithmetic operations of large integers.

## The Solution
To solve this impreciseness, We have created a library called **sateek.js**

The word _sateek_ means exact or precise in hindi language.

To use this library, Encode your large integer in a string format & call the functions provided by sateek.js

```
sateek.add("10000000000000001", "1"); // => 10000000000000002
sateek.subtract("10000000000000002", "1"); // => 10000000000000001
sateek.multiply("10000000000000002", "3"); // => 30000000000000006
```
It returns output in string format.

## Installation
Sateek.js is available on [github](https://github.com/Kalpitrathore/sateek) & [npm](https://www.npmjs.com/package/sateek) or you can simply add it's [CDN](https://cdn.skypack.dev/sateek) to your JavaScript file.

##### Node.js
1) To use this library, You need to install [Node.js](https://nodejs.org) & [npm](https://www.npmjs.com/get-npm).
2) Now run the following command in your project directory.
```
npm install --save sateek
```
3) Import sateek.js library in your project.
```
var sateek = require('sateek')();
```

##### JavaScript
1) Create a HTML file & write some code in it.
```
<html>
    <body>

    </body>    
    <script type="module">
        import sateekModule from 'https://cdn.skypack.dev/sateek';
        const sateek = sateekModule();
        console.log(sateek.add("10000000000000002", "3"));
    </script>
</html>
```

## Usage
Sateek.js offers 5 functions.
1) add(n1,n2);
2) subtract(n1,n2);
3) divide(n1,n2);
4) compare(n1,n2);

Where _n1_ & _n2_ are two numbers encoded in string format.

##### Add
```
sateek.add("10000000000000001", "1"); // => 10000000000000002
```

##### Subtract
```
sateek.subtract("10000000000000002", "1"); // => 10000000000000001
```

##### Multiply
```
sateek.multiply("10000000000000002", "3"); // => 30000000000000006
```

##### Divide
```
sateek.divide("20000000000000022", "2"); // => 10000000000000011
```

##### Compare
```
sateek.compare("10000000000000001", "10000000000000000"); // => 1

sateek.compare("10000000000000000", "10000000000000001"); // => -1

sateek.compare("10000000000000001", "10000000000000001"); // => 0
```
if n1>n2, it returns 1
if n1<n2, it returns -1
if n1==n2, it returns 0

## The Conclusion
Every library has it's own advantages & limitations. Here are some limitations of sateek.js library.

1) Sateek.js focuses more on precision as compare to efficiency.
2) It only work with integers.
3) Division operation only work when dividend is greater than divisor.
4) Division operation only returns quotient.

We have tested this library with large test cases, Still if you found any issue feel free to report it on github/npm or mail me at kalpitrathore@gmail.com.

Thank you for reading.

For daily updates follow me on [twitter](https://twitter.com/kalpitrathore).
