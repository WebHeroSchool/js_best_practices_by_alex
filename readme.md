#JS Best Practices

**1. Avoid Global Variables - Declare Only Local Ones**

Global variables and functions can be overwritten by other scripts, so better use local variables instead. 

    //Bad practice:
    var result;
    function multiply(x, y) {    
        result = x * y;
        return result;
     }
     
     //Instead:
     function multiply(x, y) {
        var result = x * y;
        return result;
     }
    

**2. Declare variables at the top of the script**
Although thanks to hoisting, JS moves all declarations to the top anyway, it is still a good coding practice to put all declarations at the top of each script or function. 

This will:

* Give cleaner code
* Provide a single place to look for local variables
* Make it easier to avoid unwanted (implied) global variables
* Reduce the possibility of unwanted re-declarations

Example:

    //Declare:
    var studentName, studentSurname, studentDateOfBirth; studentAge;
    //Then use:
    studentName = 'Alex';
    studentSurname = 'Kipelova';
    studentDateOfBirth = 1993;
    studentAge = 2020 - studentDateOfBirth;

**3. Use easy, short and readable variable and function names**

Good variable and function names should be written in English, be easy to understand and tell you what is going on — not more and not less. It makes the code easier to read for humans and easier to debug.

    //Bad practice:
    var nameOfUserIfAgeIsMoreThanLegalDrinkingAge;
    var familiiaPlzovatelia;
    var cfgyhjk;
    //Good practice:
    var userName;
    var legalDrinkingAge;

**4. Stick to a strict coding style**

Although the style does not matter when the browser reads the code, it does matter when people read the same code. It is important not only when working in a team but also when there is a need to come back to your own code some time later or when there is a need to debug the code. Use The WordPress Javascript Coding Standard, and ensure you validate and lint your code.

**5. Ensure your site still works without JavaScript**

This is progressive enhancement (putting emphasis on web content first). JavaScript should be used to decorate the site with additional functionality, and should not be required for the site to be operational. As a result, users who have older browser versions or slow Internet connection will still be able to access the content. 

    //For example, do not add a link with JS code into DOM:
    <a href="#">There's a JavaScript click handler somewhere else...</a>
    <a href="javascript:someJavaScriptFunctionInThisLink()">...</a>

**6. Do not create new objects through new Object() constructor function**

Creating new objects through new Object(), new Array(), etc., constructor functions might create numerous problems. For example, when creating an array, the newly created array length will be measured not from number 0 but from 1, what will lead to numerous problems and errors:

    var a = new Array(1,2,3,4,5);
    a.length // returns 5
    
Therefore:

+ Use {} instead of new Object()
+ Use "" instead of new String()
+ Use 0 instead of new Number()
+ Use false instead of new Boolean()
+ Use [] instead of new Array()
+ Use /()/ instead of new RegExp()
+ Use function (){} instead of new Function()

**7. Use === Comparison**

The == comparison operator always converts data type of variables to matching types before comparison. Thus, it can falsly declare that number 5 equals string '5'. The === operator compares both values and type:

    0 == "";        // true
    1 == "1";       // true
    1 == true;      // true
    
****************************************************************************************************************************************

    0 === "";       // false
    1 === "1";      // false
    1 === true;     // false

**8. Use Parameter Defaults**

If a function is called with a missing argument, the value of the missing argument is set to undefined. Undefined values can break your code. It is a good habit to assign default values to arguments.

    //Example:
        function myFunction(x, y) {
            if (y === undefined) {
                y = 0;
            }
        }

**9. End Your Switches with Defaults**

Always end your switch statements with a default. It ensures that the condition really covers all possible cases, and it reduces chances of errors.

    //Example:
        switch (new Date().getDay()) {
    case 0:
        day = "Sunday";
        break;
    case 1:
        day = "Monday";
        break;
    case 2:
        day = "Tuesday";
        break;
    default:
        day = "Unknown";
    };
    
**10. Use shortcut notation when it makes sense**

Shortcut notations make the code easier to read, shorther, and cleaner.

    //Instead of this:
    var number;
    if(x > 100){
        number = 1;
    } else {
        number = -1;
    //Write this:
    var number = (x > 100) ? 1 : -1;

    
