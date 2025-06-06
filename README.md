Todo:
- Create all the specialized wordlists
- Create details program
- Add links to specific wordlists

# Password Cracking Wordlists README
This contains the wordlists I use in my password cracking setup with John the Ripper.

## Contents
* [Wordlists](#wordlists)
    * [English Dictionaries](#english-dictionaries)
    * [Other Language Dictionaries](#other-language-dictionaries)
    * [Specialized Wordlists](#specialized-wordlists)
    * [Other](#other)
* [Rules](#rules)
* [How to Use](#how-to-use)
* [Individualized Wordlists](#individualized-wordlists)

## Wordlists
### English Dictionaries
* engDictionary.txt (75 KB)
    * This dictionary contains the 10,000 most common English words used. Most English speakers have a working vocabulary of about 20,000 words and know 40,000 words, so this is just a portion of that. 
* engDictionaryEdited.txt (35 KB)
    * This dictionary is an edited version of the engDictionary.txt list with 6167 words. There are no capital letters, spaces, or symbols, and all words are between 3 and 7 letters long. Common password base words have been added to this list also.
* engDictionaryLarge.txt (4.7 MB)
    * This dictionary contains all the words in the English language (466,545 words). It is meant to be much more extensive than engDictionary.txt. 
* engDictionaryLargeEdited.txt (2.4 MB)
    * This dictionary is an edited version of the engDictionaryLarge.txt list with 268,333 words. There are no capital letters, spaces, or symbols, and all words are between 6 and 10 letters long. Common password base words have been added to this list also.
* doubleDictionary.txt (??? GB)

### Other Language Dictionaries
* Other languages
    * https://github.com/xajkep/wordlists/tree/master/dictionaries
    * https://github.com/miglen/bulgarian-wordlists
    * https://github.com/baclv/vietnamese-password-dicts
    * https://github.com/sharsi1/russkiwlst
    * https://github.com/hypn/custom-wordlists
    * https://github.com/1337z/wordlists
    * https://github.com/clem9669/wordlists
    * https://github.com/Blkzer0/Wordlists
    * https://github.com/napolux/paroleitaliane
    * https://github.com/kkrypt0nn/Wordlists
    * https://github.com/serapath/bip39wordlist

### Specialized Wordlists
Only passwords between 6 and 10 characters long are included. Most words that also appear in any English dictionaries were removed from these wordlists. All symbols, capital letters, and spaces have been removed.

* starTrek.txt (4 KB)
    * This wordlist contains 369 commonly used words, major characters, nicknames, slang, etc.
* starWars.txt (3 KB)
    * This wordlist contains 323 major characters, creatures, alien races, worlds, objects, slang, quotes, vehicles, weapons, etc.
* harryPotter.txt (4 KB)
    * This wordlist contains 375 major characters, spells, creatures, book titles, places, items, quidditch positions, slang, etc.
* usCanadaLocations.txt (89 KB)
    * This wordlist contains 9,734 cities, counties, provinces, and states of the United States and Canada.
* gameOfThrones.txt (2 KB)
    * This wordlist contains 132 words, phrases, places, and people from the Game of Thrones universe. 
* anime.txt (315 KB)
    * This wordlist contains 38,439 characters, places, and words from an animanga wordlist contained [here](https://github.com/ryuuganime/animanga-wordlist). Note - when I get a Japanese dictionary, I will remove all words from this wordlist that are already in that one. Also, words of length 5 *have* been included in this wordlist.
* internationalLocations.txt (124 KB)
    * This wordlist contains 15,154 international cities, countries, islands, continents, and other various locations. Only words between 5 and 10 characters have been included in this list. All entries that are already in the English dictionary and usCanadaLocations.txt have been removed from this list. 
* doctorWho.txt
* lds.txt
* music.txt
* vehicles.txt
* marvel.txt
* outdoors.txt
* sports.txt
* videoGames.txt
* boardGames.txt
* americanHistory.txt
* lordOfTheRings.txt
* memes.txt
* celebrities.txt
    * https://github.com/Cheroxx/custom-wordlists
* popularplaces.txt (national parks, landmarks, amusement parks, stores, etc.)
* techTerms.txt
    * https://github.com/hypn/custom-wordlists/blob/master/dev-terms.txt
    * https://github.com/wirzka/wordlists/tree/master/dirb
    * https://github.com/wirzka/wordlists/tree/master/metaploit
    * https://github.com/kkrypt0nn/Wordlists
* Most common dog names - https://github.com/Cheroxx/custom-wordlists/blob/master/pets

### Other
* crackStation.txt (14.6 GB)
    * This is a list from [crackstation.net](https://crackstation.net/crackstation-wordlist-password-cracking-dictionary.htm) that contains every wordlist, dictionary, and password database leak that the creator could find, along with every word in Wikipedia from 2010 and books from Project Gutenberg.

## Rules
I created a few of my own custom rules that can be put into the john.conf file in /etc/john. These rules, when used in a `john` command, are automatically applied to each word. 

* numbersLong - this rule adds numbers either before a word or after a word. The numbers go from 0-9999. This is for both capitalized versions and uncapitalized versions of the word, plus it runs just the capital word with no numbers also. This multiplies the number of possible passwords by 44,441, since each word will have 44,441 variations of it run. 
* numbersShort - this rule adds numbers either before a word or after a word. The numbers go from 0-99. This is for both capitalized versions and uncapitalized versions of the word, plus it runs just the capital word with no numbers also. This multiplies the number of possible passwords by 441, since each word will have 441 variations of it run.
* capital - this rule adds each word with the first letter capitalized, which doubles the number of possible passwords tried. 
* symbolsLong - This includes a very long list of possible password variations that include common symbols and digits. This multiplies the number of possible passwords by 3112. 
* symbolsShort - This includes a short list of possible password variations with common symbols. It's mainly exclamation marks and some @ symbols. This multiplies the number of possible passwords by 12. 
* leet - these basic 1337 (leet) rules have been copied from one of the JTR preset rules options and separated. Please note that there are several possibilities for leet rules, so I may make an extended version of this at some time.

## How to Use
* Make sure John the Ripper and perl are installed
* Edit the john.conf file and insert the rules found in johnrules.rul
* To produce crackStation.txt
    * Download crackStation.txt from [crackstation.net](https://crackstation.net/crackstation-wordlist-password-cracking-dictionary.htm)
    * Depending on download and file read/write speeds, this can take approximately 20 minutes
* To produce engDoubleDictionary.txt
* Other useful commands for cleaning/preparing wordlists:
    * `perl -lne 'length()>5 && length()<11 && print' file1.txt > file2.txt;` - this perl command removes all lines that do NOT have a length of 6-10.
    * `tr '[:upper:]' '[:lower:]' < file1.txt > file2.txt` - this Linux command turns all uppercase characters to lowercase characters
    * `grep -v '[[:upper:]]' file1.txt > file2.txt` - this Linux command removes all lines with uppercase characters
    * `sort file1.txt > file2.txt; uniq file2.txt > file3.txt` - these commands sort all the lines alphabetically, then removes all duplicate lines
    * `tr -cd '[:alnum:]\n ' < file1.txt > file2.txt` - this removes all non-alphanumeric characters (except newlines and spaces), which can be helpful when dealing with symbols that aren't available on a normal keyboard
    * `comm -23 <(sort file1.txt) <(sort file2.txt) > file1.txt` - this command keeps everything that's unique in file1.txt (or everything in file1.txt that's NOT in file2.txt), this can eliminate duplicates across wordlists

## Individualized Wordlists
The point of list of details is to find words that aren't on my wordlist, or uncommon words/phrases

First name:
Middle names:
Last names:
Nicknames: 
Street number:
Street name:
Apt #:
City:
State:
Country:
Old house street numbers:
Old house street names:
Old house apt #s:
Old house cities:
Old house states:
Old house countries:
Phone #s:
Parent/grandparent/spouse/children phone #s:
Emails:
Current/old school names:
Current/old school mascots:
Company/old company names:
Company/old company positions:
Favorite sports teams:
Favorite books:
Favorite movies:
Favorite TV show:
Favorite colors:
Favorite foods:
Others:
Hobbies:
Languages spoken:
Birthday:
Birth city:
Birth state:
Birth country:
Partner first names:
Partner middle names:
Partner last names:
Partner birthday:
Partner nickname:
Anniversary:
Parents first names:
Parents middle names:
Parents last names:
Children first names:
Children middle names:
Children last names:
Children nicknames:
Children birthdates:
Pet names:
Old/current usernames:
Other info:
