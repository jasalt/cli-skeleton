# Phel Cli Skeleton

Example code for https://github.com/phel-lang/phel-lang/issues/784

Defining the macro inline in REPL works in as expected:

```
$ vendor/bin/phel repl

phel:1> (defmacro time
  "Evaluates expr and prints the time it took.  Returns the value of expr."
  [expr]
  (let [start (gensym)
        ret (gensym)]
    `(let [,start (php/microtime true)
           ,ret ,expr]
       (println "Elapsed time:" (* 1000 (- (php/microtime true) ,start)) "msecs")
       ,ret)))
1
phel:10> (time (do (php/sleep 1) :well-slept))
Elapsed time: 1000.0691413879 msecs
:well-slept
phel:11> exit
```

However when running as a script with `vendor/bin/phel run src/main.phel` (or requiring it REPL from a ns) leads to unexpected result:

```
$ vendor/bin/phel run src/main.phel
vendor/bin/phel run src/main.phel
(let [__phel_763 (microtime true) __phel_764 :well-slept] (println Elapsed time: (* 1000 (- (microtime true) __phel_763)) msecs) __phel_764)
$
```
