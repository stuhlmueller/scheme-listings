# Scheme-listings

Example:

    \documentclass{article}
    \usepackage{listings}
    \usepackage{color}
    \usepackage{textcomp}
    
    \lstset{
      language=Scheme
    }
    
    \begin{document}
    
    \title{A Scheme Listing in \LaTeX}
    \date{}
    \maketitle
    
    \begin{lstlisting}
    ;; The Y combinator
    (define Y
      (lambda (f)
        ((lambda (x) (f (lambda arg (apply (x x) arg))))
         (lambda (x) (f (lambda arg (apply (x x) arg)))))))
    
    ;; Factorial function using the Y combinator
    (define fact
      (Y (lambda (f)
           (lambda (n)
             (if (<= n 0)
                 1
                 (* n (f (- n 1))))))))     
    \end{lstlisting}
    
    \end{document}
