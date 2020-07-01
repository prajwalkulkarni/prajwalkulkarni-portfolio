---
layout: post
title: "Web automation in python"
date:   2020-07-01
excerpt: "This article covers,how to automate tasks on web using python and selenium"
image: "/images/pic05.jpg"
categories: coding
---


Automation has been a giant leap in the evolution of mankind.
Everybody prefers automation mainly because it saves time and human effort.
Tasks which require repititive steps to be performed periodically are automated.
In today's aticle we'll see how we can automate few tasks which we do on the internet.

We'll be using python to do this.
Firstly install "Selenium" library, selenium is a popular web application testing tool.

To install selenium:<br>
``` pip install -u selenium
```

We'll be writing a script to send custom messages to WhatsApp contacts. (or spam, lol :P)

create a new python file <b>spam.py</b>


<script src="http://gist-it.appspot.com/https://github.com/prajwalkulkarni/whatspam/blob/master/spam.py"></script>

We can see that, there's a class 'Spam' class with an initializer to assign values such as recipient user name, count(message count) and message body.<br>
The function 'startSpam' contains a <i><b>try/catch/finally</b></i> block locates the search bar to input user name -> clicks to open the chat(if exists),else an exception is thrown and the finally block is executed.
If the chat gets opened(i.e a valid contact/group name was entered),
A 'for' loop is executed which sends the message equal to the 'count' value supplied.
Then the 'finally' block is executed, Note that we're using a dictionary to display an appropriate message based on whether the task was accomplished or not.<br>
'''self.complete=True or self.complete=False'''<br>

Further, we make use of 'if-else' ladder where the user is prompted to re-run or quit the program.

Finally, in the ```if __name__=="__main__"``` block, we take first time user input and pass them as arguments of 'Spam' class's object.

<h4>Chromedriver</h4>
In order to automate the above process, you'll need to have chromedriver installed.
You can download it from <a href="https://chromedriver.chromium.org/downloads" target="_blank">here</a> .<br>
That's all for this article, I hope you found this interesting, you can also play around and modify this code to perform other tasks, you could also schedule the messages by using the 'time' library.
