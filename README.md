To serve `python3 -m http.server`

Minikanren examples <https://io.livecode.ch/learn/webyrd/webmk>

Microkanren Implementation <https://github.com/jasonhemann/microKanren>
Minikanren Implementation <https://github.com/webyrd/miniKanren-with-symbolic-constraints>
Faster-minikanren seems hopeless.

Microkanren needs a couple changes.. Change the usage of `assp` to

```
(define (walk u s)
  (let ((pr (and (var? u) (assoc u s var=?))))
    (if pr (walk (cdr pr) s) u)))
```

And deleted the tests in miniKanren-wrappers.scm

Errors:

In microkanren basic examples work and then:
```
lips.min.js:87 syntax: internal error, ellipis not transformed in macro: 
(() ((_ (g0 g ...) ...) (disj+ (conj+ g0 g ...) ...))) in macro: 
(() ((_ n (x ...) g0 g ...) (map reify-1st (take n (call/goal (fresh (x ...) g0 g ...))))))
```

In minikanren, even basic queries do not work.

```
Invalid Syntax (#:lambdag+++ (#:c #:: #:B #:E #:S #:D #:Y #:N #:T) (#:inc (#:let ((q (#:var (#:quote q)))) (#:let ((#:B (#:append (#:quasiquote ((#:unquote q))) #:B))) (#:bind* ((== q 1) (#:quasiquote ((#:unquote #:B) (#:unquote #:E) (#:unquote #:S) (#:unquote #:D) (#:unquote #:Y) (#:unquote #:N) (#:unquote #:T)))) (#:lambdag+++ (#:final-c) (#:let ((#:z ((#:reify q) #:final-c))) (#:choice #:z #:empty-f)))))))) in macro: (() ((_ (x ...) g0 g ...) (lambdag+++ (c : B E S D Y N T) (inc (let ((x (var (quote x))) ...) (let ((B (append (quasiquote ((unquote x) ...)) B))) (bind* (g0 (quasiquote ((unquote B) (unquote E) (unquote S) (unquote D) (unquote Y) (unquote N) (unquote T)))) g ...))))))) in macro: (() ((_ e (() e0) ((f^) e1) ((c^) e2) ((c f) e3)) (let ((c-inf e)) (cond ((not c-inf) e0) ((procedure? c-inf) (let ((f^ c-inf)) e1)) ((not (and (pair? c-inf) (procedure? (cdr c-inf)))) (let ((c^ c-inf)) e2)) (else (let ((c (car c-inf)) (f (cdr c-inf))) e3)))))) in macro: (() ((_ n (q) g0 g ...) (take n (lambdaf+++ () ((fresh (q) g0 g ... (lambdag+++ (final-c) (let ((z ((reify q) final-c))) (choice z empty-f)))) empty-c)))) ((_ n (q0 q1 q ...) g0 g ...) (run n (x) (fresh (q0 q1 q ...) g0 g ... (== (quasiquote ((unquote q0) (unquote q1) (unquote q) ...)) x)))))
```




