
# The 𝕆ᗪ⒟𝙞ȶч of Unicode Homoglyphs

## 

You may have heard of the concept of homoglyphs, or [confusables ](http://www.unicode.org/terms_of_use.html)as Սnicode calls them. To make it simplе just because a letter on a cοmputer looks like an X does not mean it is an Χ. In fact a few of characterꮪ in this last paragraph are not the standard Latin characters.

Above I avoided some more of the obⅴіo∪s ones. What blends in varies highly based on the font you are using and the particular formatting around it. Overuse of them can cause the [ransom note effect](https://en.wikipedia.org/wiki/Ransom_note_effect). The more devious, or the ones who have read about this before may have realized a problem with having identical characters. [wíkipedia.org ](http://wíkipedia.org)is a great example. At first glance it may appear to be Wikipedia, but it’s actually Desciclopédia, the Portuguese version of Uncyclopedia.

Those who followed the link may have noticed they are protected from such an attack. In the navbar it changes to [http://xn--wkipedia-c2a.org](http://xn--wkipedia-c2a.org). Different programs handle this differently. For example Discord does the same thing, but Slack will happily show the Unicode version. The reason behind this is the DNS wants hostnames to be in ASCII, but still wants to be able to support non-latin characters. The solution to this is called [Punycode](https://en.wikipedia.org/wiki/Punycode).

Unicode is massive. As of this writing the latest version is 11.0, which contains 137,439 characters from 146 different scripts. These range from languages in active use to things like Inscriptional Parthian and Linear B. There is even some fun stuff in there like ︘(*U+FE18) *whose name contains a misspelling of bracket as *brakcet*. There are 1,114,112 different code points in UTF-16, meaning that just over a tenth are used. Reducency is therefore not a problem and may go a bit to explaining why homoglyphs are allowed to exist.

If you want to play with what I am about to talk about yourself, head over to the website I made and give it a try: [https://textconstructor.y42.xyz/](https://textconstructor.y42.xyz/)

### Cyrillic

By far one of the easiest foreign scripts to find equivalents to Latin characters in. It should be obvious why this is in Unicode being the language of many people.
а с е о р х у — Lowercase Russian Cyrillic
a c e o p x y — Lowercase Latin
А В С Е Н І Ј К М О Р Ѕ Т Х — Uppercase Russian Cyrillic
A B C E H I J K M O P S T X — Uppercase Latin
і ј ԛ ѕ ԝ Ү Ғ Ԍ — Misc Cryllic
i j q s w Y F G — Latin

### Greek

Greek shares an overlap with Latin characters, mostly capitals. Interestingly it also has an overlap with Cyrillic which I will not get into here. 
Α Β Ε Η Ι Κ Μ Ν Ο Ρ Τ Χ Υ Ζ ο ν — Greek
A B E H I K M N O P T X Y Z o v — Latin

![A diagram for the overlap between Latin, Cyrillic, and Greek — Credit [Wikipedia](https://commons.wikimedia.org/wiki/File:Venn_diagram_showing_Greek,_Latin_and_Cyrillic_letters.svg)](1*7rGu1zS2VBeAARCn-WWHeg.png)*A diagram for the overlap between Latin, Cyrillic, and Greek — Credit [Wikipedia](https://commons.wikimedia.org/wiki/File:Venn_diagram_showing_Greek,_Latin_and_Cyrillic_letters.svg)*

### Armenian

There is not as much overlap here but there is still a few shared characters.
Լ Տ օ ո ս — Armenian
L S o n u — Latin

### Roman Numerals

A rather odd thing to include, given that they are just Latin letters. However they were added to Unicode as a way to make compatibility with older letter encoding systems easier.
Ⅰ Ⅴ Ⅹ Ⅼ Ⅽ Ⅾ Ⅿ ⅰ ⅴ ⅹ ⅼ ⅽ ⅾ ⅿ — Roman numerals
I V X L C D M i v x l c d m — Latin

### Bold/Italic/Sans-serif

These are all functionally the same as normal Latin characters but with some sort of formatting involved. Unicode says you should not use these for presentation markup, meaning you should not just substitute the bold set in to display a bolded Latin character. The sans-serif set will appear identical to the normal Latin set in a sans-serif font.
 𝐚𝐛𝐜𝐝𝐞𝐟𝐠𝐡𝐢𝐣𝐤𝐥𝐦𝐧𝐨𝐩𝐪𝐫𝐬𝐭𝐮𝐯𝐰𝐱𝐲𝐳𝐀𝐁𝐂𝐃𝐄𝐅𝐆𝐇𝐈𝐉𝐊𝐋𝐌𝐍𝐎𝐏𝐐𝐑𝐒𝐓𝐔𝐕𝐖𝐗𝐘𝐙 — Bold
 𝘢𝘣𝘤𝘥𝘦𝘧𝘨𝘩𝘪𝘫𝘬𝘭𝘮𝘯𝘰𝘱𝘲𝘳𝘴𝘵𝘶𝘷𝘸𝘹𝘺𝘻𝘈𝘉𝘊𝘋𝘌𝘍𝘎𝘏𝘐𝘑𝘒𝘓𝘔𝘕𝘖𝘗𝘘𝘙𝘚𝘛𝘜𝘝𝘞𝘟𝘠𝘡 — Italic
 𝙖𝙗𝙘𝙙𝙚𝙛𝙜𝙝𝙞𝙟𝙠𝙡𝙢𝙣𝙤𝙥𝙦𝙧𝙨𝙩𝙪𝙫𝙬𝙭𝙮𝙯𝘼𝘽𝘾𝘿𝙀𝙁𝙂𝙃𝙄𝙅𝙆𝙇𝙈𝙉𝙊𝙋𝙌𝙍𝙎𝙏𝙐𝙑𝙒𝙓𝙔𝙕 — Bold Italic
 𝖠𝖡𝖢𝖣𝖤𝖥𝖦𝖧𝖨𝖩𝖪𝖫𝖬𝖭𝖮𝖯𝖰𝖱𝖲𝖳𝖴𝖵𝖶𝖷𝖸𝖹𝖺𝖻𝖼𝖽𝖾𝖿𝗀𝗁𝗂𝗃𝗄𝗅𝗆𝗇𝗈𝗉𝗊𝗋𝗌𝗍𝗎𝗏𝗐𝗑𝗒𝗓 — Sans Serif (these also come in bold,italic, and bold/italic varients)

### Bubble

This is a very old part of Unicode though it has been updated and expanded since it first appeared. It was used for making things like lists. ® © ℗ are not actually part of this set considered instead to be unique symbols. 
ⓐⓑⓒⓓⓔⓕⓖⓗⓘⓙⓚⓛⓜⓝⓞⓟⓠⓡⓢⓣⓤⓥⓦⓧⓨⓩⒶⒷⒸⒹⒺⒻⒼⒽⒾⒿⓀⓁⓂⓃⓄⓅⓆⓇⓈⓉⓊⓋⓌⓍⓎⓏ — Circled Latin
🅐🅑🅒🅓🅔🅕🅖🅗🅘🅙🅚🅛🅜🅝🅞🅟🅠🅡🅢🅣🅤🅥🅦🅧🅨🅩🅐🅑🅒🅓🅔🅕🅖🅗🅘🅙🅚🅛🅜🅝🅞🅟🅠🅡🅢🅣🅤🅥🅦🅧🅨🅩 — Negative Circled Latin

### Small Capitals

Like normal capital letters but smaller. These are meant for IPA representations of spellings. This set is missing the x, and the f, q, and s are not available on some systems.
ᴀʙᴄᴅᴇꜰɢʜɪᴊᴋʟᴍɴᴏᴘꞯʀꜱᴛᴜᴠᴡʏᴢ — Small caps

### Superscript / Subscript

The most interesting thing here is the lack of the letter q in superscript lowercase. If this post does one thing, I hope it starts momentum to fix this oversight. Both subscript and superscript capital are missing a number of characters.
 ᴬᴮᴰᴱᴳᴴᴵᴶᴷᴸᴹᴺᴼᴾᴿᵀᵁᵂ — Superscript capital
 ᵃᵇᶜᵈᵉᶠᵍʰⁱʲᵏˡᵐⁿᵒᵖʳˢᵗᵘᵛʷˣʸᶻ — Superscript lowercase
 ₐₑₕᵢⱼₖₗₘₙₒₚᵣₛₜᵤᵥₓ — Subscript

### Upside Down Text

This one is a hodgepodge of different characters. Different people implement the idea differently. Wikipedia actually has [a chart comparing sites](https://en.wikipedia.org/wiki/Transformation_of_text#Comparison_of_algorithms) (the site I made uses the list on that page) that have done which may be close to the most ridiculous feature comparison on Wikipedia. Most of the truly flipped characters are used in IPA.
 Z⅄XMΛ∩⊥SᴚტԀONW˥ꓘſIH⅁ℲƎᗡƆᗺ∀zʎxʍʌnʇsɹbdouɯןʞɾıɥƃɟǝpɔqɐ — Upside Down Latin

### Paratherized

This is from the same block as the bubble letters above and are used for a similar purpose.
 ⒜⒝⒞⒟⒠⒡⒢⒣⒤⒥⒦⒧⒨⒩⒪⒫⒬⒭⒮⒯⒰⒱⒲⒳⒴⒵ — Paratherized Latin

### Squared

From the same block as Paratherized and Bubble letters. This block also contains the regional symbols (🇺 🇸) which are used to make the country flag emojis. The negative version of squared does not render the same for every character because of both blood types (A,B,O, and AB) and parking (the P). There exists a few combination squares as well . 🆑🆒🆓🆔🆕🆖🆗🆘🆙🆚 🆊 🆋 🆌 🆍🆎🆏
 🄰🄱🄲🄳🄴🄵🄶🄷🄸🄹🄺🄻🄼🄽🄾🄿🅀🅁🅂🅃🅄🅅🅆🅇🅈🅉 — Squared
 🅰🅱🅲🅳🅴🅵🅶🅷🅸🅹🅺🅻🅼🅽🅾🅿🆀🆁🆂🆃🆄🆅🆆🆇🆈🆉 — Negative Squared

### Blackboard Bold

This group is used for math, specifically number sets. It is not new, and is thought to have come from a 1965 textbook on complex analysis. 
 𝕒𝕓𝕔𝕕𝕖𝕗𝕘𝕙𝕚𝕛𝕜𝕝𝕞𝕟𝕠𝕡𝕢𝕣𝕤𝕥𝕦𝕧𝕨𝕩𝕪𝕫𝔸𝔹ℂ𝔻𝔼𝔽𝔾ℍ𝕀𝕁𝕂𝕃𝕄ℕ𝕆ℙℚℝ𝕊𝕋𝕌𝕍𝕎𝕏𝕐ℤ — Blackboard Bold

### Full Width

The official text of ａｅｓｔｈｅｔｉｃ. This is a holdover from early usage of Chinese on the computer. A Chinese character is closer to a square so it would take up two character slots on a terminal. To keep formatting ASCII text consistent they added full width characters which take up two normal ASCII character slots.
 ａｂｃｄｅｆｇｈｉｊｋｌｍｎｏｐｑｒｓｔｕｖｗｘｙｚＡＢＣＤＥＦＧＨＩＪＫＬＭＮＯＰＱＲＳＴＵＶＷＸＹＺ — Full Width Latin

### Script

Unicode has included another set of letters for the purpose of mathematics. This is quite fancy looking and comes in normal and bold variants. This has less support than many other items on this list, notably ChromeOS can not display it.
𝒶𝒷𝒸𝒹𝑒𝒻𝑔𝒽𝒾𝒿𝓀𝓁𝓂𝓃𝑜𝓅𝓆𝓇𝓈𝓉𝓊𝓋𝓌𝓍𝓎𝓏𝒜𝐵𝒞𝒟𝐸𝐹𝒢𝐻𝐼𝒥𝒦𝐿𝑀𝒩𝒪𝒫𝒬𝑅𝒮𝒯𝒰𝒱𝒲𝒳𝒴𝒵 — Script Latin
𝓪𝓫𝓬𝓭𝓮𝓯𝓰𝓱𝓲𝓳𝓴𝓵𝓶𝓷𝓸𝓹𝓺𝓻𝓼𝓽𝓾𝓿𝔀𝔁𝔂𝔃𝓐𝓑𝓒𝓓𝓔𝓕𝓖𝓗𝓘𝓙𝓚𝓛𝓜𝓝𝓞𝓟𝓠𝓡𝓢𝓣𝓤𝓥𝓦𝓧𝓨𝓩 — Bold Script Latin

### Fraktur

This might be one of the weirder alphabets on this list. There are 400 years of history behind the usage of it. Up until the early 20th century it was the German lettering of choice. The move away from it was a dispute worthy of a [Wikipedia article](https://en.wikipedia.org/wiki/Antiqua%E2%80%93Fraktur_dispute). It does contain the entire Latin alphabet so it is included here. 
𝔞𝔟𝔠𝔡𝔢𝔣𝔤𝔥𝔦𝔧𝔨𝔩𝔪𝔫𝔬𝔭𝔮𝔯𝔰𝔱𝔲𝔳𝔴𝔵𝔶𝔷𝔄𝔅ℭ𝔇𝔈𝔉𝔊ℌℑ𝔍𝔎𝔏𝔐𝔑𝔒𝔓𝔔ℜ𝔖𝔗𝔘𝔙𝔚𝔛𝔜ℨ — Fraktur
𝖆𝖇𝖈𝖉𝖊𝖋𝖌𝖍𝖎𝖏𝖐𝖑𝖒𝖓𝖔𝖕𝖖𝖗𝖘𝖙𝖚𝖛𝖜𝖝𝖞𝖟𝕬𝕭𝕮𝕯𝕰𝕱𝕲𝕳𝕴𝕵𝕶𝕷𝕸𝕹𝕺𝕻𝕼𝕽𝕾𝕿𝖀𝖁𝖂𝖃𝖄𝖅 — Bold Fraktur

This is not a comprehensive list. Unicode is massive and they continue to add to it every year. In the future more homoglyphs may appear. I welcome any feedback, interesting tidbits, and corrections. There will be an attempt to keep this article up to date but no guarantee. I hope this inspires you to look at the text of Unicode in a different way and make your own discoveries about the weirdness it contains.