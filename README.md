# security-node
Secure node.js/express template

##Headers
* It’s best practice to throw a node behind a proxy like nginx or apache in order to modify the headers especially since running the node.js app over port 80:443 requires sudo, and a node.js app can own a system if poorly coded.
* If not behind a proxy there’s an npm package called helmut [https://github.com/helmetjs/helmet]  this package lets you modify the headers, force https, remove the poweredby messages, etc.
 
##Cookies
 If using cookies there are two packages that are useful: 
* cookie-session [https://github.com/expressjs/cookie-session] lets you set the scoping of the cookies along with the secure flags. 
* cookie-parser[https://github.com/expressjs/cookie-parser] lets you have signed cookies.
 
##CSRF
* csurf [https://github.com/expressjs/csurf] this package helps protect against CSRF, it requires the cookie-parser package to be used in order to work with cookies.
 
##Command Injection
* You should never use child_process.exec as it basically executes as a bash command, use child_process.execFile instead.

##Input Validation
* This is a mostly a manual task, but there’s another package called express-validator [https://github.com/ctavan/express-validator], you can use this to do simple validation on input, like is a string, is not empty, etc.
 
##Brute Force Attacks
* There are packages available for rate limiting, like ratelimiter [https://github.com/tj/node-ratelimiter] but it requires redis.
 
##SQL Injection
* It depends on the database being used, but almost all the databases have some kind of npm package that includes parameterized queries
 
##Linting
* There's a bunch of tools used to enforce a specific style and detect potential errors, jshint [http://jshint.com/about/] is a popular one also ES Lint [http://eslint.org/]


##Password Hashing
* It's bad practice to keep passwords in plaintext in side configuration files. The following is an article for node and other languages on how to use bcrypt [https://www.praetorian.com/blog/secure-password-storage-in-go-python-ruby-java-haskell-and-nodejs]

##Package Scanning
nodejs is basically just packages thrown together, there are tools used to scan your packages and make sure they are up to date and do not contain known vulnerabilities.
* nsp [https://github.com/nodesecurity/nsp​]
* retire.js [http://retirejs.github.io/retire.js/]  
