# RishikaNew
just a new repository
#lang racket
 (define ring-area
   (lambda (o i)
     (* pi (- (* o o) (* i i)))))

(define list-length
  (lambda (x)
    (if (empty? x)
        0
        (+ 1 (list-length(rest x))))))
(define list-with-length-at-least-two?
   (lambda (x)
     (>= (list-length x) 2)
     "#t"
     "#f"
     ))
 (define remove-second
   (lambda (x)
      (<= (list-length x) 2)
     error"this is random"
     (cons (first x) (rest (rest x)))))
(define gcd
  (lambda(a b)
     (if (> b 0)
       (gcd b (modulo a b))
    a)))
