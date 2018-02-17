# Smart Augmenting Graphs
A tex package to draw automatically tex graphs.

This package requires the packages **fp**, **xparse**, **xstring** and **tikz** (in particular tikz/calc). If you don't have them you can proceed by installing them by running:

```sh
sudo tlmgr instal fp xparse xstring tikz
```

I'm currently looking into publishing this package on ctan, until then you'll have to download it and include in locally with the usual:

```latex
\usepackage{adigraph}
```

Then, suppose you want to create a graph as the following:

![alt text][graph]

We start by defining a new graph:

```latex
    \NewAdigraph{myAdigraph}{
        s,0,0,b,red;
        1,2,2;
        3,2,-2;
        2,6,2;
        4,6,-2;
        t,8,0,e,blue;
    }{
        s,3,25;
        s,1,25;
        3,1,5;
        3,4,20;
        4,2,5;
        2,3,15,0,near start;
        4,1,5,0,near start;
        1,2,35;
        2,t,20;
        4,t,30;
    }
```

In the first argument we are defining the *nodes*, while in the second one we are defining the *edges*. The name of this particular graph will be *myAdigraph*.

We now want to draw this graph. We proceed as follows:

```latex
\begin{figure}
    \center
    \myAdigraph{}
    \caption{My Personal Graph}
\end{figure}
```

Suppose now we want to show the steps for calculating the maximum flow of the graph. We just add the edited edges inside the now empty argument of the *\myAdigraph*:

```latex
\begin{figure}
    \center
    \myAdigraph{
        s,3,5,20,1;
        3,4,0,20,1;
        4,t,20,10,1;
    }
    \caption{Sending 10 units over $s,3,4,t$}
\end{figure}

\begin{figure}
    \center
    \myAdigraph{
        s,3,5,20;
        3,4,0,20;
        s,1,20,5,1;
        4,1,5,0,red,blue,near start;
        4,t,15,15,1;
    }
    \caption{Sending 5 units over $s,1,4,t$}
\end{figure}

\begin{figure}
    \center
    \myAdigraph{
        s,3,5,20;
        3,4,0,20;
        s,1,15,10,1;
        1,2,25,10,1;
        4,2,5,0,1;
        4,t,10,20,1;
    }
    \caption{Sending 5 units over $s,1,2,4,t$}
\end{figure}

\begin{figure}
    \center
    \myAdigraph{
        s,3,5,20;
        3,4,0,20;
        s,1,5,20,1;
        1,2,15,20,1;
        4,2,5,0;
        2,t,0,20,1;
        4,t,10,20;
    }
    \caption{Sending 10 units over $s,1,2,t$}
\end{figure}

\begin{figure}
    \center
    \myAdigraph[
        3,4;
        2,t;
    ]{
        s,3,5,20;
        3,4,0,20;
        s,1,5,20,1;
        1,2,15,20,1;
        4,2,5,0;
        2,t,0,20,1;
        4,t,10,20;
    }
    \caption{Showing minimum cut}
\end{figure}
```

The working example in latex is found in the file *adigraph_library_example.tex*.

Have a nice day!
**Luca Cappelletti**

[graph]: https://github.com/LucaCappelletti94/smart_augmenting_graphs/blob/master/img_examples/example_1.jpg?raw=true "Example_1"