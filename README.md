# Scheme listings in LaTeX

 Scheme syntax highlighting for the LaTeX listings package

## Example

LaTeX code:

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

As an alternative to `lstlisting`, Scheme code can also be included from an external file:

    \lstinputlisting{ycombinator.ss}

Rendered:

![Rendered example](http://github.com/stuhlmueller/scheme-listings/raw/master/example.png)

## Installation

The `scheme-listings` directory must be on your TeX search path.

To use LaTeX from the Bash shell, add this to your shell config file (e.g. `.bashrc`):

    export TEXINPUTS=/path/to/scheme-listings/:$TEXINPUTS
    
For Emacs, use:

    (setenv "TEXINPUTS" (concat "/path/to/scheme-listings/:" (getenv "TEXINPUTS")))
