# Regular Expression  

## Contents
* [Meta Character](#Meta_Character)
* [Character Classes](#Character_Classes)
* [Examples](#Examples)  
* [Reference Sources](#Reference_Sources)

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

Back to [Contents](#Contents)
<br>

## Character_Classes

| Character Classes <br/> 字符集 | Description <br/> 說明 |
|:----:|----|
|\w| Match alphanumeric characters: `[a-zA-Z0-9_]` <br/> 匹配所有的字母與數字 |
|\W| Match non-alphanumeric characters: `[^\w]` <br/> 匹配所有的符號(非字母、非數字) |
|\d| Match digits: `[0-9]` <br/> 匹配數字 |
|\D| Match non-digits: `[^\d]` <br/> 匹配非數字 |
|\s| Match whitespace characters: `[\t\n\f\r\p{Z}]` <br/> 匹配所有空格符號 |
|\S| Match non-whitespace characters: `[^\s]` <br/> 匹配所有非空格符號 |

Back to [Contents](#Contents)
<br>

## Examples   

| Test String | Regular Expression |
|:----|----|
| This is<code> just\na simple </code>sentence. | <code>(?<=This is)(.*)(?=sentence)</code> | 
| <a href="#learn-regex"><strong>A1B2C3<strong></a>? <br> <a href="#learn-regex"><strong>A1B2C3<strong></a>?? <br> <a href="#learn-regex"><strong>A1<strong></a>??B2C3 <br> ??A1B2C3 | <code>^[^\\?]*</code> | 
| <a href="#learn-regex"><strong>106<strong></a> 台北市大安區仁愛路 <br> <a href="#learn-regex"><strong>801<strong></a> 高雄市前金區八德二路 <br> <a href="#learn-regex"><strong>266<strong></a> 宜蘭縣三星鄉建富路一段 | <code>[^\D]</code> | 
| 106 <a href="#learn-regex"><strong>台北市<strong></a>大安區仁愛路 <br> 801 <a href="#learn-regex"><strong>高雄市<strong></a>前金區八德二路 <br> 266 <a href="#learn-regex"><strong>宜蘭縣<strong></a>三星鄉建富路一段 | <code>(?<=\D)(.\*)(?<=市\|縣)</code> <br> <code>(?<=\s)(.\*)(?<=市\|縣)</code> | 
| 106 台北市<a href="#learn-regex"><strong>大安區<strong></a>仁愛路 <br> 801 高雄市<a href="#learn-regex"><strong>前金區<strong></a>八德二路 <br> 266 宜蘭縣<a href="#learn-regex"><strong>三星鄉<strong></a>建富路一段 | <code>(?<=市\|縣)(.*)(?<=區\|鄉)</code> |
| (隨文引入)(<a href="#learn-regex"><strong>ATTCH1.pdf<strong></a>) <br> 如主旨(保險單、保險費收據影本各1份)(<a href="#learn-regex"><strong>ATTCH2.pdf<strong></a>) <br> 如文(<a href="#learn-regex"><strong>ATTCH1.pdf、ATTCH2.pdf、ATTCH3.pdf<strong></a>) | <code>(?<=\\()([^\\(]*pdf)(?=\\))</code> |   
| 01_<a href="#learn-regex"><strong>Test01<strong></a>.pdf <br> 02_<a href="#learn-regex"><strong>測試檔02<strong></a>.pdf <br> 03_<a href="#learn-regex"><strong>測試檔_20210426<strong></a>.pdf | <code>(?<=_)(.*)(?=.pdf)</code> |  
| 01_A1_<a href="#learn-regex"><strong>File1<strong></a>.pdf <br> 02_B1_<a href="#learn-regex"><strong>File 2<strong></a>.pdf | <code>[^_]+(?=.pdf)</code> |  
| <a href="#learn-regex"><strong>Tom1112<strong></a>@gmail.com <br> <a href="#learn-regex"><strong>Tom_1112<strong></a>@gmail.com <br> <a href="#learn-regex"><strong>Tom Wu<strong></a>@gmail.com | <code>^.+(?=@)</code> | 
  
Back to [Contents](#Contents)  
<br>

## Reference_Sources

- [Regular Expession 101](https://regex101.com/ "語法測試用")  
- [LEARN REGEX](https://github.com/ziishaned/learn-regex/blob/master/translations/README-cn.md)

Back to [Contents](#Contents)
<br>
