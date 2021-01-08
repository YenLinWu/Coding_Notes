# Regular Expression  

## Contents
* [Meta Character](#Meta_Character)

## Meta_Character

| Meta Character <br/> 元字符 | Description <br/> 說明 |
|:----:|----|
|.| Match any single character except \n new line. <br/> 匹配任何字符( 字母、數字或符號，但不包含換行符號 ) |
|[ ]| Character class. Match any character contained between the square brackets. <br/> 任意匹配中括號內字串中裡的每個項目 |
|[^ ]| Negated character class. Match any character that is not contained between the square brackets. <br/> 任意批配**不包含**中括號內字串中裡的每個項目 |
|*| Match 0 or more repetitions of the preceding symbol. <br/> 匹配 0 到無窮多次個在 <code>*</code> 之前的字符。 |
|+| Match 1 or more repetitions of the preceding symbol. <br/> 匹配 1 到無窮多次個在 <code>+</code> 之前的字符。 |
|?| Make the preceding symbol optional. <br/> 匹配 0 或 1 次在 <code>?</code> 之前的字符。 |
|{n,m}| Braces. Match at least "n" but not more than "m" repetitions of the preceding symbol. <br/> 匹配某個符號或字符集出現 n ~ m 次 |
|(xyz)| Character group. Match the characters xyz in that exact order. <br/> 匹配與 xyz 完全相等的字符串 |
|^| Match the beginning of the input. <br/> 匹配開頭與 <code>^</code> 鄰接字符相符的字符 |
|$| Match the end of the input. <br/> 匹配結尾與 <code>$</code> 鄰接字符相符的字符 |
|&#92;| Escape the next character. This allows you to match reserved characters <code>[ ] ( ) { } . * + ? ^ $ \ &#124;</code> <br/> 表示鄰接字符應視為字符 |
|&#124;| Alternation. Match either the characters before or the characters after the symbol. |

【Examples】  
| Test String | Regular Expression |
|:----:|----|
| This is<code> just\na simple </code>sentence. | <code>(?<=This is)(.*)(?=sentence)</code> | 




Back to [Contents](#Contents)
<br>
