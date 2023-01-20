# GUILE-IRC

An irc library for [GNU guile](http://www.gnu.org/software/guile/).

## Usage

1. Add the modules to your load-path and load.
```scheme
(add-to-load-path "path/to/lib/..")
(use-modules (irc irc) 
             (irc handlers) 
             ((irc message)
              #:renamer (symbol-prefix-proc 'msg:)))
```

2. Create an irc object.
```scheme
(define irc (make-irc #:nick "bot" #:server "localhost" #:port 6697 #:ssl #t))
```
   
3. Install some message handlers.
```scheme
(install-ping-handler! irc)
(install-hello-handler! irc #:prefix "," #:command "hi" #:reply "hello master!")
(install-printer! irc)
```
   
4. Connect to the server and register.
```scheme
(do-connect irc)
(do-register irc)
```

5. Join channel "#test".
```scheme
(do-join irc "#test")
```
   
6. Let the `bot' do its job.
```scheme
(do-runloop irc)
```

## API

The API is documented in the Info manual.


## License

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation; either version 2 of the
License, or (at your option) any later version.
