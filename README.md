Lyve JavaScript
===============

JavaScript Style Guide




## Table of Contents

 * [Whitespace](#whitespace)
 * [Naming](#naming)
 * [Syntax](#syntax)
 * [Conditional Evaluation](#cond)




------------------------------------------------




1. <a name="whitespace">Whitespace</a>
    - Never mix spaces and tabs.
    - Use soft indents (spaces).
        + Set your editor's indent size to four characters.
	- No trailing whitespace.
	- Use a newline at the end of a file.


2. <a name="naming">Naming</a>
    - Use camelcase.
        + Use lowerCamelCase for variables, properties, function names.
        + Use UpperCamelCase for module names.
    - Use uppercase for constants.


3. <a name="syntax">Syntax</a>
    - End all statements with a semicolon.
    - Use single quotation marks.
        

    A. Declarations

    ```javascript

    var foo = 'foo';

    var foo = 'foo',
        bar = 'bar';

    var
        foo = 'foo',
        bar = 'bar',
        baz = 'baz'
    ;

    var array = [
        // elements
    ];
    
    var object = {
        // properties
    };
    ```


    B. Conditionals & Loops

    ```javascript

    if (condition)
        // statement

    if (condition) {
        // statements
    }

    if (condition) {
        // statements
    }
    else {
        // statements
    }

    switch (expression) {
        case value:
            // statements
            break;
        default:
            // statements
            break;
    }

    for (var i = 0; i < 100; i++) {
        // statements
    }

    for (var foo in baz) {
        // statements
    }

    while (condition) {
        // statements
    }
    ```


    C. Function Statements & Callbacks

    ```javascript

    function foo (params) {
    	// statements
    }

    function foo (params) {
      return // statement or expression
    }
    
    function foo (options, callback) {
        // statements        

        if (error)
            return callback(error); 
        callback(null, response);
    }

    foo(options, function fooCallback (error, response) {
        if (error)
            // handle error
        // statements
    });
    ```


    D. Promises

    ```javascript

    function foo () {
        return P()
        .then(function () {
            // statements        
        }, function (error) {
            // statements
        });
    }

    function foo () {
        return P()
        .then(function () {
            // statements
        })
        .fail(function (error) {
            // statements
        });
    }

    function foo () {
        var deferred = P.defer();

        asyncFunc(function (error, response) {
            if (error)
                return defferred.reject(new Error(error));

            deferred.resolve(response);
        });

        return deferred.promise;
    }

    // usage
    foo()
    .then(function () {
        // statements
    })
    .done(function (error, response) {
        if (error)
            // handle error
        // statements
    })
    ```


    E. Module Declarations

    ```javascript

    function Foo (options) {
        if (!(this instanceof Foo))
            return new Foo(options);

        this.options = options;

        return this;
    }

    Foo.prototype.bar = function bar () {
        // statements
    }

    var foo = Foo(options);

    var foo = new Foo(options);
    ```




4. <a name="cond">Conditional Evaluation</a>

    ```javascript

    // truthiness
    if ( !!array.length ) ...

    if ( !!string ) ...

    // falsiness
    if ( !array.length ) ...

    if ( !string ) ...


    // equality
    // Prefer `===` over `==` (unless the case requires loose type evaluation)

    // === does not coerce type, which means that:

    "1" === 1;
    // false

    // == does coerce type, which means that:

    "1" == 1;
    // true


    // Reference.
    
    // Boolean
    true, false

    // Truthy:
    "foo", 1

    // Falsy:
    "", 0, null, undefined, NaN, void 0
    ```
