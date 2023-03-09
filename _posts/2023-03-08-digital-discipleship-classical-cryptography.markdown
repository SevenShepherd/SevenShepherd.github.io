---
layout: post
title: "🔑 Exercises In Digital Discipleship, Puzzle II: Classical Cryptography"
date: 2023-03-08 2:15:00 -0500
categories: cryptography
published: true
---

<!-- <style>
.cogitotable {
    background-color: #f8f9fa;
    color: #202122;
    margin: 1em 0;
    border: 1px solid #a2a9b1;
    border-collapse: collapse;
}
.cogitotable > * > tr > th, .cogitotable > * > tr > td {
    border: 1px solid #a2a9b1;
    padding: 0.2em 0.4em;
}
</style> -->

<!-- I thought this would be a fun article to write, seeing as how the recent move across the country has been extraordinarily time consuming and has prevented me from writing for some time. Classical cryptography was always a very interesting topic for me when I was growing up, and I spent my youth learning how to code on topics like these. This article will be a good introductory programming corse for the curious. -->

This article provides a series of **easy** exercises originally written 11/10/2022 on a separate blog, and repurposed for the digital discipleship program created by SevenShepherd. If you are new or haven't gone through our fundamentals course, you may want to check that out before attempting this exercise.

This article encrypts a famous movie quote from the movie "The Princess Bride" in dozens of ways using classical cryptography. This was written for fun. This ministry does not condone violence or vengeance.

## ⚠️ Under Construction

<span style="font-style:italic;font-size:2em;">I. Monoalphabetic Substitution Ciphers</span>

<!-- ```py
print(*map(lambda l: ord(l), s))
# 69 110 99 114 121 112 116 32 109 101 33

print(*map(lambda l: ord(l) - (65 if l.isupper() else 97), s))
# 4 13 2 17 24 15 19 -65 12 4 -64

print(*map(lambda l: ((ord(l) - (65 if l.isupper() else 97)) + 13) % 26, s))
# 17 0 15 4 11 2 6 0 25 17 1

print(*map(lambda l: (((ord(l) - (65 if l.isupper() else 97)) + 13) % 26) + (65 if l.isupper() else 97), s))

print(*map(lambda l: (((ord(l) - (65 if l.isupper() else 97)) + 13) % 26 + (65 if l.isupper() else 97)), s))
# 82 97 112 101 108 99 103 97 122 114 98

print(*map(lambda l: chr(((ord(l) - (65 if l.isupper() else 97)) + 13) % 26 + (65 if l.isupper() else 97)), s))
# R a p e l c g a z r b

print(''.join(map(lambda l: chr(((ord(l) - (65 if l.isupper() else 97)) + 13) % 26 + (65 if l.isupper() else 97)), s)))
# Rapelcgazrb

print(''.join(map(lambda l: chr(((ord(l) - (65 if l.isupper() else 97)) + 13) % 26 + (65 if l.isupper() else 97)) if l.isalpha() else l, s)))
# Rapelcg zr!
``` -->

The `ClassicalCryptography` class below just supplies some getters, setters, deleters and error checking around the shift instance variable / constant.

```py
class ClassicalCryptography:
    def __init__(self, shift=13):
        self.constraints(shift)
        self.__shift = shift
        
    @property
    def shift(self):
        return self.__shift
    
    @staticmethod
    def constraints(value: int) -> None:
        if not isinstance(value, int):
            raise TypeError("Must be an integer!")
            
        if not 0 <= value <= 26:
            raise ValueError("Shift must be 0-26.")
    
    @shift.setter
    def shift(self, value):
        self.constraints(value)
        self.__shift = value
    
    @shift.deleter
    def shift(self):
        raise TypeError("Cannot delete shift.")
```

```py
from ciphers.baseclass import ClassicalCryptography

class MonoalphabeticSubstitutionCipher(ClassicalCryptography):
    def __init__(self, *args):
        super().__init__(*args)
```

This is the class method we will be using to implement the other substitution ciphers when we're not expanding them to explain their inner details.

```py
def succinct(self, msg, decrypt=False, rotation=None):
    """
    Monoalphabetic Substitution Cipher (one-liner /w list comprehension)
    """
    if rotation: self.shift = rotation

    # case handler
    case  = lambda l: ord('A') if l.isupper() else ord('a')

    # right shift, encryption & decryption, characters only (one-liner)
    return ''.join([(chr(((ord(l) - case(l)) + ((26 - self.shift) if decrypt else self.shift)) % 26 + case(l)) if l.isalpha() else l) for l in msg])
```

The code snippet below is an expanded version of the one liner presented above. This example is given so you can see the process that is taking place clearly.

```py
def expanded(self, msg, decrypt=False, rotation=None):
    """
    E_n(x) = (x+n) % 26
    """
    if rotation: self.shift = rotation
            
    # case handler
    case  = lambda l: ord('A') if l.isupper() else ord('a')
    
    res = []
    # iterate through each character in string
    for character in msg:

        # encrypt alphabetic characters only
        if character.isalpha():

            # transform letters into numbers
            # retrieve integer representing unicode code point
            # subtract correct case sensitive decimal representation
            temp = ord(character) - case(character)

            # handle decryption logic
            if decrypt is True:
                # identical to original formula in else
                # reversed to achieve opposite affect
                temp = (temp + (26 - self.shift)) % 26
            else:
                # this is where the actual modular arithmetic 
                # from the main formula takes place, now that
                # we have the characters transformed properly
                temp = (temp + self.shift) % 26

            # restore unicode representation of current integer
            temp = temp + case(character)

            # apply inverse of ord for ciphertext character
            temp = chr(temp)
            res.append(temp)
        else:
            res.append(character)
            
    return ''.join(res)
```

```py
from ciphers.monoalphabetic import MonoalphabeticSubstitutionCipher

def main():
    plaintext = "My name is Inigo Montoya. You killed my father. Prepare to die."

    monoalphabetic = MonoalphabeticSubstitutionCipher()

    for i in range(1,25+1):
        succinct = monoalphabetic.succinct(plaintext, rotation=i)
        print(f"ROT{i:>02}: {succinct}")

    expanded = monoalphabetic.expanded(plaintext, rotation=13)
    print(f"secret message: {expanded}")

if __name__ == "__main__":
    main()
```

```
ROT01: Nz obnf jt Jojhp Npoupzb. Zpv ljmmfe nz gbuifs. Qsfqbsf up ejf.
ROT02: Oa pcog ku Kpkiq Oqpvqac. Aqw mknngf oa hcvjgt. Rtgrctg vq fkg.
ROT03: Pb qdph lv Lqljr Prqwrbd. Brx nloohg pb idwkhu. Suhsduh wr glh.
ROT04: Qc reqi mw Mrmks Qsrxsce. Csy omppih qc jexliv. Tvitevi xs hmi.
ROT05: Rd sfrj nx Nsnlt Rtsytdf. Dtz pnqqji rd kfymjw. Uwjufwj yt inj.
ROT06: Se tgsk oy Otomu Sutzueg. Eua qorrkj se lgznkx. Vxkvgxk zu jok.
ROT07: Tf uhtl pz Pupnv Tvuavfh. Fvb rpsslk tf mhaoly. Wylwhyl av kpl.
ROT08: Ug vium qa Qvqow Uwvbwgi. Gwc sqttml ug nibpmz. Xzmxizm bw lqm.
ROT09: Vh wjvn rb Rwrpx Vxwcxhj. Hxd truunm vh ojcqna. Yanyjan cx mrn.
ROT10: Wi xkwo sc Sxsqy Wyxdyik. Iye usvvon wi pkdrob. Zbozkbo dy nso.
ROT11: Xj ylxp td Tytrz Xzyezjl. Jzf vtwwpo xj qlespc. Acpalcp ez otp.
ROT12: Yk zmyq ue Uzusa Yazfakm. Kag wuxxqp yk rmftqd. Bdqbmdq fa puq.
ROT13: Zl anzr vf Vavtb Zbagbln. Lbh xvyyrq zl sngure. Cercner gb qvr.
ROT14: Am boas wg Wbwuc Acbhcmo. Mci ywzzsr am tohvsf. Dfsdofs hc rws.
ROT15: Bn cpbt xh Xcxvd Bdcidnp. Ndj zxaats bn upiwtg. Egtepgt id sxt.
ROT16: Co dqcu yi Ydywe Cedjeoq. Oek aybbut co vqjxuh. Fhufqhu je tyu.
ROT17: Dp erdv zj Zezxf Dfekfpr. Pfl bzccvu dp wrkyvi. Givgriv kf uzv.
ROT18: Eq fsew ak Afayg Egflgqs. Qgm caddwv eq xslzwj. Hjwhsjw lg vaw.
ROT19: Fr gtfx bl Bgbzh Fhgmhrt. Rhn dbeexw fr ytmaxk. Ikxitkx mh wbx.
ROT20: Gs hugy cm Chcai Gihnisu. Sio ecffyx gs zunbyl. Jlyjuly ni xcy.
ROT21: Ht ivhz dn Didbj Hjiojtv. Tjp fdggzy ht avoczm. Kmzkvmz oj ydz.
ROT22: Iu jwia eo Ejeck Ikjpkuw. Ukq gehhaz iu bwpdan. Lnalwna pk zea.
ROT23: Jv kxjb fp Fkfdl Jlkqlvx. Vlr hfiiba jv cxqebo. Mobmxob ql afb.
ROT24: Kw lykc gq Glgem Kmlrmwy. Wms igjjcb kw dyrfcp. Npcnypc rm bgc.
ROT25: Lx mzld hr Hmhfn Lnmsnxz. Xnt jhkkdc lx ezsgdq. Oqdozqd sn chd.

secret message: Zl anzr vf Vavtb Zbagbln. Lbh xvyyrq zl sngure. Cercner gb qvr.
```

<span style="font-style:italic;font-size:1.5em;">❍ Affine Cipher</span>

```py
from ciphers.baseclass import ClassicalCryptography

class AffineCipher(ClassicalCryptography):
    def __init__(self, *args):
        super().__init__(*args)
```
```py
@staticmethod
def succinct(msg, a, b, decrypt=False):
    """Affine Cipher (one-liner /w list comprehension)"""
    case = lambda l: ord('A') if l.isupper() else ord('a')
    
    # right shift, encryption & decryption, characters only (one-liner)
    return ''.join([(chr( ((pow(a, -1, 26) * ((ord(l) - case(l)) - b)) if decrypt else (a * (ord(l) - case(l)) + b)) % 26 + case(l)) if l.isalpha() else l) for l in msg])
```
```py
@staticmethod
def expanded(msg, a, b, decrypt=False):
    """
    E(x) = (ax + b) % m
    """
    case = lambda l: ord('A') if l.isupper() else ord('a')

    res = []
    # iterate through each character in string
    for character in msg:
        
        # encrypt alphabetic characters only
        if character.isalpha():

            # transform letters into numbers
            temp = ord(character) - case(character)

            if decrypt is False:
                # apply E_n(x) = (x+n) % 26
                temp = (a * temp + b) % 26
            else:
                # apply a**-1(x-b) % 26
                temp = (pow(a, -1, 26) * (temp - b)) % 26

            # restore unicode representation of current integer
            temp = temp + case(character)

            # apply inverse of ord for ciphertext character
            temp = chr(temp)
            res.append(temp)
            
        else:
            res.append(character)
        
    return ''.join(res)
```

```py
from ciphers.affine import AffineCipher

def main():

    plaintext = "My name is Inigo Montoya. You killed my father. Prepare to die."
    affine    = AffineCipher()

    ciphertext1 = affine.succinct(plaintext, 7, 8)
    ciphertext2 = affine.expanded(plaintext, 7, 8)
    print(f"ciphertext: {ciphertext1}")
    print(f"ciphertext: {ciphertext2}")

    plaintext1 = affine.succinct(ciphertext1, 7, 8, True)
    plaintext2 = affine.expanded(ciphertext2, 7, 8, True)
    print(f"plaintext: {plaintext1}")
    print(f"plaintext: {plaintext2}")

if __name__ == "__main__":
    main()
```

```
ciphertext: Ou viok me Mvmyc Ocvlcui. Ucs amhhkd ou rilfkx. Jxkjixk lc dmk.
ciphertext: Ou viok me Mvmyc Ocvlcui. Ucs amhhkd ou rilfkx. Jxkjixk lc dmk.

plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
```
<span style="font-style:italic;font-size:1.5em;">❍ Atbash</span>

These methods belong to the same `AffineCipher` class in the previous section.

```py
def atbash(self, msg):
    """Atbash is an affine cipher with a = b = 25"""
    return self.succinct(msg, 25, 25)
```

```py
@staticmethod
def atbash_static(msg):
    """Atbash is an affine cipher with a = b = 25"""
    case = lambda l: ord('A') if l.isupper() else ord('a')
    
    # right shift, encryption, characters only (one-liner)
    return ''.join([(chr((25 * (ord(l) - case(l)) + 25) % 26 + case(l)) if l.isalpha() else l) for l in msg])
```

```py
from ciphers.affine import AffineCipher

def main():

    plaintext = "My name is Inigo Montoya. You killed my father. Prepare to die."
    affine    = AffineCipher()

    ciphertext1 = affine.succinct(plaintext, 25, 25)
    ciphertext2 = affine.expanded(plaintext, 25, 25)
    ciphertext3 = affine.atbash(plaintext)
    ciphertext4 = affine.atbash_static(plaintext)
    print(f"ciphertext: {ciphertext1}")
    print(f"ciphertext: {ciphertext2}")
    print(f"ciphertext: {ciphertext3}")
    print(f"ciphertext: {ciphertext4}")

    plaintext1 = affine.succinct(ciphertext1, 25, 25)
    plaintext2 = affine.expanded(ciphertext2, 25, 25)
    plaintext3 = affine.atbash(ciphertext3)
    plaintext4 = affine.atbash_static(ciphertext4)
    print(f"plaintext: {plaintext1}")
    print(f"plaintext: {plaintext2}")
    print(f"plaintext: {plaintext3}")
    print(f"plaintext: {plaintext4}")

if __name__ == "__main__":
    main()
```

```
ciphertext: Nb mznv rh Rmrtl Nlmglbz. Blf proovw nb uzgsvi. Kivkziv gl wrv.
ciphertext: Nb mznv rh Rmrtl Nlmglbz. Blf proovw nb uzgsvi. Kivkziv gl wrv.
ciphertext: Nb mznv rh Rmrtl Nlmglbz. Blf proovw nb uzgsvi. Kivkziv gl wrv.
ciphertext: Nb mznv rh Rmrtl Nlmglbz. Blf proovw nb uzgsvi. Kivkziv gl wrv.

plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
```

<!-- <table class="cogitotable"><tbody><tr style="vertical-align:top"><th scope="row">  Plain</th><td>  A</td><td>B</td><td>C</td><td>D</td><td>E</td><td>F</td><td>G</td><td>H</td><td>I</td><td>J</td><td>K</td><td>L</td><td>M</td><td>N</td><td>O</td><td>P</td><td>Q</td><td>R</td><td>S</td><td>T</td><td>U</td><td>V</td><td>W</td><td>X</td><td>Y</td><td>Z</td></tr><tr style="vertical-align:top"><th scope="row">  Cipher</th><td> Z</td><td>Y</td><td>X</td><td>W</td><td>V</td><td>U</td><td>T</td><td>S</td><td>R</td><td>Q</td><td>P</td><td>O</td><td>N</td><td>M</td><td>L</td><td>K</td><td>J</td><td>I</td><td>H</td><td>G</td><td>F</td><td>E</td><td>D</td><td>C</td><td>B</td><td>A</td></tr></tbody></table> -->

<!-- <table class="cogitotable"><tbody><tr style="text-align:center;"><th scope="row"></th><td><span style="font-size:85%;">Aleph</span></td><td><span style="font-size:85%;">Bet</span></td><td><span style="font-size:85%;">Gimel</span></td><td><span style="font-size:85%;">Daleth</span></td><td><span style="font-size:85%;">Heh</span></td><td><span style="font-size:85%;">Vav</span></td><td><span style="font-size:85%;">Zayin</span></td><td><span style="font-size:85%;">Het</span></td><td><span style="font-size:85%;">Tet</span></td><td><span style="font-size:85%;">Yodh</span></td><td><span style="font-size:85%;">Kaph</span></td><td><span style="font-size:85%;">Lamed</span></td><td><span style="font-size:85%;">Mem</span></td><td><span style="font-size:85%;">Nun</span></td><td><span style="font-size:85%;">Samech</span></td><td><span style="font-size:85%;">Ayin</span></td><td><span style="font-size:85%;">Peh</span></td><td><span style="font-size:85%;">Tzady</span></td><td><span style="font-size:85%;">Koof</span></td><td><span style="font-size:85%;">Reish</span></td><td><span style="font-size:85%;">Shin</span></td><td><span style="font-size:85%;">Taw</span></td></tr><tr style="text-align:center;"><th scope="row">Plain</th><td>א</td><td>ב</td><td>ג</td><td>ד</td><td>ה</td><td>ו</td><td>ז</td><td>ח</td><td>ט</td><td>י</td><td>כ</td><td>ל</td><td>מ</td><td>נ</td><td>ס</td><td>ע</td><td>פ</td><td>צ</td><td>ק</td><td>ר</td><td>ש</td><td>ת</td></tr><tr style="text-align:center;"><th scope="row"></th><td><span style="font-size:85%;">Taw</span></td><td><span style="font-size:85%;">Shin</span></td><td><span style="font-size:85%;">Reish</span></td><td><span style="font-size:85%;">Koof</span></td><td><span style="font-size:85%;">Tzady</span></td><td><span style="font-size:85%;">Peh</span></td><td><span style="font-size:85%;">Ayin</span></td><td><span style="font-size:85%;">Samech</span></td><td><span style="font-size:85%;">Nun</span></td><td><span style="font-size:85%;">Mem</span></td><td><span style="font-size:85%;">Lamed</span></td><td><span style="font-size:85%;">Kaph</span></td><td><span style="font-size:85%;">Yodh</span></td><td><span style="font-size:85%;">Tet</span></td><td><span style="font-size:85%;">Het</span></td><td><span style="font-size:85%;">Zayin</span></td><td><span style="font-size:85%;">Vav</span></td><td><span style="font-size:85%;">Heh</span></td><td><span style="font-size:85%;">Daleth</span></td><td><span style="font-size:85%;">Gimel</span></td><td><span style="font-size:85%;">Bet</span></td><td><span style="font-size:85%;">Aleph</span></td></tr><tr style="text-align:center;"><th scope="row">Cipher</th><td>ת</td><td>ש</td><td>ר</td><td>ק</td><td>צ</td><td>פ</td><td>ע</td><td>ס</td><td>נ</td><td>מ</td><td>ל</td><td>כ</td><td>י</td><td>ט</td><td>ח</td><td>ז</td><td>ו</td><td>ה</td><td>ד</td><td>ג</td><td>ב</td><td>א</td></tr></tbody></table> -->

<!-- <span style="font-style:italic;font-size:1.5em;">❍ Autokey</span> -->

<span style="font-style:italic;font-size:1.5em;">❍ Caesar Cipher</span>

The *Caesar cipher* is a monoalphabetic substitution cipher. The transformation is represented by a cipher alphabet which is the plain alphabet with a rotatation or shift of **3 to the left** or **23 to the right**. The method is named after Julius Caesar, who used it in his private correspondence. Since our program operates with only right shifts, we use 23 to encrypt and 3 to decrypt.

<!-- <table class="cogitotable"><tbody><tr style="vertical-align:top"><th scope="row">  Plain</th><td>  A</td><td>B</td><td>C</td><td>D</td><td>E</td><td>F</td><td>G</td><td>H</td><td>I</td><td>J</td><td>K</td><td>L</td><td>M</td><td>N</td><td>O</td><td>P</td><td>Q</td><td>R</td><td>S</td><td>T</td><td>U</td><td>V</td><td>W</td><td>X</td><td>Y</td><td>Z</td></tr><tr style="vertical-align:top"><th scope="row">  Cipher</th><td> X</td><td>Y</td><td>Z</td><td>A</td><td>B</td><td>C</td><td>D</td><td>E</td><td>F</td><td>G</td><td>H</td><td>I</td><td>J</td><td>K</td><td>L</td><td>M</td><td>N</td><td>O</td><td>P</td><td>Q</td><td>R</td><td>S</td><td>T</td><td>U</td><td>V</td><td>W</td></tr></tbody></table> -->

> "If he had anything confidential to say, he wrote it in cipher, that is, by so changing the order of the letters of the alphabet, that not a word could be made out. If anyone wishes to decipher these, and get at their meaning, he must substitute the fourth letter of the alphabet, namely D, for A, and so with the others." &mdash; Suetonius, Life of Julius Caesar 56

<!-- ```py
def monoalphabetic(self, msg, decrypt=False):

    # case handler
    case = lambda l: ord('A') if l.isupper() else ord('a')
    
    # encryption / decryption one-liner
    return ''.join([(chr(((ord(l) - case(l)) + ((26 - self.shift)%26 if decrypt else self.shift)) % 26 + case(l)) if l.isalpha() else l) for l in msg])
``` -->

```py
plaintext  = "abcdefghijklmnopqrstuvwxyz"
cipherObj  = ClassicalCryptography(23)
ciphertext = cipherObj.monoalphabetic(plaintext)
print(f"secret message: {ciphertext}")
```
```
xyzabcdefghijklmnopqrstuvw
```

```py
@staticmethod
def caesar_cipher(msg, decrypt=False):
    """Caesar cipher"""

    # case handler
    case = lambda l: ord('A') if l.isupper() else ord('a')
    
    # right shift, encryption & decryption, characters only (one-liner)
    return ''.join([(chr(((ord(l) - case(l)) + (3 if decrypt else 23)) % 26 + case(l)) if l.isalpha() else l) for l in msg])
```

<!-- ```py
# examples

# right shift encryption (one-liner)
''.join([chr(((ord(l) - case(l)) + 23) % 26 + case(l)) for l in msg])

# left shift encryption (one-liner)
''.join([chr(((ord(l) - case(l)) - 3) % 26 + case(l)) for l in msg])

# right shift decryption (one-liner)
''.join([chr(((ord(l) - case(l)) + 3) % 26 + case(l)) for l in msg])

# left shift decryption (one-liner)
''.join([chr(((ord(l) - case(l)) - 23) % 26 + case(l)) for l in msg])
``` -->

<!-- Let's take a closer look at what's happening. For the sake of simplicity and example, the following code snippet does not implement error handling, the handling of punctuation, or the decryption logic. An example containing all of these things can be found in the monoalphabetic method's source code at the top of section I. Monoalphabetic Substitution Ciphers. -->

```py
@staticmethod
def caesar_cipher_expanded(msg, decrypt=False):
    """
    E_n(x) = (x+23) % 26
    E_n(x) = (x-3)  % 26
    """
    case = lambda l: ord('A') if l.isupper() else ord('a')
    
    res  = []
    # iterate through each character in string
    for character in msg:
        
        # encrypt alphabetic characters only
        if character.isalpha():
        
            # transform letters into numbers
            temp = ord(character) - case(character)

            # handle decryption logic
            if decrypt is True:
                # apply E_n(x) = (x+3) % 26
                temp = (temp + 3) % 26
            else:
                # apply E_n(x) = (x+23) % 26
                temp = (temp + 23) % 26

            # restore unicode representation of current integer
            temp = temp + case(character)

            # apply inverse of ord for ciphertext character
            temp = chr(temp)
            res.append(temp)
            
        else:
            res.append(character)
        
    return ''.join(res)
```

```py
@staticmethod
def caesar_translate(msg):
    # make translation table
    trans = str.maketrans(
        "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ", 
        "xyzabcdefghijklmnopqrstuvwXYZABCDEFGHIJKLMNOPQRSTUVW"
    )
    
    # translate
    return msg.translate(trans)
```


<!-- <span style="font-style:italic;font-size:1.5em;">❍ Chaocipher</span> -->

<!-- <span style="font-style:italic;font-size:1.5em;">❍ Pigpen</span> -->

<span style="font-style:italic;font-size:1.5em;">❍ ROT13</span>

```py
plaintext  = "abcdefghijklmnopqrstuvwxyz"
cipherObj  = ClassicalCryptography(13)
ciphertext = cipherObj.monoalphabetic(plaintext)
print(f"secret message: {ciphertext}")
```
```
nopqrstuvwxyzabcdefghijklm
```

```py
@staticmethod
def rot13(msg):
    # case handler
    case = lambda l: ord('A') if l.isupper() else ord('a')
    
    # right shift, encryption & decryption, characters only (one-liner)
    return ''.join([(chr(((ord(l) - case(l)) + 13) % 26 + case(l)) if l.isalpha() else l) for l in msg])
```

```py
@staticmethod
def rot13_expanded(msg):
    """
    E_n(x) = (x+13) % 26
    """
    case = lambda l: ord('A') if l.isupper() else ord('a')
    
    res  = []
    # iterate through each character in string
    for character in msg:
        
        # encrypt alphabetic characters only
        if character.isalpha():
        
            # transform letters into numbers
            temp = ord(character) - case(character)

            # handles encryption as well as decryption
            temp = (temp + 13) % 26

            # restore unicode representation of current integer
            temp = temp + case(character)

            # apply inverse of ord for ciphertext character
            temp = chr(temp)
            res.append(temp)
            
        else:
            res.append(character)
        
    return ''.join(res)
```

```py
@staticmethod
def rot13_translate(msg):
    # make translation table
    trans = str.maketrans(
        "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ", 
        "nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM"
    )
    
    # translate
    return msg.translate(trans)
```

<span style="font-style:italic;font-size:2em;">II. Polyalphabetic Substitution Ciphers</span>

<span style="font-style:italic;font-size:1.5em;">❍ Beaufort Cipher</span>

```py
@staticmethod
def beaufort_cipher_Expanded(msg, key, decrypt=False):
    """
    C_i = E_k(M_i) = (K_i - M_i) % 26
    M_i = D_k(C_i) = (K_i - C_i) % 26
    """
            
    # case handler
    case     = lambda l: ord('A') if l.isupper() else ord('a')
    cyclekey = cycle(key)
    result   = []
    # iterate through each character in string
    for character in msg:

        # encrypt alphabetic characters only
        if character.isalpha():
            kcharacter = next(cyclekey)

            # transform letters into numbers
            temp  = ord(character)  - case(character)
            tempk = ord(kcharacter) - case(kcharacter)

            # handle decryption logic
            if not decrypt:
                # C_i = E_k(M_i) = (K_i - M_i) % 26
                temp = (tempk - temp) % 26
            else:
                # M_i = D_k(C_i) = (K_i - C_i) % 26
                temp = (tempk - temp) % 26

            # restore unicode representation of current integer
            temp = temp + case(character)

            # apply inverse of ord for ciphertext character
            temp = chr(temp)
            result.append(temp)
            
        else:
            result.append(character)
            
    return ''.join(result)
```

<!-- <span style="font-style:italic;font-size:1.5em;">❍ Alberti</span> -->

<!-- <span style="font-style:italic;font-size:1.5em;">❍ Enigma</span> -->

<!-- <span style="font-style:italic;font-size:1.5em;">❍ Trithemius</span> -->

<span style="font-style:italic;font-size:1.5em;">❍ Vigenère Cipher</span>

```py
from ciphers.baseclass import ClassicalCryptography
from itertools         import cycle

class VigenereCipher(ClassicalCryptography):
    def __init__(self, *args):
        super().__init__(*args)
```

```py
@staticmethod
def succinct(msg, key, decrypt=False):
    """
    Vigenère Polyalphabetic Substitution Cipher (two-liner :D)
    Walrus operator works in Python 3.8+
    """

    case  = lambda l: ord('A') if l.isupper() else ord('a')
    wheel = cycle(key)

    if not decrypt:
        # encryption only, characters only (one-liner)
        return ''.join([(chr(((ord(c)-case(c)) + (ord(k := next(wheel))-case(k))) % 26 + case(c)) if c.isalpha() else c) for c in msg])
    else:
        # decryption only, characters only (one-liner)
        return ''.join([(chr(((ord(c)-case(c)) - (ord(k := next(wheel))-case(k))) % 26 + case(c)) if c.isalpha() else c) for c in msg])
```

Modular arithmetic 

```py
@staticmethod
def expanded(msg, key, decrypt=False):
    """
    C_i = E_k(M_i) = (M_i + K_i) % 26
    M_i = D_k(C_i) = (C_i - K_i) % 26
    """

    # case handler
    case     = lambda l: ord('A') if l.isupper() else ord('a')
    cyclekey = cycle(key)
    result   = []
    # iterate through each character in string
    for character in msg:

        # encrypt alphabetic characters only
        if character.isalpha():
            # don't cycle on non-characters
            kcharacter = next(cyclekey)

            # transform letters into numbers
            # retrieve integer representing unicode code point
            # subtract correct case sensitive decimal representation
            temp  = ord(character)  - case(character)
            tempk = ord(kcharacter) - case(kcharacter)

            # handle decryption logic
            if not decrypt:
                # C_i = E_k(M_i) = (M_i + K_i) % 26
                temp = (temp + tempk) % 26
            else:
                # M_i = D_k(C_i) = (C_i - K_i) % 26
                temp = (temp - tempk) % 26

            # restore unicode representation of current integer
            temp += case(character)

            # apply inverse of ord for ciphertext character
            temp = chr(temp)
            result.append(temp)

        else:
            result.append(character)

    return ''.join(result)
```

```py
from ciphers.vigenere import VigenereCipher

def main():

    plaintext = "My name is Inigo Montoya. You killed my father. Prepare to die."
    vigenere  = VigenereCipher()

    ciphertext1 = vigenere.succinct(plaintext, "DreadPirateRoberts")
    ciphertext2 = vigenere.expanded(plaintext, "DreadPirateRoberts")
    print(f"ciphertext: {ciphertext1}")
    print(f"ciphertext: {ciphertext2}")
    
    plaintext1 = vigenere.succinct(ciphertext1, "DreadPirateRoberts", True)
    plaintext2 = vigenere.expanded(ciphertext2, "DreadPirateRoberts", True)
    print(f"plaintext: {plaintext1}")
    print(f"plaintext: {plaintext2}")

if __name__ == "__main__":
    main()
```
```
ciphertext: Pp rapt qj Igmxc Nsemgbr. Cox zqclxh dm gekawu. Gvespzv th hzs.
ciphertext: Pp rapt qj Igmxc Nsemgbr. Cox zqclxh dm gekawu. Gvespzv th hzs.

plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
```

<span style="font-style:italic;font-size:1.5em;">❍ Vigenère Cipher Beaufort Variant</span>

```py
@staticmethod
def beaufort(msg, key, decrypt=False):
    """
    C_i = E_k(M_i) = (M_i - K_i) % 26
    M_i = D_k(C_i) = (C_i + K_i) % 26
    """

    # case handler
    case     = lambda l: ord('A') if l.isupper() else ord('a')
    cyclekey = cycle(key)
    result = []
    # iterate through each character in string
    for character in msg:

        # encrypt alphabetic characters only
        if character.isalpha():
            kcharacter = next(cyclekey)

            # transform letters into numbers
            # retrieve integer representing unicode code point
            # subtract correct case sensitive decimal representation
            temp  = ord(character)  - case(character)
            tempk = ord(kcharacter) - case(kcharacter)

            # handle decryption logic
            if not decrypt:
                # M_i = D_k(C_i) = (C_i - K_i) % 26
                temp = (temp - tempk) % 26
            else:
                # C_i = E_k(M_i) = (M_i + K_i) % 26
                temp = (temp + tempk) % 26

            # restore unicode representation of current integer
            temp = temp + case(character)

            # apply inverse of ord for ciphertext character
            temp = chr(temp)
            result.append(temp)

        else:
            result.append(character)

    return ''.join(result)
```

```py
from ciphers.vigenere import VigenereCipher

def main():

    plaintext = "My name is Inigo Montoya. You killed my father. Prepare to die."
    vigenere  = VigenereCipher()

    ciphertext1 = vigenere.beaufort(plaintext, "DreadPirateRoberts")
    ciphertext2 = vigenere.succinct(plaintext, "DreadPirateRoberts", True)
    ciphertext3 = vigenere.expanded(plaintext, "DreadPirateRoberts", True)
    print(f"ciphertext: {ciphertext1}")
    print(f"ciphertext: {ciphertext2}")
    print(f"ciphertext: {ciphertext3}")

    plaintext1 = vigenere.beaufort(ciphertext1, "DreadPirateRoberts", True)
    plaintext2 = vigenere.succinct(ciphertext2, "DreadPirateRoberts")
    plaintext3 = vigenere.expanded(ciphertext3, "DreadPirateRoberts")
    print(f"plaintext: {plaintext1}")
    print(f"plaintext: {plaintext2}")
    print(f"plaintext: {plaintext3}")

if __name__ == "__main__":
    main()
```
```
ciphertext: Jh jajp ab Iuepa Lkwawvj. Uor vaullz vk ewcomo. Ynemljn tv zrq.
ciphertext: Jh jajp ab Iuepa Lkwawvj. Uor vaullz vk ewcomo. Ynemljn tv zrq.
ciphertext: Jh jajp ab Iuepa Lkwawvj. Uor vaullz vk ewcomo. Ynemljn tv zrq.

plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
plaintext: My name is Inigo Montoya. You killed my father. Prepare to die.
```

<span style="font-style:italic;font-size:1.5em;">❍ Running key</span>

<span style="font-style:italic;font-size:2em;">III. Transposition Ciphers</span>

<span style="font-style:italic;font-size:1.5em;">❍ Columnar</span>

<span style="font-style:italic;font-size:1.5em;">❍ Double</span>

<!-- <span style="font-style:italic;font-size:1.5em;">❍ Myszkowski</span> -->

<span style="font-style:italic;font-size:1.5em;">❍ Rail fence</span>

<span style="font-style:italic;font-size:1.5em;">❍ Route</span>

<span style="font-style:italic;font-size:2em;">IV. Steganographic Message Encoding</span>

<span style="font-style:italic;font-size:1.5em;">❍ Baconian Cipher</span>

```py
@staticmethod
def baconian_cipher_26(msg):

    # encode only, characters only (one-liner)
    return ' '.join([(dict(((c,f"{i:05b}".translate(str.maketrans("01", "AB"))) for i,c in enumerate(ascii_lowercase)))[c.lower()] if c.isalpha() else '') for c in msg])
```

```py
@staticmethod
def baconian_cipher_26_expanded(msg):

    def char_map():
        trans = str.maketrans("01", "AB")
        
        for i, c in enumerate(ascii_lowercase):
            binary = f"{i:05b}"
            yield (c,binary.translate(trans))
        
    result = []
    for character in msg:
        if character.isalpha():
            result.append(dict(char_map())[character.lower()])
        else:
            result.append(character)
    
    return ' '.join(result)
```

<span style="font-style:italic;font-size:2em;">V. One-Time-Pad</span>
