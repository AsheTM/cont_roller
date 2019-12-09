Cont Roller
=============

A library for ExpressJS to simplify controller function.



Installation
------------

To use with node:

```bash
$ npm install --save cont_roller
```



Usage
-----------------

Then in server side with ExpressJS:

```javascript
...
const $ = require('cont_roller');
...
const cont = $((req, options) => {
    // Do something
    req;        // Request
    options;    // Options
    options.__headers__ =   { /* Some headers*/ };
    options.__cookies__ =   [
        {
            name:       'Cookie name', 
            value:      'Cookie value', 
            options:    {
                // Same options as cookie method in res.cookie
            }
        }
    ];
    options.__contentType__ ='json'; // Only 'json' value supported
    return {/* Return datas like res.send(...) or res.json(...) */
        data: ['...']
    };
})._200().if((req, data) => {
    let check = true;
    // Do some check
    req;            // Request
    data;           // Data returned from the callback of $; 
                    // Its value in this example { data: ['...'] }
    return check;   // Return a Boolean value
})._500({/* Data to send when an error is catched or 
            when the callback of if method return false */
    error:  'Sample Error Message'
});
...
router.get('/test', cont);
...
```
