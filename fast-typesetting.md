---
layout: default
title: Fast Typesetting with Obsidian Plugins 
---

# Fast Typesetting with Obsidian Plugins 

*This guide is a follow up to my <a href="latex-guide.html">last post</a> about typesetting with LaTeX.*

## The Problem

If you've ever prepared a document with LaTeX before, you know that it can be a long and frustrating process. The language is built to create scientific papers, and it comes equipped to deal with the detail that one would expect from such publications. But the cost of precision is time, and virtually nothing in LaTeX is designed to be done quickly. 

Every command requires the inconveniently located backslash key, and you'll probably get carpal tunnel from open and closing the curly brackets every five keystrokes. To make matters worse, common symbols often require five or more characters, like `\partial`, `\mathbb{R}`, or `\Leftrightarrow`. 

However, not all is lost. This article will show you how to transform LaTeX from a hulking monolith of mathematical symbosl and formatting commands to a simple, customizable tool for taking notes in math and science classes.

## The Solution

In 2019, the late [Gilles Castel](https://castel.dev/) published an excellent blog post on his system for taking notes using LaTeX and Vim. Instead of typing the commands by hand, he used a snippet program to autocomplete symbols as he typed. If you're familiar with configuring Vim and want to try this, the original article is [here](https://castel.dev/post/lecture-notes-1/). A more detailed guide, written by Elijian Mastnak, can be found [here](https://www.ejmastnak.com/tutorials/vim-latex/intro/).

However, not everyone wants to learn Vim. For the less technically inclined, there's the [Obsidian LaTeX Suite](https://github.com/artisticat1/obsidian-latex-suite), which can be installed using the following steps:
1. Open the settings menu in Obsidian
2. Go to the community plugins tab and make sure that "Restricted Mode" is off. 
3. Click "Browse", then search for, install, and enable the Obsidian LaTeX Suite.

To check that it was installed correctly, open a new note and type `mk`. If the text is automatically repalced with `$ $`, then the plugin is installed correctly. 

## Writing Snippets

For a more thorough introduction to writing snippets, I recommend you read the [documentation](https://github.com/artisticat1/obsidian-latex-suite). To create and remove snippets, open the Obsidian settings menu, then click on the "Latex Suite" tab under "Community Plugins".

A snippet is a javascript object that looks like this:
```
{trigger: "...", replacement: "...", options: "..."}
```
- `trigger` is the series of keystrokes that will activate the snippet.
- `replacement` is the text that will replace the trigger. If you're writing LaTeX, remember to escape backslashes by writing `\\` instead of `\`.
    - The replacement can contain any number of tabstops, which are included using the characters `$0`, `$1`, etc. Upon snippet activation, the cursor will be moved to the first tabstop.
- `options` is a string of characters that contains the settings:
    - `m` stands for "math mode". If this setting is enabled, the snippet will only activate in math mode (either inline or display).
    - `A` stands for "autocomplete". If this setting is enabled, the trigger will be replaced immediately. Otherwise, you will have to press TAB.

For example, here is a simple snippet that replaces `ff` with `\frac` command:
```
{
    trigger: "ff",
    replacement: "\\frac{$0}{$1}",
    options: "mA"
}
```
- Note that we use escape the backslash character using `\\`.
- `"mA"` means the snippet will activate automatically in math mode.
- Upon snipet activation, the cursor will move to the `$0` tabstop. If you press tab again, it will move to the `$1` tabstop.

## Building a System

Now, go to back to the settings menu, and *delete all the default snippets*. If you want to remember your snippets and build a system that works for you, it's best to write them yourself. Of course, feel free to check the default snippets for ideas, many of them are very good.

Here are some of my recommendations:
- Every snippet should autocomplete using the `"A"` option. The only time I don't do this is for large snippets like matrices and environments.
- Snippets should be 2 or 3 characters long, maybe 4. 
- Snippets should not use groups of letters that are commonly used in mathematical expressions. For example, an autocopmleting snippet with the trigger `dx` will frequently activate when you don't want it to. 
- Use capital letters and special characters to differentiate snippets.
- ONLY create snippets when you need them. Remember that every additional snippet creates more possibilities for errors.

If you're in need of ideas, here are some of the snippets I use:
- Short greek letters use their full name as a trigger (i.e. `pi` for `\pi`)
- Long greek letters use a semicolon followed by the first letter of the command as a trigger (i.e. `;l` for `\lambda`).
- Mathematical sets use double capital letters (i.e. `RR` for \\(\mathbb{R}\\))
- Arrows use the corresponding combination of `-`, `=`, `<` and `>`. For example, I use the trigger `=>` for the \\(\Rightarrow\\) symbol.
- I use `neq`, `geq`, and `leq` for the inequalities \\(\neq, \geq,\\) and \\(\leq\\).
- I use the trigger `tt` for the `\text{}` command and `ff` for `\frac{}`.
