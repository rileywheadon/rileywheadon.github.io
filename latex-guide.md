---
layout: default
title: Typesetting Mathematics using LaTeX
---

# latex-guide

If you read my <a href="why-obsidian.html">previous post</a> about why I use <a href="https://obsidian.md/">Obsidian</a>, you might be curious how to actually use LaTeX for formatting mathematical equations. This guide is intended for people using Obsidian or another markdown based text editor, and does not include information on document preparation. If you'd like to use LaTeX natively, I'd recommend you consult the [LaTeX Wiki](https://en.wikibooks.org/wiki/LaTeX/Introduction).

## What is LaTeX?

**LaTeX** is based on **TeX**, a *typesetting system* developed by Donald Knuth. Put simply, LaTeX is a way to convert plain text into an enormous variety of scientific symbols. It does this by using **Commands**, which start with a backslash. A command may accept one or more **Arguments**, as shown below.

```
\command{argument1}{argument2}
```
Commands can also be nested (placed inside each other). Remember to close all the curly brackets, otherwise it will cause an error. 

## Math Mode

When taking notes in Obsidian, there are two ways begin typesetting using LaTeX:
- Enter **Inline Math Mode** by wrapping LaTeX commands in single dollar signs. For example, if I type `$3x^2 + 2x + 4$` in an Obsidian note, it will look like this: \\(3x^2 + 2x + 4\\). Inline math mode is useful for including a few mathematical symbols without breaking the flow of your writing.
- Enter **Display Math Mode** by wrapping LaTeX commands in double dollar signs. If I instead type `$$3x^2 + 2x + 4$$` into an Obsidian note, the equation will appear centered and on a new line, like this:
\\[3x^2 +2x + 4\\]

## Basic Commands 

This section includes some of the more useful commands for symbols used in high school math and science classes. The examples will be shown in display math mode, but they can be used in inline math mode as well.

**Polynomial Functions**

Use the `^` symbol to write "to the power of". By using curly brackets, you can add multiple characters.
```
$$ x^4, x^{3x + 2} $$
```
\\[ x^4, x^{3x + 2} \\]

**Rational Functions**

Use the `\sqrt{}` command to write the square root symbol. You can also use `\sqrt[n]{}` to write an n-th root, as shown below.
```
$$ \sqrt{4}, \sqrt[6]{8} $$
```
\\[ \sqrt{4}, \sqrt[6]{8} \\]

**Fractions**

Use the `\frac{}{}` command to create a fraction. 
```
$$ \frac{x^2}{\sqrt{4}} $$
```
\\[\frac{x^2}{\sqrt{4}} \\]

**Greek Letters**

All of the greek letters have commands in LaTeX (like `\theta` and `\pi`). Some greek letters also have capital variants (i.e. `\Theta` is different than `\theta`).
```
$$ \theta, \Theta, \pi $$
```
\\[\theta, \\: \Theta, \\: \pi\\]

**Trigonometric Functions**

The commands `\sin`, `\cos`, and `\tan` are used to write the trigonometric functions. There is also `\arcsin`, `\arccos` and `\arctan`.
```
$$ A\sin(\theta) + D $$
```
\\[A\sin(\theta) + D\\]

**Logarithms**

The `\log` command is used to write a logarithm. You can add a base using the subscript command `_`.
```
$$ 3\log_2 (x) + y_1 $$
```
\\[3\log\_2 (x) + y\_1\\]

**Other Useful Commands**

Insert plain text using the `\text{}` command. Sometimes, the regular brackets aren't tall enough to cover a fraction. In this case, use the `\left(` and `\right)` commands together to fix it.
```
$$ x^2 + 3 \approx 3 \text{ (for small x)} $$
```
\\[ x^2 + 3 \approx 3 \text{ (for small x)} \\]
```
$$ \text{Short brackets: } (\frac{1}{2}) $$
$$ \text{Tall brackets: } \left(\frac{1}{2}\right) $$
```
\\[ \text{Short brackets: } (\frac{1}{2}) \\]
\\[ \text{Tall brackets: } \left(\frac{1}{2}\right) \\]


## Formatting Using Environments

These commands are used in display math mode for additional control over the formatting of equations. The first environment is the **Align** environment. Shown below is some example code and output:
```
$$ \begin{align}
    &x^2 + 4x + 12 \\
    = &x^2 + 4x + 4 + 8 \\
    = &(x + 2)^2 + 8
\end{align} $$
```
\\[ \begin{align}&x^2 + 4x + 12 \\\\ =\\:&x^2 + 4x + 4 + 8 \\\\ =\\:&(x + 2)^2 + 8\end{align} \\]

- Notice how the left edge of each equation is aligned.
- The `&` symbol is used to set the alignment point. 
- Use two backslashes `\\` to create a new line.

The **Cases** environment is used to create piecewise functions. See the example code and output below:
```
$$ f(x) = \begin{cases}
    x^2 + 5 & x < 0 \\
    3x & 0 \leq x \leq 2 \\
    6 & x > 2 \\
\end{case} $$
```
\\[ f(x) = \begin{cases} x^2 + 5 & x < 0 \\\\ 3x & 0 \leq x \leq 2 \\\\ 6 & x > 2 \\\\ \end{cases} \\]

- The `&` symbol is still used to set an alignment point.
- Cases are separated by a two backslashes `\\`.
- Any symbols before the `\begin{cases}` will be vertically centered.


