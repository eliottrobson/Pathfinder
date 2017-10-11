# Pathfinder

The static and dynamic analysis tool for reverse debugging

--------------------------------------------------------------------------------

We've all been there. Running our app and everything is working great. Until it isn't. There's a bug in our JavaScript, how can we fix it? The first step is to find out what we know.

- The problem lies in the last 1000 lines of code we wrote, probably.
- Turning it off and on again is unlikely to fix it.
- We know where it breaks.

Only the last point is useful.

Enter **Pathfinder**. This tool is designed to use a hybrid static and dynamic analysis process to provide reverse debugging capabilities.

Static analysis allows me to prune the abstract syntax tree, before instrumentation. Dynamic analysis allows me to collect the data of the instrumented calls. Pathfinder allows you to stop at the broken code and work backwards to find the problem.

# How it works

[Esprima](http://esprima.org/) is a static analysis tool which is used to construct an ast of your code. We perform a run over the code to detect uses of `debugger` (the "trigger"). The second run uses this information to instrument only the functions which lead up to that point. This process of pruning the tree allows us to collect much more detailed results without the concern of observing unnecessary events. Then, we convert the data into something digestible, ready for you to review.

# Meta

This is a research project and there are no guarantees it will be finished, tested or work at all. Yet.
