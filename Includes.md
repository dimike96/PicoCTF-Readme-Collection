# Includes

We are given a website (```http://saturn.picoctf.net:59300/```) and asked to find out what we can.

## Solution

Simple digging around using our browsers developer tools can often prove fruitful.

Under our "view-source" of the provided page we see two other files referenced: ```style.css``` and ```script.js```

Contents of ```style.css```:

```
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */
```

Contents of ```script.js```:

```
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_6edef411}
```

## Flag:

```
picoCTF{1nclu51v17y_1of2_f7w_2of2_6edef411}
```
