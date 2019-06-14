
# A Short Guide to VScode Snippets

## Photo by Matt Artz on Unsplash

A quick way to get consistently output chunks of code is by the VScode inbuilt tool of snippets. This article explain the basics with plenty of provided examples. You may already be using snippets in VScode. There are few built in as part of language support. For example the Javascript for loops are all represented.

![](1*VkUe7PHeVewyY1TsHuVLzA.gif)

However you do not need to just rely on the built in ones. It may even be better for you not to. Creating your own snippets means that you know exactly how they’re named and they can confirm to your coding style. For example maybe you prefer using `i` instead of `index` in your for loop. My most commonly used snippet was one I wrote for console.log.

![](1*KNH-GYMUAbckpOqbocFpFQ.gif)

With just a simple `cl` and an enter key, I insert a `console.log('test);` with my cursor ready to type over the middle part. If I move my cursor off of the inserted bit of code it will just console log a string of test.

How To Add Your Own

![](1*LWDrIUywS4BNimis2TpwSA.png)

1. Go to File > Preferences > User Snippets

1. Here you will see a selection of snippet files. There are options for individual languages as well as the option to create a new global snippets file. I personally prefer to put my snippets in my the global file for ease of movement between computers.

1. If you chose to create a global file, you should now be in a file called `global.code-snippets` .

This is a JSON file despite the name. Next we will look at the `console.log `snippet I showed above.

```
"Console Log Text": {
    "prefix": "cl",
    "scope": "javascript,typescript,javascriptreact",
    "body": [
       "console.log(${0:`Test`});"
    ],
    "description": "Adds a quick console log for testing"
},
```


The breakdown of what each of these things mean:

`"Console Log Text"` — This is the name of the snippet you do not see it outside of this file. 
`"prefix"` — Prefix is what you will type to make the snippet pop up with auto completion. Note that this can be an array of strings if you want multiple names.
`"scope"` — This field is not necessary on snippets contained on a specific language file. It is however on the global config file. In this case I have this snippet appear for js, ts, and jsx files. To see a complete list of languages that VScode supports visit [this page](https://code.visualstudio.com/docs/languages/identifiers). 
`"body"` — The meat of the snippet. I will go into greater detail in the next section about this field. 
`"description"` — This is what appears above the example code on the VScode selection popup.

Creating the Body of a Snippet

As promised I will now go into the body section. The body I provided above is one unindented line which you may recognize as not how much code looks. If you look closely you’ll notice it is contained inside an array and not just a string. To get multiple lines you just keep adding strings to the array. However that will not add indentation. To do so just add `\t `to the front of your string.

```
"body": [
    "const ${1:mappedArr} = ${2:arr}.map((e,i)=>{",
        "\treturn ${0:e}",
    "})"
],
```


This is another code snippet I wrote. This one adds a map method to an array when map is typed. Notice the `\t` on the middle part allowing allow indentation to be added. This will use spaces or tabs depending on what you have your editor set to.

You may also notice the $ sign next to the number. That’s called a tab stop. When you first insert the snippet your cursor will end up on the `$1`. Each tab key press after that will move to the next tab stop in order. The `$0` is the final place for the cursor. If you have the same number twice, the cursor will appear at both at the same time. In the one above after insertion the cursor will be right next to the `return` then a tab key will move it up to right next to the `const` and the last tab push will put the cursor a space away from the `=` .

![](1*eODMvhcf4v1x8Cxx4Ugifw.gif)

If you just put `$0`this will just leave an empty to type. My example in gif does have filled values already. This is called a placeholder. Changing your tabstop from `$0` to `${0:"Your Value"}` adds the placeholder. When you tab to it the whole placeholder is highlighted allowing easy replacement just via typing.

![](1*5aK721cpkzrn8HeY2Rr2PQ.gif)

Multiple choices are possible as a placeholder. The above example is written as `$(1|'test','Hi',err|}.`It allows a selection of options via the drop down menu.

Finishing Up

That is all you really need to get started making your own snippets. A few more advanced features exist like Variables for things like CURRENT_TIME, LINE_COMMENT, and TM_SELECTED_TEXT. You can assign keyboard shortcuts to insert snippets as well. If you make enough good ones you can also package them up and distribute them as an extension on the VScode Marketplace. If you come up with anything cool, let me know! Either by replying here, or via Twitter.