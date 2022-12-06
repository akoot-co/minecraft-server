# Preface
Whenever you come across a funny message that looks like this, it means that it hasn't been initialized with a proper message yet.
The reason it's called a "string" is because it's a "string" of characters, it can be interchanged with the term sentence or paragraph, but I will refer to a "string" as merely a message.

# Tools
Use your text editor of choice and set the syntax to TOML.
If you don't have a text editor, use [this site](https://www.toml-lint.com/)! I implore you to click the **Validate** button when you're done with the edits.

# What do I do now..
Consider the following in-game message:
![Exhibit A](https://raw.githubusercontent.com/akoot-co/minecraft-server/master/Pasted%20image%2020221205213415.png)
Now is the time for action. Type the command that is "broken", and click on the first line it spits out. this will give you the path.

Paste the path in the text editor, within brackets.
For example: \[messages.select.value.error]

Notice that the last part is not copied. That is because the last part is actually the "key".
Underneath \[messages.select.value.error], you write `key = "message"`

Example:
```
[messages.select.value.error]
title_not_unlocked = "You have not unlocked the $TITLE title!"
```
Notice the `$TITLE` in this string. As you can see, the message you get in-game tells you what `TITLE` is. It is *j* in this case. It also tells you that `PLAYER` is *your*. They are the values for placeholders.
Placeholders start with a dollar sign `$`, and will be computed with the actual value in-game. An error message like the one above will tell you which placeholders you are allowed to use. You don't have to use any placeholders, but depending on what you want the message to say, you should use them!

Here's another example:
![Exhibit B](https://raw.githubusercontent.com/akoot-co/minecraft-server/master/Pasted%20image%2020221205213733.png)
Here we see a total of 2 placeholders, `TITLES` and `PLAYER`.

We can then create a message string like so:
```
[messages.list.success]
get = "You currently own these titles: $TITLES"
```

Notice I didn't use the `PLAYER` placeholder.

# TOML issues
Here are some things to consider which may seem correct but are actually not.

You cannot have 2 of the same paths at the same time, such as:
```
[messages.list.success]
cool = "Something"

[messages.list.success]
lame = "something else"
```

You instead have to write it like this
```
[messages.list.success]
cool = "Something"
lame = "something else"
```
