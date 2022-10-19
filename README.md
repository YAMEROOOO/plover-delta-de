# Delta's German Stenography

This is the system plugin for Delta's German stenography system, designed by [delta](https://github.com/YAMEROOOO) and implemented by Kaoffie.

Layout: 
```
F- P- N- *- ^        < -* -N -P -F ->
K- S- T- R- ^        < -R -T -S -K ->
            A- E-   -I -U
```

Steno order: `#<^SKFPTNR*AEIURNTPSKF*>`

## Dictionary Formats

This system supports all regular dictionary formats, such as json. It also comes with support for two additional formats: **DSD**, and **DWD**. In both formats, keys within the left bank (`SKFPTNR*`), vowel bank (`EAIU`), and right banks (`-RNPSKFTe_*`) can be arranged in any order within the bank itself, and the final `-e` key is written as a capital `E`.


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

## Introduction:
This chapter will explain basic terms like stroke, steno order and the basics of plovers raw steno. More information can be found at the [Steno Glossary](https://github.com/openstenoproject/plover/wiki/Glossary). The basic idea of stenography is to write words faster than typing the letters one by one. This is accomplished by pressing multiple keys on a keyboard (which is usually a special machine but can also be a normal NKRO-keyboard). Pressing multiple buttons at once is called a stroke and the programm „Plover“ translates these strokes via a dictionary into regular words. Plover is just the basic construct and what pressing each key will output will be decided by the theory which is being used. Theories are the plugins one can install as well as their corresponding dictionaries which need to be added in order for the plugin to work. For a more indepth (and probably way better) explanation check out the YouTube playlist „[Plover And Stenography](https://www.youtube.com/playlist?list=PLatiIGGUmVcvXHf-uiScllH33-mY_Lc1_)“ by [Aerick](https://github.com/aerickt) which mainly focusses on the bacis english theory but is generally helpful for understanding how plover works: 
Another basic concept is steno order. The keys on a steno keyboard follow an order that usually goes from left to right (as one would write and read in most languages) and there is usually a block of consonants on the left, a block of vowels at the botton and a block of consonants on the right. Some keys can be on both the left and the right side and are then differeciated by a „-„ either at the beginning or at the end of the letter (or of the letters if they are both on one side). A „T“ on the left side would look like this: T-, while a T on the right side would look like this: -T. Similarly pressing S and T on the left side would be ST- and pressing both on the right side would be -ST. If a – is needed as well as the order of the letters depends on the theory used. for example has the Keys S and T on either side, but if some other theory would not have the S only on the right side and not on the left there is no need for the „-„ before the S because there is noting like an „S-„. Also if there are vowel keys pressed (like trying to write SOS) there is no need to differenciate aswell so it would look like SOS (and not S-O-S). If more than one key is pressed in either area, the order of these Keys is determined my the steno order of the corresponding theory, so if the Order is STAOEUTS (with blocks [ST][AOEU][TS], where „ST“ are the keys on the left side, „AOEU“ are the keys in the lower middle and „TS“ are the keys on the right side) then stost would get the output STOTS instead of STOST. It is not important to understand all of this fully but it it important to not that letters with a „-„ afterwards correspond to keys on the left and letters with a „-„ in front correspond to keys on the right. Also these Previously mentioned Strokes are a set of these uppercase letters which will always follow the steno order of the theory used. Two strokes are seperated by a „/“ and it is not possible for a letter to appear two times in either block of the Stroke (because all the keys in a stroke are pressed simultaneously and thus one can not click a key two times) so something like SSOTT is not a possible stroke.
An example with my theory would be this:
(Reminder: These instructions are for this german theory and thus my further examples will revolve around this theory.)
^F*AR>/<TNIU/^PNERT> which would translate to „Hallo Welt“ (Hello World).
The steno order for my theory is the following:
SKFPTNR*AEIURNTPSKF*> and can also be seen in the image below:
`-T`. 

## Rules:
The system ist orthographical, this means, that all words are written as one would spell them. Try for example writing the word "kauft". It will be written by pressing the left K key, the A and the U key, as well as the right FT key. This is simple right? Other words like „reis“, „stern“ or „pfau“ work in the same way. For words like „clown“ for example you will need letters that are not present on the keyboard. Further explanation for this will follow in the next chapter. Right now though i want to talk more about how this plugin works. Each word has to be written in syllables and those syllables have to have vowels in the middle and optionally consonants on the sides. There can't be words such as "Safe" (which is an english word the germans use respectively) because there are vowels at the end of the syllable (or to be more precise one stroke can only contain consonants, then vowels and then consonants again. So "Safe" would have to be split into 2 Syllables in order to be written. pressing SA and the FE would be the way, though if you press these now if will output "sa fe" instead of "Safe". Here you need the "^" and "<" keys, also called "capitalize-key" or "c-key" and "glue-(together)-key" or "g-key". These (as the name suggests) capitalize a syllable or glue one syllable to the previous one (that is the reason why the arrows point in these directions). To capitalize a syllable simply press the c-key together with the other key of your stroke. In the example of „Safe“ you would press ^SA to get „Sa“. Now to glue the second syllable tot he first you simply press the g-key together with the syllable you want to glue to the previosly written part. Doing this together will give you „Safe“ (by inputting ^SA/<FE).
The reason this is so different from most other stenography systems is due to the nature of the german language. In german you can combine a lot of words (especially nouns) and get a perfectly fine german word. Like „Müll“ („trash“) and „Eimer“ („bin“) gives „Mülleimer“ („trashcan“). So far so good but in german you can keep doing this: „Plastikmülleimerdeckel“ („plastic trashcan lid“) is one german word and there are a lot of those really long ones. Furthermore 

## Hidden letters:
Some letters like D and M can not be found on the keys. To access these you will need the special key labled *. Try pressing * and T on one side (either right or left) and you will see a „d“ appear on your text. This works for most Letters and the counterparts to each letter are in the following table:

h	-F*
g	-K*
b	-P*
z	-S*
m	-N*
d	-T*

(These can of course be written on both sides, for simplicity sake this will only cover the left side if it is different from the right side)
The only letter which does not have a counter part here is the R key. The reason behind this and the further uses of this key (as well as it’s hidden counterpart) will be explained leter on.
As one can see, the counterparts are usually the „softer“ versions of the letters (T and D, K and G as well as P and B). the reason S is on the keys instead of being the „soft“ counterpart of z is just because the letter S is used more frequently in german language (this is also true for the other letters). Others like M and N are just counterparts out of obvious reasons. F and H just have their reason to be counterparts due to there being no german words with an F and an H together at either the end or the start of a syllable and therefore one wont run into issues of needing to press F and F*(H) on the same side in the same stroke. As a mnemonic you can think about the F being a really „soft“ sound and the H being even „softer“ (They also look pretty alike).
But there are still letters missing like C, J, L, O, Q, V, W, X, Y, and ß as well as the so called „umlaute“ Ä, Ö and Ü. Due to most of these being sparely used in the german language they are hidden behind combinations of letters. Some of them are intuitive whilst others aren’t. I tried to make this theory as intuitive as possible but especially here the randomness starts to take place. There is no need worry if this get’s a little confusing at first, it is just a matter of memorization and practice. The missing Letters are in the following table:



c	-PK	This combination is purely random 
j	*I	I looks kind of like J so J is the counterpart of I
l	TN-	This combination is random
l	-R>	This is random aswell and will be explained in the next chapter
o	IU	One vowel hat to go and O was the least common, also O usually never appears together with either I or U
q	-NPK	Words that start with Q ususally sound like KW (which is KNP)
v	-NPF	Similar to the Q but here it is just because the V looks like a W (or at least half a W) and is used similar to F
w	-NP	This combination is purely random
x	-RPSK	The X in a word usually sounds like a KS (though R and P are random)
y	EU*	Y in the middle of a word sounds like Ü (which also can be written as UE). The * is there to clarify the difference between Y and UE.
ä	AEI	To differeciate AE and Ä an I was added (because german has no Ï)
ö	AIU	Since O is IU just doing EIU would be the same as Ü so it had to be another combination with IU (the only one being left was AIU)
ü	EIU	Same as Ä (and also the reason why Y can’t be EIU)
ß		
 
(Here the letter l has two input methods, depending on the side you need the l)
(((This sums up this chapter on all the letters and in the next chapter we will be talking about some other combinations.)))
Other combinations:
There are some other issues one can run into while trying to write certain words like „bann“, „zahm“ or „siel“. These require other combinations as well as the > key (which acts as another extra key similar to the * and is not to be confused with the g-key). Usually the >-key is there to double a letter like the N in bann. You to write bann you simply stroke P*AN>. The same works with most of the other letters except for R and L which, due to L being R> on the right side, have other combinations which will be listed below. Also if a vowel needs to be doubled like in „see“ or „tee“ you simply type the vowel along with the > and the right * (so see would be SE*> and tee would be TE*>). The >-key can also be used if the * needs to be doubled like in the word zahm which would be S*ANF** (rearranged from S*AF*N*) but needs to be stroked as S*ANF*>. As seen in the above chapter the >-key is also used to write the letter l on the right side. Furthermore the > can be used to distinguish „chs“ from „sch“ as in Lachs (^TNASKF>) and lasch (TNASKF). As seen there the combination for writing an „sch“ is SKF (which makes sense due to K being similar to C and H being the counterpart to F). Therefore the „ch“ alone with no S in the stroke is KF. The only time where a S is used together with a KF but does not form an „sch“ or „chs“ is when this S is used to stroke a „z“ as in schluchtz (SKFTNUTSKF*). This is really important due to to words like nachts and nascht being stroked the same way. „ck“ on the other hand can’t be written that easily so instead it needs another combination of letters which can also be seen below.
Another problem occurs with the word siel which requires the same inputs as seil (SEIR>). This requires every „ie“ to be stroked as AE instead of EI (a pony for this are english words like „beamer“, where the „ea“ sounds like a german „ie“ as in „biegen“).
Here are all of the combinations from this chapter:
 
ff	-F>
pp	-P>
bb	-P*>
nn	-N>
mm	-N*>
gg	-K*>
ss	-S>
zz	-S*>
tt	-T*>
rr	-RNP
ll	-RNP>
aa	A*>
ee	E*>
oo	IU*>
sch	-SKF
chs	-SKF>
ch	-KF
ck	-RPK
ie	AE

of course you can ask me why i did things the way i did them, just dont expect me to change things (i thought about them a lot and there are (((as far as i know))) no other possibilities to do it better).
