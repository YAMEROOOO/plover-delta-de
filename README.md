# Delta's German Stenography

This is the system plugin for Delta's German stenography system, designed by [delta](https://github.com/YAMEROOOO) and implemented by Kaoffie.

Layout: 
```
F- P- N- *- ^     < -* -N -P -F ->
K- S- T- R- ^     < -R -T -S -K ->
         A- E-   -I -U
```

Steno order: `#<^SKFPTNR*AEIURNTPSKF*>`

## Contents:

- [Introduction](#introduction)
- [Rules](#rules)
- [Hidden Letters](#hidden-letters)
- [Other Combinations](#other-combinations)
- [Dictionary Formats](#dictionary-formats)
- [List of Conflicting Words](#list-of-conflicting-words)
- [Addendum](#addendum)

## Introduction:

This chapter will explain basic terms like stroke, steno order and raw steno while talking a bit about the basics of plover. More information can be found at the [Steno Glossary](https://github.com/openstenoproject/plover/wiki/Glossary). The basic idea of stenography is to write words faster than typing the letters one by one. This is accomplished by pressing multiple keys on a keyboard (which is usually a special machine, but can also be a normal NKRO-keyboard). Pressing multiple buttons at once is called a stroke and the program "Plover" translates these strokes via a dictionary into regular words. Plover is just the basic construct and what pressing each key will output will be decided by the theory which is being used. Theories are the plugins one can install as well as their corresponding dictionaries which need to be added in order for the plugin to work. For a more in-depth (and probably way better) explanation check out the YouTube playlist "[Plover And Stenography](https://www.youtube.com/playlist?list=PLatiIGGUmVcvXHf-uiScllH33-mY_Lc1_)" by [Aerick](https://github.com/aerickt) which mainly focuses on the basic English theory but is generally helpful for understanding how plover works: 
Another basic concept is steno order. The keys on a steno keyboard follow an order that usually goes from left to right (as one would write and read in most languages) and there is usually a bank of consonants on the left, a bank of vowels at the bottom and a bank of consonants on the right (a bank is referring to multiple keys, usually 4 for the vowels and 8 to 12 for the consonants). Pressing any of the keys with no added dictionary will output the raw steno of the input. Raw steno just means that the output looks like each key that was pressed in a single string of characters. The raw steno for pressing `T` in the left bank would look like this: `T-`, while the raw steno for pressing `T` in the right bank would look like this: `-T`. The "-" at the beginning or the end of the "T" just indicates from which bank the T came from. Similarly, pressing `S` and `T` in the left bank would be `ST-` and pressing both in the right bank would be `-ST`. If a `-` is needed as well as the order of the letters depends on the theory used. For example, one theory may have the keys `S` and `T` in either bank, but if some other theory would have the `S` only in the right bank and not in the left, then there is no need for the `-` before the `S` because there is noting like an `S-`. Also, if there are keys from the middle bank pressed (like trying to write "sos") there is again no need to differentiate, so it would look like `SOS` (and not `S-O-S`). If more than one key is pressed in either bank, the order of these keys is determined by the steno order of the corresponding theory, so if the steno order is `STAOEUTS` (with the banks `[ST]`, `[AOEU]` and `[TS]`, where `ST` are the keys in the left bank, `AOEU` are the keys in the middle bank and `TS` are the keys in the right bank) then "stost" would get the output `STOTS` instead of `STOST`. It is not important to understand all of this fully, but it is important to note that letters with a `-` afterwards correspond to keys in the left bank and letters with a `-` in front correspond to keys in the right bank. Also, these previously mentioned strokes are a set of these uppercase letters which will always follow the steno order of the theory used. Two strokes are separated by a `/` and it is not possible for a letter to appear two times in either part of the Stroke (because all the keys in a stroke are pressed simultaneously and thus one can't click a key two times) so something like `SSOTT` is not a possible stroke.
An example with this theory would be this:
(Reminder: These instructions are for this German theory and thus my further examples will revolve around this theory.)
`^F*AR>/<TNIU/^PNERT>` which would translate to "Hallo Welt" (Hello World).
The steno layout and order for my theory are the following and can also be seen in the image below:
![keys](https://user-images.githubusercontent.com/71076286/196929655-74b2221c-be4d-4d86-bf3f-631639927a7b.png)

Layout:
```
F- P- N- *- ^     < -* -N -P -F ->
K- S- T- R- ^     < -R -T -S -K ->
         A- E-   -I -U
```

Steno order:
`SKFPTNR*AEIURNTPSKF*>`



## Rules:

The system is orthographic, this means, that all words are written as one would spell them. Try for example writing the word "kauft". It will be written by pressing the `K-` key, the `A` and the `U` key, as well as the keys `-F` and `-T`. Other words like "reis", "stern" or "pfau" work in the same way. On the other hand, words like "clown" will need letters that are not present on the keyboard. Further explanation for this will follow in the next chapter. Right now though, this chapter will only talk about the basics of this plugin. Each word has to be written in syllables, and those syllables have to have vowels in the middle and optionally consonants on the sides. There can't be syllables such as "Safe" (which is an English word the Germans use respectively) because there are vowels in the middle AND at the end of the syllable (or to be more precise one stroke has three parts, an initial part with only consonants from the left bank, a middle part with only vowels from the middle bank, and a final part with only consonants from the right bank). So "Safe" would have to be split into 2 Syllables in order to be written. Pressing `SA` and the `FE` would be the way, though trying this out will output "sa fe" instead of "Safe". Here the `^` and `<` keys are needed, also called "capitalize-key" or "c-key" and "glue-(together)-key" or "g-key". These (as the name suggests) capitalize a syllable or "glue" one syllable to the previous one (that is the reason why the arrows point in these directions). To capitalize a syllable, one simply needs to press the c-key together with the other keys of the stroke. In the example of "Safe" one would press `^SA` to get "Sa". Now to glue the second syllable to the first one simply presses the g-key together with the syllable that needs to be attached to the previously written part. Doing this together will output "Safe" (by inputting `^SA/<FE`).
The reason this is so different from most other stenography systems (that usually operate on words rather than syllables that need to be "glued" together manually) is due to the nature of the German language. In German one can combine a lot of words (especially nouns) and get a perfectly fine German word. Like "Müll" ("trash") and "Eimer" ("bucket") gives "Mülleimer" ("trashcan"). So far so good, but in German this keeps on going further: "Plastikmülleimerdeckel" ("plastic trashcan lid") is one German word and there are a lot of those really long ones.

## Hidden letters:

Some letters like "d" and "m" can't be found on the keys. To access these, a special key labeled `*` is needed. Pressing `*` and `T` on one side (either right or left) will output a "d". This works for most letters, and the "counterparts" to each letter are in the following table:

| output | input |
| :---: | :---: |
| h | -F* |
| g | -K* |
| b | -P* |
| z | -S* |
| m | -N* |
| d | -T* |


(These can of course be written on both sides, for the sake of simplicity this will only cover the left side if it is different from the right side)

The only letter which does not have a counterpart here is the `R` key. The reason behind this and the further uses of this key (as well as it’s hidden counterpart) will be explained later on.
As one can see, the counterparts are usually the "softer" versions of the letters (`T` and "d", `K` and "g" as well as `P` and "b"). The reason `S` is in the layout instead of being the "soft" counterpart of "z" is just because the letter "s" is used more frequently in German language (this is also true for the other letters). Others like `N` and "m" are just counterparts out of obvious reasons. `F` and "h" just have their reason to be counterparts due to there being no German words with an "f" and an "h" together at either the end or the start of a syllable and therefore one won't run into issues of needing to press `F` and `F*`(h) on the same side in the same stroke. As a mnemonic, one can think about the `F` being a really "soft" sound and the "h" being even "softer" (they also look pretty alike).
But there are still letters missing like c, j, l, o, q, v, w, x, y and ß as well as the so called "umlaute" ä, ö and ü. Due to most of these being sparely used in the German language, they are hidden behind combinations of letters. Some of them are intuitive, whilst others aren’t. This theory is build to be as intuitive as possible, but especially here the randomness starts to take place. There is no need to worry if this gets a little confusing at first, it is just a matter of memorization and practice. The missing letters are in the following table:


| output | input | explanation |
| :---: | :---: | :---: |
| c | -PK |This combination is purely random |
| j | *I | "i" looks kind of like "j" so "j" is the counterpart of `I` |
| l | TN- | This combination is random |
| l | -R> | This is random aswell and will be explained in the next chapter |
| o | IU | One vowel hat to go and "o" was the least common, also "o" usually never appears together with either "i" or "u" |
| q | -NPK | Words that start with "q" usually sound like "kw" (which is `KNP`) |
| v | -NPF | Similar to the "q" but here it is just because the "v" looks like a "w" (or at least half a "w") and is used similar to "f" |
| w | -NP | This combination is purely random |
| x | -RPSK | The "x" in a word usually sounds like a "ks" (though `R` and `P` are random) |
| y | EU* | "y" in the middle of a word sounds like "ü" (which also can be written as "ue"). The `*` is there to clarify the difference between "y" and "ue". |
| ä | AEI | To differetiate "ae" and "ä" an `I` was added (because German has no "Ï") |
| ö | AIU | Since "o" is `IU` just doing `EIU` would be the same as "ü" so it had to be another combination with `IU` (the only one being left was `AIU`) |
| ü | EIU | Same as "ä" (and also the reason why "y" can’t be `EIU`) |
| ß |
(Here the letter "l" has two input methods, depending on the side the l is needed)

## Other combinations:

There are some other issues one can run into while trying to write certain words like "bann", "zahm" or "siel". These require other combinations as well as the `>` key (which acts as another extra key similar to the `*` and is not to be confused with the g-key). Usually the `>` key is used to double a letter like the "n" in "bann". To write "bann" one simply strokes `P*AN>`. The same works with most of the other letters except for "r" and "l" which, due to "l" being `-R>` on the right side, have other combinations which will be listed below. Also, if a vowel needs to be doubled like in "see" or "tee" one simply types the vowel along with the `>` and the right `*` (so "see" would be `SE*>` and "tee" would be `TE*>`). The `>` key can also be used if the `*` needs to be doubled, like in the word "zahm" which would be `S*ANF**` (rearranged from `S*AF*N*`) but needs to be stroked as `S*ANF*>`. As seen in the above chapter, the `>` key is also used to write the letter "l" on the right side. Furthermore, the `>` key can be used to distinguish "chs" from "sch" as in "Lachs" (`^TNASKF>`) and "lasch" (`TNASKF`). As seen there, the combination for writing an "sch" is `SKF` (which makes sense due to `K` being similar to "c" and "h" being the counterpart to `F`). Therefore, the "ch" alone with no "s" in the same part of the stroke is `KF`. The only time when a `S` is pressed together with a `KF` in the same bank but does not form an "sch" or "chs" is when this `S` is used to stroke a "z" as in "schluchtz" (`SKFTNUTSKF*`). This is really important due to words like "nachts" and "nascht" being stroked the same way. For the "ck" another combination of letters is needed, which can also be seen below.
Another problem occurs with the word "siel" which requires the same inputs as "seil" (`SEIR>`). Thus, every "ie" needs to be stroked as `AE` instead of `EI` (a pony for this are english words like "beamer", where the "ea" sounds like a german "ie" as in "biegen").
Here are all the combinations from this chapter:


| output | input |
| :---: | :---: |
| ff | -F> |
| pp | -P> |
| bb | -P*> |
| nn | -N> |
| mm | -N*> |
| gg | -K*> |
| ss | -S> |
| zz | -S*> |
| tt | -T*> |
| rr | -RNP |
| ll | -RNP> |
| aa | A*> |
| ee | E*> |
| oo | IU*> |
| sch | -SKF |
| chs | -SKF> |
| ch | -KF |
| ck | -RPK |
| ie | AE |


## Dictionary Formats

This system supports all regular dictionary formats, such as json. It also comes with support for two additional formats: **DSD**, and **DWD**. In both formats, keys within the left bank (`SKFPTNR*`), vowel bank (`AEIU`), and right banks (`-RNTPSKF*>`) can be arranged in any order within the bank itself.


### DSD Dictionaries

```json
{
"STE.NUI": "steno",
"STE.NUI.K*RAF": "stenograf",
"STE.NUI.K*RA.PF*EA": "stenographie"
}
```

### DWD Dictionaries

Use `\,` to escape commas.

```
steno, STE.NUI
stenograf, STE.NUI.K*RAF
stenographie, STE.NUI.K*RA.PF*EA
```

## List of Conflicting Words

Some words will still create issues because they have the same stroke as some other word. To differentiate them, the first working option in the following list should be used:

#### Option 1:
**Example:** hemd=`F*ENT*>`=hemmt ; **Solution:** hem?=`F*ENT*>` ; hemd=`F*E_*NT.*T` ; hemmt=`F*E_*NT.*NT`

Replace the part of the translation where the disambiguation happened with a "?" to indicate to the user that further input is required. Then in the second stroke, the user can input the missing letters that got replaced by the "?" (without the need to add the g-key).

#### Option 2:
**Example:** samt=`SANT*`=sand ; **Solution:** sant?=`SANT*` ; samt=`SAN*T.*N` ; sand=`SANT*.*T`

Replace the part of the translation where the disambiguation occurs with the unchanged form of the characters (in this case the counterpart "m" will change back to "n" or the counterpart "d" will change back to "t") and add a "?" at the end of the translation to indicate the user that further input is required. Then in the second stroke, the user can input the counterpart of the letter which needs to be changed (without the need to add the g-key).

#### Option 3:
**Example:** psi=`SPI`=spi ; **Solution:** psi=`SPI*` ; spi=`SPI`

Add a `-*` (or a `->` if `-*` is already used) in the raw steno of the syllable that is not in steno order (or is the one which uses hidden letters). If this creates an issue with another entry, add the `*-` (or a `->` if `*-` is already used) in the raw steno of the syllable that is not in steno order (or is the one which uses hidden letters).
Note: This Option requires memorization of this disambiguation.

The conflicting words are listed here (in .dwd):

| Option | Conflicts | |
| :---: | :---: | :---: |
| 2 | samt, `SAN*T.*N` | sand, `SANT*.*T` |
| 2 | brems, `PR*E*NS.*N` | brenz, `PR*E*NS.*S` |
| 3 | psi, `SPI*` | spi, `SPI` |
| 1 | hemd, `F*E_*NT.*T` | hemmt, `F*E_*NT.*NT` |

If more disambiguations are found, they will be added here.

## Addendum

First and foremost, I would like to thank [Kathy](https://github.com/Kaoffie) for creating this plugin for me. Without her constant help and quick implementation of changes to the plugin, I wouldn't have been able to create this theory in the first place. Furthermore, I want to thank the people on the plover discord that helped me out weren't annoyed of my constant questionings regarding steno topics. Also, I want to say something regarding this theory and myself. This has been a passion project of mine since 2021 and was (except for the plugin) all done by me. I changed the theory multiple times as well as the dictionary and ended up translating all the (at the time of writing this around 5500) syllables by myself, so if there are any mistakes in there I'm sorry. That said, the best place to reach out to me would be my discord (YAMERO#3100) or via the [plover discord server](https://discord.gg/f47aYcst9B) where I will be talking about new improvements and updates from now on. I appreciate everyone who is willing to help me out on this project, even if it's just finding some mistakes or missing syllables and sending them to me. Be aware though that I worked on this theory a long time now, and thought about the layout and other improvement ideas dozens of times and most of them will have some issues that will create more problems than before, so I can confidently say that this is the best theory I can craft and there won't be any major changes to it, so please respect that.

**Last but not least, have fun writing!**
