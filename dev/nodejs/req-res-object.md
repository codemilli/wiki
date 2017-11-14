<!-- TITLE: Req Res Object -->
<!-- SUBTITLE: A quick summary of Req Res Object -->

# Nodejs Express Request & Response object data

What is Req & Res?

Req -> Http (https) Request Object.
- You can get the request query, params, body, headers and cookies from it.
- You can overwrite any value or add anything there.
- However, overwriting headers or cookies will not affect the output back to the browser. 


Res -> Http (https) Response Object. 
- The response back to the client browser.
- You can put new cookies value and that will write to the client browser (under cross domain rules)
- Once you res.send() or res.redirect() or res.render(), you cann do it again, otherwise, there will be uncaught error. 

For convenient, sometimes I just put values into the req or res objects and pass along to different functions.  That's handy, but in the expense of speed.  Because it may trigger re-creation of the JSON hidden class.  

Also, you cannot JSON.stringify req or res objects beacuse of the deeply nested recursive structure.

So, how's req and res look like?  By default, it looks like that:

```js
req = {
    _startTime     :    Date, 
    app            :    function(req,res){},
    body           :    {},
    client         :    Socket,
    complete       :    Boolean,
    connection     :    Socket,
    cookies        :     {},
    files          :     {},
    headers        :    {},
    httpVersion    :    String,
    httpVersionMajor    :    Number,
    httpVersionMinor    :     Number,
    method         :    String,  // e.g. GET POST PUT DELETE
    next           :    function next(err){},
    originalUrl    :    String,     /* e.g. /erer?param1=23¶m2=45 */
    params         :    [],
    query          :    {},
    readable       :    Boolean,
    res            :    ServerResponse,
    route          :    Route,
    signedCookies  :    {},
    socket         :    Socket,
    url            :    String /*e.g. /erer?param1=23¶m2=45 */
}
```



```js
res = {
    app            :    function(req, res) {},
    chunkedEncoding:    Boolean,
    connection     :     Socket,
    finished       :    Boolean,
    output         :    [],
    outputEncodings:    [],
    req            :    IncomingMessage,
    sendDate       :    Boolean,
    shouldkeepAlive    : Boolean,
    socket         :     Socket,
    useChunkedEncdoingByDefault    :    Boolean,
    viewCallbacks  :    [],
    writable       :     Boolean
}
```

from http://www.murvinlai.com/req-and-res-in-nodejs.html
