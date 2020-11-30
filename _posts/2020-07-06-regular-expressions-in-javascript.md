---
layout: post
title: "Regular expressions in JavaScript"
date:   2020-07-06
excerpt: "This article covers what are regular expressions and how to use them in JavaScript"
image: "/images/regex.jpg"
categories: coding
---

Regular expressions(regEx) are patterns used to match character combination in a string. They're also objects(in Javascript), meaning functions defined in the regEx obj class can be called on it. regEx is a common concept and can be used in any language.
Regular expressions are mainly used in string validation, i.e if a given string meets specific format or not. A more real world example would be form/input validation. A form consists of various fields like <i>Name,age,email,password et cetera...</i> . All the fields are unique and needs to be formatted in a certain way, this is where regular expressions comes handy.
In today's article we'll be looking at how to use regular expressions in JavaScript which can be used in other languagues as well(with few changes).<br>

<h2>Manual validation v/s Regular expressions</h2>
As I said above in a form validation, we'd want to make sure that the values entered are valid and properly formatted.
But wait, couldn't we achieve the same by minimal common sense ?
Let's take a look at it.

E.g validate a password, where it needs to satisfy the following conditions:<br>
<ul>
	<li>Minimum of 8 characters</li>
	<li>Should contain atleast 1 number</li>
	<li>Should begin with a captial letter</li>
</ul>

1. Minimum 8 characters

```
var str = 'a234567B'

if(str.length>=8){
	return true
}
```
<br>
2.Should contain atleast 1 number 

```
var str = 'a234567B'
var num = 0

for(s in str){
	if(parseInt(str[s])){
		num+=1;
	}
}

if(num.length>=1){
	return true
}
```
<br>

3.Should begin with a capital letter

```
var str = 'a234567B'

if(str[0]>="A"&&str[0]<="Z"){
	return true
}
```

As we can see above, to satisfy the condition we're making use of several <b>if-else</b> statements along with loops, which needs to iterate over the string length or whatsoever, and this is only to validate a single field.
This is a bad programming practice as it increases code base, space and time complexity.
So, a good rule of thumb is to make use of regular expressions.
Using regular expressions binds all the required logic in a single line. It also greatly reduces the need to use iterators or multiple if-else statements.
<br>
Now,let us look at it's syntax and how to use them.

<h2>Input,Syntax and formatting</h2>

To validate any input we require a formatting logic, so this logic, is enclosed within two forward slashes "//".

```
var regEx = /regular-expression-here/;
```

First off, to check if there's a pattern present in the given string or not, we just specify the pattern within the forward slashes.Note that, plainly writing down the pattern does not consider the pattern's position in the given string, it returns true if a match is found, irrespective of the position.<br>
E.g

```
var str = "ABCDEFQQQ"

var regEx = /QQQ/

if(regEx.test(str)){ //if statement is executed.
	return true;
}
```
The given string is "ABCDEFQQQ" and the pattern we're checking for, is "QQQ". As previously said, regular expression is also an object in JavaScript, hence we're calling a method called 'test' on the regEx object.
The 'test' method takes an argument which is the test string and returns <b>boolean</b> ,i.e, returns true if the pattern is found(as per the rules specified) , false otherwise.
<br>
By default, regular expressions are case sensitive, to make it case insensitive, just add 'i' at the end of the expression.

```
var regEx = /QQQ/i
var str = "ABCqqq"

if(regEx.test(str)){ 
	// if statement executed,because expression is now case //insensitive.
	alert("match found")
}
```

<h3>Character set and range</h3>
Suppose, we need to look for a pattern(again,irrespective of position) where the first character in the pattern needs to be a vowel(a,e,i,o,u) followed by 123. 
Here, we can make use of character set and range.
A character set is defined inside square brackets '[]'.

```
var regEx = /[aeiou]123/
```
'aeiou' is placed within the square bracket which means the first character in pattern could be any vowel. Again, by default expressions are case sensitive , to make it insensitive, we could use an 'i' flag or include capital vowel letters.

```
var regEx = /[aeiou]123/i
//(or)
regEx = /[aeiouAEIOU]123/
```
Now what if the first character could be any alphabet and not just a vowel ? If you say we can inlcude all the alphabets like,
[abcdefghijklmnopqrstuvwxyz] . You're not wrong, but an easier way to do it would be to specify the range.

```
var regEx = /[a-zA-Z]123/
```

Multiple character sets could be used as per required.
We could also exclude certain characters at the beginning or at any position in the pattern by using the '^' sign.
For example, we could invert the above scenario, wherein the first character in the pattern cannot be a vowel.

```
var regEx = /[^aeiou]123/
```
<h3>Repeating character sets</h3>

In a pattern if we need to have certain characters at consecutive positions, instead of specifying the set for each position we use '{}' within which we describe the value, the value represents the repition count.
E.g: A pattern which should include 5 consecutive vowels.
With our current knowledge, we'd do something like this.

```
var regEx = /[aeiou][aeiou][aeiou][aeiou][aeiou]/i
```
The above expression is quiet tedious and lengthy, to cut down we can use '{}'.<br>
```
var regEx = /[aeiouAEIOU]{5}/
```

<h3>Shorthand notations for various character sets</h3>

Instead of using '[]' we could also make use of certain shorthand notations,to imply the same meaning.
<ul>
	<li><b>\d</b>:digits, can replace [0-9]</li>
	<li><b>\w</b>:words, can replace [a-zA-Z], whitespace and '_'(underscore)</li>
	<li><b>\s</b>:whitespace, can replace ' '(space) and '	'(tab)</li>
	<li><b>\t</b>:whitespace, can replace '		'(tab only).
	</li>
</ul>


<h3>Position and parts</h3>

Until now, we were concerned only about the pattern and really didn't cared about where it began and ended. All we looked for, is to verify if a pattern was contained in a string or not.
What if, we wanted to have only the pattern and not any extra characters preceeding or succeeding the pattern.
For that, we can make use of '^' and '$'. '^' Represents the beginning of string and '$' represents ending of the string.<br>
<b>Caution:'^' used within '[]' brackets means to exclude the characters in the square bracket, e.g [^abc] means to exclude abc, whereas '^' used outside '[]' brackets denotes the beginning of the string, e.g ^[aA] means the string should begin with 'a' or 'A'</b>
<br>

```
var regEx = /^[a-z]{5}$/
```
The above regular expression means that the pattern or string should begin with a small case alphabet, should consist of 5 letter (all small cap letters) and end with the same.

<br>
Sometimes, we wouldn't be certain of the string length,but the string should follow a certain format.
E.g consider email validation, which follows the following format:
<br>
<i>username@domain.com/net/in/co</i>
<br>
As we can see, the email address follows a format, it should begin with a set of characters(alphabets) followed by at, followed by set of characters,again followed by a period(.), further followed by an extension(com,net,in) basically set of characters.
A simple convention we could follow is divide the expression into 3 parts. The first part could contain any number of characters, the second part same as the first with a '@' in between, and the third part set of characters(only lowercase alphabets).

In regular expressions, we can partition pattern using parentheses '()'.

Let's see how a regular expression to validate email address would look like.

```
var regEx = /^([a-zA-Z\.-]+)@([a-zA-Z\.-]+).([a-z]{2,10})/
```
Explanation:
'^' in the first implies the beginning of the pattern, the first part could consist of any letters,inlcuding period(.) and hypen(-),
note that i've used '\.' instead of '.' directly, because '.' specified directly means a wildcard entry, '.' is like a placeholder for any character, since we need the '.' itself not to function as wild card entry we explcitly cast it as a plain character by using '\.'. I've used '+' after the character set which was not explained above, using plus functions similarly like {value} , except for the fact that + means greater than or equal to 1, where as {value} is more like hardcoded.
Since we're not sure of the username length we use '+'.
The second and third part get the same explanation, in the third part two values within '{}' are specified instead of one, two values means the range of characters, here {2,10} means atleast 2 and atmost 10 characters.

<br>
This covers the basics of regular expressions, there are still many concepts and topics on regular expressions and it could take a whole series.But this minimum knowledge is quiet sufficient to validate several instances.

<h3>Bonus</h3>

Q.Validate password which needs to satisfy conditions as stated above.

<br>
Ans:

```
var regEx = /^[A-Z](?=.*[0-9][a-zA-Z]{6})/
```
<b>Explanation:</b>

Should begin with a capital letter -> '^[A-Z]'<br>
Should contain atleast 8 characters(alphabets)  -> [a-zA-Z]{6}
siz letters+capital letter in the beginning+1 number = 8(minimum length satisfied)


This wraps up the article, I hope you found this informative and useful,if you did feel free to follow me on <a href="https://www.instagram.com/prajwalkulkarni_" target="_blank">Instagram</a> .
