# 15-150 Cheatsheet

## Type-Checking and Evaluation
- **Type-checking happens before evaluation!** Only well-typed expressions can be evaluated (into values).

## Built-in Comparison Operators
- Operators: `>`, `<`, `>=`, `<=`
- Operate on: `int`, `string`, `char`, `real`

## Operations and Types
- A tuple of values is itself a value.

## Binding Values
- **Big idea:** Bind values to variable names (either `val` declarations or `fun` declarations).
  - Example: `val x : int -> int = (fn y => y + 1)`
  - Example: `fun x (y : int) : int = y + 1`
- **Note:** Declarations are not expressions. If asked for an expression of some type, do not write a `val` or `fun` declaration.

## Function Application
- **Big Idea:** `e e’ : t2` iff `e : t1 -> t2` and `e’ : t1`

## Totality and Valuability
**Definition (Valuable).** A well-typed expression `e` is *valuable* if there exists a value `v` such that  
`e ⟹ v`. We also say that *e evaluates to a value*.
**Definition (Total).** A well-typed expression `e1 : t1 -> t2`, for types `t1` and `t2`, is *total* if for all values `e2 : t1`, the expression `e1 e2` is valuable.

## Pattern Matching
- Patterns are used in lambda expressions, case expressions, `val`, and `fun` bindings.
- A clause is of the form: `pattern => expression`.
- Example:
  ```sml
  (case f of
     Vanilla => "Vanilla"
   | Chocolate => "Chocolate"
   | Strawberry => "Strawberry")
  ```

## Lambda Expressions
- Syntax: `fn pattern => expression`
- Example: `(fn (x : int, y : int) => x + y)`
- Lambda expressions are values of function type.

## Function Binding
- Use `val` or `fun` to bind a lambda expression to an identifier.
  - Example:
    ```sml
    val add : int * int -> int = fn (x, y) => x + y
    fun add (x : int, y : int) : int = x + y
    ```

## Datatypes
- Syntax:
  ```sml
  datatype <type_con> = <value_con_1> | ... | <value_con_k>
  ```
- Example:
  ```sml
  datatype flavor = Vanilla | Chocolate | Strawberry
  val bestFlavor : flavor = Chocolate
  ```

## Induction and Recursion
- **Induction:**
  - **Base Case(s):** Corresponds to base case(s) in recursion.
  - **Inductive Step:** Corresponds to recursive case.
  - **Inductive Hypothesis:** Corresponds to recursive call.
- **Weak Induction:** Assume `P(n)` holds for some `n >= 0`.
- **Strong Induction:** Assume `P(k)` holds for all `0 <= k < n`.

## Extensional Equivalence
- Two expressions are extensionally equivalent if they:
  1. Reduce to the same value.
  2. Raise the same exception.
  3. Loop forever.
- Example: `fn x => 2 + 2` and `fn x => 4` are extensionally equivalent.

## Operators
- **Numeric Multiplication (`*`):** `8 * 3` evaluates to `24`.
- **Real Division (`/`):** `3.0 / 2.0` evaluates to `1.5`.
- **Integer Division (`div`):** `3 div 2` evaluates to `1`.
- **Modulo (`mod`):** `8 mod 3` evaluates to `2`.
- **String Combination (`^`):** `"foo" ^ "bar"` evaluates to `"foobar"`.
- **List Construction (`::`):** `1 :: [2, 3, 4]` evaluates to `[1, 2, 3, 4]`.
- **List Combination (`@`):** `[1, 2] @ [3, 4]` evaluates to `[1, 2, 3, 4]`.

## Associativity
- Most operators are left-associative.
- Right-associative operators: `::` and `@`.

## Boolean Operations
- `andalso`, `orelse`, `not`.

## Proofs 
- Proving totality requires `⇒`.
- For structural inductions on a list `L = (x::xs)`:
  - **Base Case (BC):** `[]`
  - **Inductive Hypothesis (IH):** Assume the theorem holds for `L = xs`.
  - **Want to Show (WTS):** Theorem holds for `L = (x::xs)`.
