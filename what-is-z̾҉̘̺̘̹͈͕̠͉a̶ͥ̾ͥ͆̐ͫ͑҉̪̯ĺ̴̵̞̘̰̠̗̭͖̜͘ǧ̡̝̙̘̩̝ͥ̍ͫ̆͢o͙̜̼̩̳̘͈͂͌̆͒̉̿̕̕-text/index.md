
# What is Z̾҉̘̺̘̹͈͕̠͉a̶ͥ̾ͥ͆̐ͫ͑҉̪̯ĺ̴̵̞̘̰̠̗̭͖̜͘ǧ̡̝̙̘̩̝ͥ̍ͫ̆͢o͙̜̼̩̳̘͈͂͌̆͒̉̿̕̕ text?

## 

You may have seen z̎ͬ̂̅̋҉̹̘̬̠̩̲͖aͫ̆͗ͬ͏̷̟̣̗l͕̩̹̥̮͇̈́͞͡g̹͓̾͜͟ỏ̑͒ͦͣ̓̓͗̀͏̭͔͔̱́ text before, originally popularized by [eeemo.net](http://www.eeemo.net/). This spooky mysterious text has a simple cause. But before we get into it we have to delve into a part of Unicode that is not often seen.

If you have read my previous article [The 𝕆ᗪ⒟𝙞ȶч of Unicode Homoglyphs](https://medium.com/@Andrew_Mc/the-%E1%97%AA-%C8%B6%D1%87-of-unicode-homoglyphs-41ee73b57913), you will know that Unicode is massive and a lot of the characters in it are just plain unknown. There are certain ones that are that way because there is no glyph to represent them. These are things like line ends, making text right to left, and various joiners and spaces. If you just want to the answer scroll down until you see the title, if not prepare to learn more about the invisible part of Unicode.

These are not new. The first 31 ASCII character code are all different control characters. Some are still used, like NUL (ASCII 0, U+0000) which is used to terminate strings in C. Some less so like [BEL ](https://en.wikipedia.org/wiki/Bell_character)(ASCII 7) which while working in terminals, is not something an average user is likely to run into. Unicode inherited these control characters to maintain full compatibility with ASCII.

Some other interesting control characters are the directional text known as the LEFT-TO-RIGHT( U+200E) and RIGHT-TO-LEFT( U+200F) characters. There are few different ones but the basic gist is that they will allow you to use Hebrew or other Right to Left texts in the middle of English. There’s also an explicit Arabic one ( U+061C). My attempts to display an example here were limited in success so I instead link you to a Wikipedia [example](https://en.wikipedia.org/wiki/Right-to-left_mark#Example_of_use_in_HTML).

Perhaps the most interesting to your actual usage however would be the Zero-width joiner. You may have used this without realizing it. What it was intended to do was allow two letter to combine if a script needed it. It was more recently used as a way of combing emojis. For example if we have the woman emoji 👩, the medium skin tone 🏽, and the 🚀it just takes a few zero width joiners to make 👩‍🏽🚀. A full list of these combinations is available on [emojipedia](https://emojipedia.org/emoji-zwj-sequences/). Interestedly this is not how flags work[1].

A last interesting note is the spaces of Unicode. There are many more than you think, and they are a good way to frustrate people and make things not look quite right. I have provided examples of them all bellow:

(Please note I cannot control how Medium presents these to you, they seem to ignore the tab character entirely. If these are not rendering for you, try [Wikipedia](https://en.wikipedia.org/wiki/Whitespace_character).

```
    |U+0009 character tabulation (normal tab)
 |U+0020 space (your space key)
 |U+00A0 no-break space (this will not allow the two words to be split for a line break)
 |U+1680 ogham space mark (Ogham is an early Irish Language)
 |U+2000 en quad (an en is half an em, which is not the width of an M unless you’re running a printing press)
 |U+2001 em quad (instead em is equal to the font pixel size, even if the font size is user defined) 
 |U+2002 en space (So if you have explicitly set the font size to 24px, that is what 1 em or 2 en(width wise) will equal)
 |U+2003 em space (Wikipedia notes to use 2002,and 2003 over 2000 and 2001)
 |U+2004 three-per-em space (1/3 of an em)
 |U+2005 four-per-em space (1/4 of an em)
 |U+2006 six-per-em space (1/6 of an em )
 |U+2007 figure space (a space the size of one monospaced digit)
 |U+2008 punctuation space (the size of punctuation in a font)
 |U+2009 thin space (1/5 of an em)
 |U+200A hair space (thinner then the last one)
 |U+202F narrow no-break space (1/3 of a no break space)
 |U+205F medium mathematical space (4/18ths of an em. This is for math but… seems oddly specific)
 |U+3000 ideographic space (fullwidth space essentially)
​|U+200B zero width space
```


### The Actual Answer

Combining characters. This is what Z͔͡á͔̙̞̞͕͕̱l̨g̤͔̞̻̰ọ͘ is. Just stacks of combining characters. More specifically combining diacritical marks. If you have been paying attention to my previous article as well this one you will notice that Unicode never makes just one character when they could make more. In this case say you needed to write some word plundered from french like *risqué. *Well you could use é (U+00E9) or you could use e (U+0065) put next to ́ (U+0301) which would form é. Now if you copy that and try to scroll through it with a cursor you will notice the cursor hits that letter twice. If you delete while in the middle the e will disappear and the ́ will jump to the nearest character which happens to be a space which is how I keep writing it without making it seemingly attaching to anything.

Why is a very good question here. Unicode actually has an [FAQ ](https://unicode.org/faq/char_combmark.html)for this. I will sum it up as from what I can tell are the two main reasons. The first is that they want you to be able to express pretty much anything you need to and these are tools to allow you to do it. The second is it makes it so if a font does not support the precomposed version that it will allow a graceful fall over. In the example above if a font didn’t support é you would get the unicode missing square. If you used the combining version you would get an e followed either by a square or a misaligned acute accent. A much more graceful failing.

What is happening in Z͔͡á͔̙̞̞͕͕̱l̨g̤͔̞̻̰ọ͘ is pretty simple. There is no limi̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇̇t to how many combining diacritics you can stick in a row. What Z͔͡á͔̙̞̞͕͕̱l̨g̤͔̞̻̰ọ͘ becomes is:

![](1*DtrHW-wmvv6ozCYnOciGRQ.png)

This is much easier to see when split out like this. The original Zalgo generator does not even cover the full amount of combining marks. Some are very unsupported but others were left out due to the lack of creepy factor. The letters, aeioucdhmrtvx all have combining versions. Useful if yͨoͣuͭ like cats or like things aͣrͬcͨhͪiͥvͮeͤdͩ. Looking up why these were added pointed to the transcription of historical German texts and in fact the initial proposal had all the Latin characters both above and below.

If you want to play with this, I made a site that lets you play with unicode. Just go to [https://textconstructor.y42.xyz/](https://textconstructor.y42.xyz/) type in a word, select a letter, select individual letter editing , then letter decoration. You can apply as many as you want. I also have my own implementation of Zalgo located there that does use everything in the combining diacritics block. Hopefully this explanation covered everything you were wondering. If I missed anything or got it wrong please either comment bellow or contact me either here or via social media.

*[1] I’m moving this to a footnote so I don’t delay the actual topic any longer. In my previous article I was asked why I didn’t include regional codes such as 🇺 as an alternative to Latin text. The reason is they only render like that on Windows, if you put two together 🇺🇸 it will show up as a flag on anything but Windows. This does not use a zero width joiner.*