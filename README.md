
To serve `python3 -m http.server`

Minikanren examples <https://io.livecode.ch/learn/webyrd/webmk>

Microkanren needs a couple changes.. Change the usage of `assp` to

```
(define (walk u s)
  (let ((pr (and (var? u) (assoc u s var=?))))
    (if pr (walk (cdr pr) s) u)))
```

And delete the tests in miniKanren-wrappers.scm


