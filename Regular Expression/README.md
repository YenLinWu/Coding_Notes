# Regular Expression  

## Contents
* [CREATE TABLE](#CREATE_TABLE)
* [SELECT](#SELECT)
* [SELECT DISTINCT](#SELECT_DISTINCT)
* [UNION](#UNION)
* [INSERT INTO](#INSERT_INTO) 
* [UPDATE](#UPDATE)
* [DELETE](#DELETE)
* [JOIN](#JOIN)
* [WHERE](#WHERE)
* [ORDER BY](#ORDER_BY)
* [GROUP BY](#GROUP_BY)
* [BETWEEN](#BETWEEN)
* [IN](#IN)
* [LIKE](#LIKE)
* [ANY](#ANY)
* [ALL](#ALL)
* [CASE](#CASE)

| Meta Character | Description |
|:----:|----|
|.|Period matches any single character except a line break.|
|[ ]|Character class. Matches any character contained between the square brackets.|
|[^ ]|Negated character class. Matches any character that is not contained between the square brackets|
|*|Matches 0 or more repetitions of the preceding symbol.|
|+|Matches 1 or more repetitions of the preceding symbol.|
|?|Makes the preceding symbol optional.|
|{n,m}|Braces. Matches at least "n" but not more than "m" repetitions of the preceding symbol.|
|(xyz)|Character group. Matches the characters xyz in that exact order.|
|&#124;|Alternation. Matches either the characters before or the characters after the symbol.|
|&#92;|Escapes the next character. This allows you to match reserved characters <code>[ ] ( ) { } . * + ? ^ $ \ &#124;</code>|
|^|Matches the beginning of the input.|
|$|Matches the end of the input.|

Back to [Contents](#Contents)
<br>
