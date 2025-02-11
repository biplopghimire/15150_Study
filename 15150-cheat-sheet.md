# 15-150 Cheatsheet

## Type-Checking and Evaluation
- **Type-checking happens before evaluation!** Only well-typed expressions can be evaluated (into values).

## Built-in Comparison Operators
- Operators: `>`, `<`, `>=`, `<=`
- Operate on: `int`, `string`, `char`, `real`

## Operations and Types
- A tuple of values is itself a value.

## Binding Values
- **Big idea:** Bind values to variable names using `val` or `fun`.
  - **Examples:**
    ```sml
    val x : int -> int = (fn y => y + 1)
    fun x (y : int) : int = y + 1
    val add : int * int -> int = fn (x, y) => x + y  (* Merged from Function Binding *)
    fun add (x : int, y : int) : int = x + y         (* Merged from Function Binding *)
    ```
- **Note:** Declarations are not expressions. Do not use `val`/`fun` when an expression is required.

## Function Application
- **Big Idea:** `e e’ : t2` iff `e : t1 -> t2` and `e’ : t1`

## Totality and Valuability
**Definition (Valuable).** A well-typed expression `e` is *valuable* if there exists a value `v` such that  
`e ⟹ v`. We also say that *e evaluates to a value*.
**Definition (Total).** A well-typed expression `e1 : t1 -> t2`, for types `t1` and `t2`, is *to

## Pattern Matching
- Used in lambdas, `case`, `val`, and `fun`.
- **Clause Syntax:** `pattern => expression`
  ```sml
  (case f of
     Vanilla => "Vanilla"
   | Chocolate => "Chocolate"
   | Strawberry => "Strawberry")
  ```

## Lambda Expressions
- **Syntax:** `fn pattern => expression`
- **Example:** `(fn (x : int, y : int) => x + y)` (a value of function type).

## Datatypes
- **Syntax:**
  ```sml
  datatype <type_con> = <value_con_1> | ... | <value_con_k>
  ```
- **Example:**
  ```sml
  datatype flavor = Vanilla | Chocolate | Strawberry
  val bestFlavor : flavor = Chocolate
  ```

## Induction and Recursion
- **Induction Steps:**
  - **Base Case:** Corresponds to recursion's base case.
  - **Inductive Step:** Assume `P(k)` for `0 ≤ k < n` (strong) or `P(n)` (weak), prove for `n`.
- **Structural Induction on Lists:**
  - **Base Case (BC):** `[]`
  - **Inductive Hypothesis (IH):** Assume theorem holds for `xs`.
  - **Inductive Step (WTS):** Show holds for `x::xs`.

## Extensional Equivalence
- Two expressions are equivalent if they:
  1. Reduce to the same value.
  2. Raise the same exception.
  3. Loop forever.
- **Example:** `fn x => 2 + 2` ≈ `fn x => 4`.

## Operators
- **Numeric (`*`, `/`, `div`, `mod`):** `8 * 3 = 24`, `3.0 / 2.0 = 1.5`, `3 div 2 = 1`, `8 mod 3 = 2`.
- **String (`^`):** `"foo" ^ "bar" = "foobar"`.
- **List (`::`, `@`):** `1 :: [2,3,4] = [1,2,3,4]`, `[1,2] @ [3,4] = [1,2,3,4]`.
- **Associativity:** Most left-associative. Right: `::`, `@`.

## Boolean Operations
- `andalso`, `orelse`, `not`.
