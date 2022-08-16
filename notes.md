# Syntax

~~~~~
keyword name (param: paramtype) : type := expression .
~~~~~

bar introduces constructor alternatives, with rocket for result in definition, but nothing in inductive (introduction)

`Compute` prints to the console an expression

The expression must be of the right type.  What that type is an _assertion_ then the expression is a proof object.  When you are sitting in the expression spot of such a statement, you will be shown interesting things in the proof view.

`Notation` doesn't have a type, just an expr.

Ifs work on any two-valued type!

`match expr with options end`

You need `Proof` and `Qed` so the language knows when to stop buiding the proof. todo: do better on this!

`Check` will either print a type (if you didn't give one) or check the type (if you did).

# Current Understanding

A Coq file is a series of commands.  Some of those commands introduce a _proof obligation_ which you can then dispatch using _tactics_.  Tactics are a whole different world to terms or types, they operate on the one-and-only live proof obligation.  That obligation might have many goals, or  just one.  You can only move on when a proof obligation is dispatched.  Everytime you dispatch the pending proof obligation, the thing that created it is added to your list of assumptions/proved theorems.

# Commands so far
  * Inductive : introduce a new type and its constructors.  The type of a type is `Type`
  * Definition: introduce a new named thing with a type and a term that it represents.
  * Fixpoint: introduce a recursive definition.
  * Notation: introduce a typeless/string form of a term that we can use later in place of it.
  * Check: print type or check type
  * Compute: evaluate term as far as you can
  * Module
  * Admitted: dispatch the current proof obligation trivially.
  * Abort: dispatches proof obligation in the negative, property not added to assumptions.
  * Axiom/Conjecture/Paramter: define something taken as true - no proof necessary.

Some commands create the need for a proof and move the system into proof mode, these are
  * Example/Defintion with no term: introduce a term with a type that is a proposition - you will need to prove that propisition 

# Tactics
  * simpl: compute as far as you can
  * reflexivity: dispatch any propositions with the same thing on each side
  * intros <name>: move a forall or an implication at the head of a goal to the assumptions.
  * rewrite -> <name>: anywhere you see the left-hand-side of the assumption/proven theorem <name>, replace it with right-hand side.
  * rewrite <- <name>: anywhere you see the right-hand-side of the assumption/proven theorem <name>, replace it with left-hand side.
  * destruct <name>: turn one goal with n into multiple goals with each possible way to construct n.
  * -/+/*/--/++/**/{}: move to next subgoal (no dot after!!!)