# Password Generator (`pw`)

Generate random passwords in a hopefully secure manner. By default, `pw` generates
completely random passwords. To support insecure systems, you can specify required
character groups. To support humans, you can generate pronounceable passwords. To
break things, you can generate passwords from a large unicode character set.

# Usage

```
usage: pw [-h] [--number NUMBER] [--pronounceable] [--lower] [--minimum-lower NUMBER] [--upper]
          [--minimum-upper NUMBER] [--digits] [--minimum-digits NUMBER] [--special]
          [--minimum-special NUMBER] [--characters CHARACTERS] [--unicode] [--build-markov FILE]
          [length]

Generate random passwords in a hopefully secure manner.

positional arguments:
  length                Length of password

optional arguments:
  -h, --help            show this help message and exit
  --number NUMBER, -n NUMBER
                        Number of passwords to generate
  --pronounceable, -p   Create human pronounceable passwords
  --lower, -l           Use lower case letters
  --minimum-lower NUMBER, -L NUMBER
                        Minimum number of lowercase characters required
  --upper, -u           Use upper case letters
  --minimum-upper NUMBER, -U NUMBER
                        Minimum number of upper characters required
  --digits, -d          Use digits
  --minimum-digits NUMBER, -D NUMBER
                        Minimum number of digit characters required
  --special, -s         Use special characters (punctuation)
  --minimum-special NUMBER, -S NUMBER
                        Minimum number of special characters required
  --characters CHARACTERS, -c CHARACTERS
                        Specify individual characters
  --unicode, -z         Use a large unicode character set
  --build-markov FILE, -b FILE
                        Build a markov chain using the words in FILE.
```

# Features

## Character groups

You can specify the minimum number of lower, upper, digit, or special characters. You can also include only certain groups, or even specify a list of approved characters. If you specify `--lower`, `--upper`, `--digits`, `--special`, or `--characters` then passwords will only contain those characters.

## Pronounceable passwords

Generate pronounceable passwords using Markov chains.

The Markov engine is trained using the `words.txt` file in the repository. However, that file is not required to operate `pw` because `pw` is a self-updating program, making it significantly closer to sentience than your average password generator. I am going to go out on a limb here and make the claim that `pw` uses Artificial Intelligence.

To make `pw` smarter, get a list of words in a file. The words should be separated by a newline. Then run:

```
pw -b words.txt
```

It will parse them and store the resultant Markov data inside the `pw` script file itself so that you don't have to copy around multiple files.

### Examples

Require at least one lowercase, uppercase, digit, and special character:
```
> pw -luds
NLHh'nfSgV1@U;{q
```

Only digits:

```
> pw -d
4261729641542628
```

Only certain characters:

```
> pw -c u
uuuuuuuuuuuuuuuu
```

Make a short password:

```
> pw 1
r
```

Make a long password:

```
> pw 300
rM_DK'^kf3@^pg]ja!\p3nrV$TUhq*.x(GCZr)Qz%>hup-T!y@@6KW#]f](]b!R6w'C{!x>sEeYtQ*yY~).xI7-|-Y(\Lk;c4COr-jdyM=/D@w{|jmmHeFNL:JqXWgQ$J&N@sb0.$w9e('j^R:x"qcv7Y{-DQ!pmwi%UoT,F)WTL-Q._L-1U&".jr)J[g/n"8|-Vv3/S1Yr&zG}S"xv1?!iC_(?T.$tjX!d:<B|elY^UIe,xfnR+fldNiE}V33uYT3}>yAE3kR,){x+vJsP|vHnDZKH6'N\hV@}Boh.4)O!?
```

Require 6 digits and 3 special characters:

```
> pw -D 6 -S 3
SK374-{Y5y2Wty3-
```

6 high unicode range passwords:

```
> pw -zn 6
཯୳↥ѐḒृ₮⇉O2ޝ☀แݾ࢙ቦ
♝⇧ᑙᘒଥȨണቁᢔዅ✀ᳫܡ὿࿾ᇤ
ຟക᭫ᢱᾞẠᬩ❷਴∴ᾘ✋Ṋឧ৹ཡ
ᮀ૲ᓴಙᳫaᯍ┐╝ᒨ℁ڛ܂ฃఎ֞
ࡰ⎪⍜✐␯͊ಪǱ⊯ᯒ◬ყӽѦଁ࿼
○ܠᕲ༖੄ᨱʤᧁΩ፭⁤နཟϳ഑⎬
```

5 vaguely human pronounceable passwords:

```
> pw -pn 5
eidbloneseandune
rintrsscaphatind
onionsalatrytoki
pharocagnossshyd
dititesindeseses
```
