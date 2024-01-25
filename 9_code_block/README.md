# README

关于好看的代码块，建议直接使用minted，而如果我们不喜欢配环境的话，可以直接在overleaf上直接操作就可以了，非常方便。

这里是复制overleaf上面的tex代码，由于本地没有环境可以直接运行，所以直接复制过来了。

```latex
\documentclass{article}
\usepackage{minted}
\begin{document}
\section{Python Code Block}
\begin{minted}{python}
import numpy as np
    
def incmatrix(genl1,genl2):
    m = len(genl1)
    n = len(genl2)
    M = None #to become the incidence matrix
    VT = np.zeros((n*m,1), int)  #dummy variable
    
    #compute the bitwise xor matrix
    M1 = bitxormatrix(genl1)
    M2 = np.triu(bitxormatrix(genl2),1) 

    for i in range(m-1):
        for j in range(i+1, m):
            [r,c] = np.where(M2 == M1[i,j])
            for k in range(len(r)):
                VT[(i)*n + r[k]] = 1;
                VT[(i)*n + c[k]] = 1;
                VT[(j)*n + r[k]] = 1;
                VT[(j)*n + c[k]] = 1;
                
                if M is None:
                    M = np.copy(VT)
                else:
                    M = np.concatenate((M, VT), 1)
                
                VT = np.zeros((n*m,1), int)
    
    return M
\end{minted}
\section{Markdown Block}
\begin{minted}{markdown}
# My Markdown Document

This is a *Markdown* document example.

## Lists

- Item 1
- Item 2
- Item 3

## Code Block

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
```

\end{minted}
\end{document}
```

效果查看`minted_demo.pdf`