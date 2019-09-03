# Masks

In same modules you can specify a symbol masks how source. This build from standard charsets:

* ?l — all letters of english alphabet, lower case 
* ?u — all letters of english alphabet, upper case 
* ?d — all digits Charset 

?s not using because this symbols not using in domain or directory names.

You can specify two types of masks.

Simple mask with specify every symbol. For example «?l?l?d?d» - it mean all phrases with length 4 symbols and where first two symbols - all letters of english alphabet in lower case, and second two symbols — all digits. 

Mask with length range. For example «?l?d,1,4» - all phrases with length from 1 to 4 symbols, contains all letters of english alphabet in lower case and all digits.

