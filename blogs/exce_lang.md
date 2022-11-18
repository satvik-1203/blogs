---
name: Exce Lang
Topics: Programming Languages And Concepts
Date: 11/18/2022
---

# Exce Lang

Guess what we are making this time? A programmingggggg language. It's a simple language containing variables, loops, condition statements, and mathematical operations. To make a programming language, we should first understand lexical, grammar, and many other boring programming concepts. Many of you reading this aren't here to learn those concepts, so I'll briefly introduce the concepts I think are essential, and we can dive into the code.

## What are lexical?

Each word is a lexeme, also called a token. Suppose we have a \{ , the token representation would be `CODEBLOCKOPEN` or another name the language creator gives.

for example, a Java code such as

```txt:example showLineNumber
10 + 16 * y;
```

INTEGER: 10
ADD: +
NUMBER: 16
MUL: \*
VARIABLE: y
STATEMENTEND: ;

Each word in the line gets translated to a token and then the action is performed. If you don't understand, bare with me, I'll get back to it soon.

## Backus Naur Form

Backus Naur Form is the most crucial topic to understand. The entire code will revolve around this concept.

> In computer science, Backus–Naur form or Backus normal form is a metasyntax notation for context-free grammars, often used to describe the syntax of languages used in computing, such as computer programming languages, document formats, instruction sets and communication protocols.

Taken from **Wikipedia**.

Like you, I didn't understand a thing from the definition. It's hard to explain it without a picture.

```txt:productionRules showLineNumbers
<Program> --> begin <stmt_list> end
<stmt_list> --> {<stmt> `;`}
<stmt> --> <if_stmt> | <while_stmt> | <as_s>  | <declaration>
<declaration> --> <datatype> <var> `;`
<if_stmt> --> cond `(`<bool>`)` `{` <stmt_list> `}`
<while_stmt> --> repeat <bool> `{`  <stmt_list> `}`
<as_s> --> <var> = <expression>
```

There are more production rules, but I'll talk about them when the time comes. Let's try to understand what the above grammar says.

`<Program> --> begin <stmt_list> end`

Our program starts at `begin` and ends at `end.` Between the two, we are going to have all our code. Which is what `<stmt_list>` stands for - a list of statements. As the name says, a statement list is just a bunch of statements. **What is a statement?**.

`<stmt> --> <if_stmt> | <while_stmt> | <as_s> | <declaration>`

The line indicates that statement can be either one of the four; if statement, while statement, assign statement, and declaration statement.

`<declaration> --> <datatype> <var> ;`

A declaration statement starts with a **datatype**, is followed by a variable name, and ends with ; .

In our language, the following data types are:

- SHORT (1 byte)
- TALL (2 bytes)
- GRANDE (4 bytes)
- VENTI (8 bytes)

The variable can be anything.

`<as_s> --> <var> = <expression>`

The assigning statement starts with a variable that is already declared, separated by `=`, and ends with an expression. We will talk more about an expression later, but you can now think of it as assigning the variable to some number.

`<if_stmt> --> cond (<bool>) { <stmt_list> }`

Similarly, if a statement starts with the keyword **cond**, it comes under the if statement.

The statement inside `( )` is a boolean expression. We will talk about how boolean expression is translated to grammar later. and we <stmt_list> again inside `{ }`. Perform if the boolean expression is true.

`<while_stmt> --> repeat <bool> { <stmt_list> }`

Similar to an if statement, statements start with **repeat** and keep running <stmt_list> till bool is false.

I'm hoping by now. We learned how the diagram above works. Let's cover the statements we missed out on.

```txt:productionRules showLineNumbers

<datatype> --> (SHORT|TALL|GRANDE|VENTI)

<var> -->  [a-zA-Z_]{6,8} // our variable rule

<expression> --> <term> { (`*`|`\` ) <term> }
<term> --> <term> { (`+`|`-`) <term> }
<factor> --> [0-9]+ | <var>  | `(` <expression> `)`

<bool> --> <expression> (`<=`|`>=` | `<` | `>`) <expression>

```

You all probably needed clarification on the expression. Let's try and understand what's happening. And a heads up, _ and / has a lower priority than + and - in my language, and parenthesis has the highest priority. `{ }` indicate that you can either have it or have multiple of what's inside the brackets. The regex example would look like this: term( (_|/) term)\*

### What is an expression?

2
2 + 10
-2 \* 15 + x

Suppose our expression is -2 _ 15 + x. One way of looking at it is,
-2 (_ 15 + x). -2 is a term and 15 + x is another term. -2 satisfies factor. 15 + x can again be broken down to 15 (+ x). 15 is a factor since it's a number, and x is a factor since it is a variable. I did a good job explaining expression grammar.

```txt:productionRules showLineNumbers

E --> E + T             Expression + Term
E --> E - T             Expression - Term
E --> T                 Some expression can be a term
T --> T * F             Term * Factor
T --> T / F             Term / Factor
F --> -F                Unary Minus
F --> +F                Unary Plus
E --> a                 Factor can be a constant
E --> (E)               Factor can be an expression in parentheses.

```

Whoo, that was somewhat long. We can finally start with understanding the code.

```txt:sample.exce showLineNumbers

begin

GRANDE var_one;
var_one = 10 * 15 + 2;
SHORT iter_i;
iter_i = 1;

repeat (iter_i <= 3) {

	cond (var_one < 100) {
		var_one = 101;
	}

	iter_i = iter_i + 1;
}

end

```

Let's see what happens now.

We first read the file and get all the statements inside begin and end. Then we start reading the statements line by line.

The first statement begins with a data type, so we know it's a declaration operator. The following statement starts with a variable, so we know it's an assigning operator, similarly for the third and fourth. The fifth statement begins with a repeat; we know it's a loop statement. The following statement starts with cond, so we know it's an if statement.

That should give you a base understanding. For the rest of the part, I'll explain in the code.

<iframe src="https://codesandbox.io/p/github/satvik-1203/exce-lang/main?file=%2Fsrc%2Fstatement.ts" title="code" height="700"></iframe>
