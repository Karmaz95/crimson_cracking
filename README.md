# HOW TO USE
1. [DOWNLOAD LINK - 3.6 GB](https://drive.google.com/file/d/16Vqz8PJknN8xgv1y0d9avEtl3q0NOnF9/view?usp=sharing)
2. UNCOMPRESS
```
7z x crimson_cracking.7z
```
3. "GREP" BY LENGTH
```
awk 'length >= 8 && length <= 12' crimson_cracking.txt > crack.txt
```
4. SET THE ALIAS
```
alias wordlist="$HOME/PATH/crimson_cracking.txt"
```

# HASHCAT RULES
1. [DOWNLOAD crimson_cracking.rule]()
2. SET THE ALIAS
```
alias hashcat_rule="$HOME/PATH/crimson_cracking.rule"
```
3. USE WITH HASHCAT
```
hashcat hash.txt $wordlist -r $hashcat_rule
```

# RULES
1. [best64.rule](https://github.com/hashcat/hashcat/blob/master/rules/best64.rule)
2. [d3ad0ne.rule](https://raw.githubusercontent.com/hashcat/hashcat/master/rules/d3ad0ne.rule)
3. [OneRuleToRuleThemAll.rule](https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule)
4. [cyclone_250.rule](https://raw.githubusercontent.com/cyclone-github/rules/master/cyclone_250.rule)

# WORDLISTS @ 06.04.2022:
1. [Kaonashi - 2.35 GB](https://github.com/kaonashi-passwords/Kaonashi)
2. [CrackStation - 4.2 GB](https://crackstation.net/crackstation-wordlist-password-cracking-dictionary.htm)
3. [Seclists - 655 MB](https://github.com/danielmiessler/SecLists/tree/master/Passwords)
4. [rockyou.txt - 133 MB](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt)
5. `keymap.txt - 15 MB`
```
kwp -z full.base en-us.keymap 2-to-16-max-3-direction-changes.route > keymap.txt
```

## WORDLIST STRUCTURE
`1|2|3` => Filtered & only uniques - not sorted.
1. `1,000,000 MOST COMMON`
2. `rockyou.txt`
3. `keymap.txt`
3. Rest of the wordlists sorted by length and filtered.

### COMMANDS USED DURING CREATION => crimson_cracking.txt - 20 GB
```
### 1|2|3 => c123.txt
grep -a -P "^[\x21-\x7E]+$" 10-million-password-list-top-1000000.txt > c1.txt 
grep -a -P "^[\x21-\x7E]+$" rockyou.txt >> c1.txt
grep -a -P "^[\x21-\x7E]+$" keymap.txt >> c1.txt 
awk '!x[$0]++' c1.txt | grep -v http:// >> c123.txt
rm c1.txt;

### REST => rest.txt
cat * */* | sort -u | grep -a -P "^[\x21-\x7E]+$" >> ../temp.txt
awk '{print length, $0}' temp.txt | sort -n | cut -d " " -f2- >> rest.txt
rm temp;

### JOINING (c123.txt + rest.txt) => crimson_cracking.txt
cp c123.txt crimson_cracking.txt
grep -vaFxf c123.txt rest.txt >> crimson_cracking.txt
rm c123.txt rest.txt
```

### WORDLIST FILTRER
* Wordlist contains only printable ASCII except "\x20" - Space.
```
grep -a -P "^[\x21-\x7E]+$" crimson_cracking.txt > temp.txt
``` 

### TOTAL 3599 MB COMPRESSED
```
$7z a -t7z -m0=lzma2 -mx=9 -mmt2 crimson_cracking.7z crimson_cracking.txt
-----------------------------------------
Archive size: 3772963690 bytes (3599 MiB)
Everything is Ok
-----------------------------------------
```

#### SECLISTS INCLUDED
```
.
├── 2020-200_most_used_passwords.txt
├── 500-worst-passwords.txt
├── BiblePass
│   ├── BiblePass_part01.txt
│   ├── BiblePass_part02.txt
│   ├── BiblePass_part03.txt
│   ├── BiblePass_part04.txt
│   ├── BiblePass_part05.txt
│   ├── BiblePass_part06.txt
│   ├── BiblePass_part07.txt
│   ├── BiblePass_part08.txt
│   ├── BiblePass_part09.txt
│   ├── BiblePass_part10.txt
│   ├── BiblePass_part11.txt
│   ├── BiblePass_part12.txt
│   ├── BiblePass_part13.txt
│   ├── BiblePass_part14.txt
│   ├── BiblePass_part15.txt
│   ├── BiblePass_part16.txt
│   └── BiblePass_part17.txt
├── bt4-password.txt
├── cirt-default-passwords.txt
├── citrix.txt
├── clarkson-university-82.txt
├── Common-Credentials
│   ├── 100k-most-used-passwords-NCSC.txt
│   ├── 10k-most-common.txt
│   ├── 10-million-password-list-top-1000000.txt
│   ├── 10-million-password-list-top-100000.txt
│   ├── 10-million-password-list-top-10000.txt
│   ├── 10-million-password-list-top-1000.txt
│   ├── 10-million-password-list-top-100.txt
│   ├── 10-million-password-list-top-500.txt
│   ├── 1900-2020.txt
│   ├── 500-worst-passwords.txt
│   ├── best1050.txt
│   ├── best110.txt
│   ├── best15.txt
│   ├── common-passwords-win.txt
│   ├── medical-devices.txt
│   ├── SplashData-2014.txt
│   ├── SplashData-2015-1.txt
│   ├── SplashData-2015-2.txt
│   ├── top-20-common-SSH-passwords.txt
│   ├── top-passwords-shortlist.txt
│   └── worst-passwords-2017-top100-slashdata.txt
├── Cracked-Hashes
│   └── milw0rm-dictionary.txt
├── darkc0de.txt
├── darkweb2017-top10000.txt
├── darkweb2017-top1000.txt
├── darkweb2017-top100.txt
├── darkweb2017-top10.txt
├── days.txt
├── Default-Credentials-only_pass.txt
├── der-postillon.txt
├── dutch_common_wordlist.txt
├── dutch_passwordlist.txt
├── dutch_wordlist
├── german_misc.txt
├── Honeypot-Captures
│   ├── multiplesources-passwords-fabian-fingerle.de.txt
│   ├── python-heralding-sep2019.txt
│   ├── Sucuri-Top-Wordpress-Passwords.txt
│   └── wordpress-attacks-july2014.txt
├── Keyboard-Combinations.txt
├── Leaked-Databases
│   ├── 000webhost.txt
│   ├── adobe100.txt
│   ├── alleged-gmail-passwords.txt
│   ├── Ashley-Madison.txt
│   ├── bible.txt
│   ├── carders.cc.txt
│   ├── elitehacker.txt
│   ├── faithwriters.txt
│   ├── fortinet-2021.txt
│   ├── hak5.txt
│   ├── honeynet2.txt
│   ├── honeynet.txt
│   ├── hotmail.txt
│   ├── izmy.txt
│   ├── Lizard-Squad.txt
│   ├── md5decryptor-uk.txt
│   ├── muslimMatch.txt
│   ├── myspace.txt
│   ├── NordVPN.txt
│   ├── phpbb-cleaned-up.txt
│   ├── phpbb.txt
│   ├── porn-unknown.txt
│   ├── rockyou-05.txt
│   ├── rockyou-10.txt
│   ├── rockyou-15.txt
│   ├── rockyou-20.txt
│   ├── rockyou-25.txt
│   ├── rockyou-30.txt
│   ├── rockyou-35.txt
│   ├── rockyou-40.txt
│   ├── rockyou-45.txt
│   ├── rockyou-50.txt
│   ├── rockyou-55.txt
│   ├── rockyou-60.txt
│   ├── rockyou-65.txt
│   ├── rockyou-70.txt
│   ├── rockyou-75.txt
│   ├── singles.org.txt
│   ├── tuscl.txt
│   ├── youporn2012-raw.txt
│   └── youporn2012.txt
├── Malware
│   ├── conficker.txt
│   └── mirai-botnet.txt
├── months.txt
├── Most-Popular-Letter-Passes.txt
├── mssql-passwords-nansh0u-guardicore.txt
├── openwall.net-all.txt
├── Permutations
│   ├── 1337speak.txt
│   ├── korelogic-password.txt
│   └── password-permutations.txt
├── PHP-Magic-Hashes.txt
├── probable-v2-top12000.txt
├── probable-v2-top1575.txt
├── probable-v2-top207.txt
├── richelieu-french-top20000.txt
├── richelieu-french-top5000.txt
├── seasons.txt
├── Software
│   ├── cain-and-abel.txt
│   └── john-the-ripper.txt
├── stupid-ones-in-production.txt
├── twitter-banned.txt
├── unkown-azul.txt
├── UserPassCombo-Jay.txt
├── WiFi-WPA
│   ├── probable-v2-wpa-top447.txt
│   ├── probable-v2-wpa-top4800.txt
│   └── probable-v2-wpa-top62.txt
├── xato-net-10-million-passwords-1000000.txt
├── xato-net-10-million-passwords-100000.txt
├── xato-net-10-million-passwords-10000.txt
├── xato-net-10-million-passwords-1000.txt
├── xato-net-10-million-passwords-100.txt
├── xato-net-10-million-passwords-10.txt
├── xato-net-10-million-passwords-dup.txt
└── xato-net-10-million-passwords.txt
```
