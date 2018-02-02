---
layout: post
title:      "Hoisting and Scope in JS, briefly"
date:       2018-02-02 18:33:01 +0000
permalink:  hoisting_and_scope_in_js_briefly
---



So I've found a new favorite jargony programming term: the "temporal dead zone." This is the place, according to the MDN, where a **let** or **const** variable will be lost to if the variable's declaration and assignment operations are out of order. Which is to say, declare first then assign/initialize after. Seems like an easy enough mistake to avoid. 

By comparison, a **var** variable can't be lost to the temporal dead zone. And here's the why of it: hoisting. 

Hoisting is JS's way of reframing the declaration of a **var** (and functions, more on which later), so that wherever the variable was assigned and wherever the variable was declared in a particular scope will not affect how the program operates. Not so for **let** or **const**, which, while are technically but not functinally hoisted to the top of its respective scope. As a result, these two variable types will throw an error. 

Still, where **var** variables are delcared does, of course, matter, since only the DECLARATIONS and not the INITIALIZATIONS are hoisted. Code that refers to a sequentially as-yet-uninitialized variable will not be aware of the variable's value from that initialization at the time of hoisting, even though the program will be aware of the var's declaration. 

As a result of the hoisting, the uninitialized variable will return an 'undefined' value, as opposed to throwing an error, which is what happens with out-of-order let and const declaration/initializations. 

Function declarations, by comparison, are also hoisted to the top of their scope and are considered by the program as declaration first and execution second, no matter what order they were coded in the program. That is to say, a function can be called first and declared second, and it will still... function (no pun). Function expressions cannot be declared this way or else they will throw an error.

The big takeaway: declare your variables at the top. Simple solution!  Easier for the next coder to look at your code to understand what's going on! Win-win. 


