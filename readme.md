Just something to get started

# Compilation Troubles?

In VSCoq, there appears to be no "compile buffer" so we need to do it my hand.  _Don't use `coqc` directly, use `make <target>.vo`.  At the moment I have the plugin looking in `lf` for the `_CoqProject` file, but perhaps I can use a global one?  I am also currently in `lf` when I do all this, which I think is necessary because that is where the makefile is.