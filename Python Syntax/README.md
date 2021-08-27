# Python Programming Notes
![Python3.7](https://img.shields.io/badge/Python-3.7-blue.svg)

## Contents
* [String](#String)
* [List](#List)
* [Dictionary](#Dictionary)
* [DataFrame](#DataFrame)
* [Others](#Others) 
* [Examples](#Examples)

## String
- Create a range of alphabets   
```python
import string
string.ascii_lowercase
```
> 'abcdefghijklmnopqrstuvwxyz'

```python
string.ascii_uppercase
```
> 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'  

- Reverse a string 
```python
'Hello World'[::-1]  
```
> 'dlroW olleH' 
  
Back to [Contents](#Contents)

## List 
- Convert list to string   
```python
list_ = ['A','B','C']
string = '/'.join( list_ )
string
```
> 'A/B/C' 
  
If the list is of integers, convert the elements before joining them.
```python
list_ = [1,2,3,4,5,6,7,8,9]
str2 = ''.join( str(i) for i in list_ if i%2==0 ) 
str2
```
> '2468'

- Sort a list in ascending, descending or user defined order.
```python
# Method 1
list_ = [1,8,3,6,5,4,7,2,9]
list_.sort()
list_

# Method 2
# Note that sorted() function will return a NEW sorted list.
list_ = [1,8,3,6,5,4,7,2,9]
sorted_list = sorted( list_ ) 
sorted_list
```
> [1, 2, 3, 4, 5, 6, 7, 8, 9]

```python
list_ = [1,8,3,6,5,4,7,2,9]
sorted_list = sorted( list_, reverse=True )
sorted_list
```
> [9, 8, 7, 6, 5, 4, 3, 2, 1]
 
```python
list_ = ['D','a','C','b','B','c','A','d']
sorted_list_1 = sorted( list_ )
sorted_list_2 = sorted( list_, key=str.lower )

sorted_list_1
sorted_list_2
```
> ['A', 'B', 'C', 'D', 'a', 'b', 'c', 'd']  
> ['a', 'A', 'b', 'B', 'C', 'c', 'D', 'd']

- Pick up elements in a list 
```python
list_ = [1,2,3,4,5,6,7,8,9]
```

```python
list_[:3]  # or list_[:3:]
```
> [1, 2, 3]

```python
list_[:-3]
```
> [1, 2, 3, 4, 5, 6]

```python
list_[::3]
```
> [1, 4, 7]

```python
list_[::-3]
```
> [9, 6, 3]

```python
list_[:2:-3]
```
> [9, 6]

```python
list_[3::-1]
```
> [4, 3, 2, 1]

```python
list_[:3:-1]
```
> [9, 8, 7, 6, 5] 

- Reverse a list  
```python
list_ = [1,2,3,4,5,6,7,8,9]
list_[::-1]  # or list( reversed(list_) ) 
```
> [9, 8, 7, 6, 5, 4, 3, 2, 1]

- Find the index of an element in a list  
```python
list_ = ['A','B','C','D','E']
list_.index('C')
```
> 2

- Remove the element from a list
```python
list_ = ['A','B','C','D','E']
list_.remove('B')
list_
```
> ['A', 'C', 'D', 'E']

```python
list_ = ['A','B','C','D','E']
list_ .pop(1)
list_
```
> ['A', 'C', 'D', 'E']

```python
list_ = ['A','B','C','D','E']
del list_ [1:3]
list_ 
```
> ['A', 'D', 'E']

Remove the last element of a list : 
```python
list_ = [1,2,3,4,5]
list_.pop()  # or list_[:-1]
list_ 
```
> [1, 2, 3, 4] 

Use a list comprehension for removing all occurrences of our element :  
```python
list_ = [1,2,3,4,5]
[ x for x in list_ if x%2!=0 ]
```
> [1, 3, 5]

- Add an element to the end of the list with `append()`
```python
list_ = [1,2,3]
list_.append( 'New' ) 
list_
```
> [1, 2, 3, 'New']

```python
list_ = [1,2,3]
list_.append( ['New','Old'] ) 
list_
```
> [1, 2, 3, ['New', 'Old']]

- Add an element at the specified index (position) of a list by `insert()`  
```python
list_ = [1,2,3]
list_.insert( 2, 'New' )
list_
```
> [1, 2, 'New', 3]

- Combine another list or tuple at the end of the original list by `extend()`  
```python
list_ = [1,2,3]
list_.extend( ['New','Old']  ) # or list_.extend( ['New','Old']  )
list_
```
> [1, 2, 3, 'New', 'Old']

In the case of a string, note that each character is added one by one.
```python
list_ = [1,2,3]
list_.extend('New' )
list_
```
> [1, 2, 3, 'N', 'e', 'w']

The `+` operator instead of `extend()` : 
```python
list_ = [1,2,3]
new_list = list_ + ['New','Old'] 
new_list
```
> [1, 2, 3, 'New', 'Old']

```python
list_ = [1,2,3]
list_ += ['New','Old'] 
list_
```
> [1, 2, 3, 'New', 'Old']    
  
Back to [Contents](#Contents)

## Dictionary
- Convert two lists into a dictionary  
```python
keys = [1,2,3]
values = ['A','B','C']

# Method 1
dict_ = dict( zip(keys,values) )

# Method 2
dict_ = { k:v for k, v in zip(keys,values) }

dict_
```
> {1: 'A', 2: 'B', 3: 'C'}  

- Sort a dictionary by key/value
```python
dict_ = { 4:'A', 1:'C', 2:'E', 3:'D', 5:'B' }

# Sort by key
# Method 1
sorted_by_key = dict( sorted( dict_.items(), key=lambda item: item[0] ) )
# Method 2
sorted_by_key = { k: v for k, v in sorted(dict_.items(), key=lambda item: item[0]) } 

# Sort by value
# Method 1
sorted_by_value = dict( sorted( dict_.items(), key=lambda item: item[1] ) )
# Method 2
sorted_by_value = { k: v for k, v in sorted(dict_.items(), key=lambda item: item[1]) } 

sorted_by_key
sorted_by_value
```
> {1: 'C', 2: 'E', 3: 'D', 4: 'A', 5: 'B'}   
> {4: 'A', 5: 'B', 1: 'C', 3: 'D', 2: 'E'}  

- Get value of Key  
```python
dict_ = {1:'A',2:'B',3:'C'}
dict_[1]  # or dict_.get(1)
```
> 'A'   

`get()` method allows us to provide a default value if the key is missing :  
```python
dict_ = {1:'A',2:'B',3:'C'}
dict_.get( 4,'No Data' )
```
> 'No Data'  

- Delete the element from a dictionary  
`del` statement removes an element from a divtionary.   
```python
dict_ = {1:'A',2:'B',3:'C'}
del dict_[ 2 ]  # del dictionary[ key ]
dict_
```
> {1:'A',3:'C'}  
  
- Add an item into the 1st location in a dictionary  
```python
dict_ = {1:'A',2:'B',3:'C'}
dict_ = {4:'D', **dict_}
dict_
```
> {4: 'D', 1: 'A', 2: 'B', 3: 'C'}
  
Back to [Contents](#Contents)

## DataFrame
| | Col_1 | Col_2 | Col_3 | 
| ---------- | ----------: | -----------: | -----------: |
| 0 | A | 40 | 0.9 | 
| 1 | B | 25 | 0.8 |
| 2 | C | 20 | 0.7 |
| 3 | D | 30 | 0.6 |
| 4 | A | 15 | 0.5 |

- Get index of rows which column satisfies some conditions  
```python
over_20_index = df.index[ df['Col_2']>20 ]
over_20_index

# Convert index labels to list
# over_20_index.tolist()
# > [0, 1, 3]
```
> Int64Index([0, 1, 3], dtype='int64')

- Select the rows by specific indexes using `loc[]`.  
```python
df.loc[ over_20_index ]

# or 
# df.loc[ [0,1,3] ]
```
> | | Col_1 | Col_2 | Col_3 | 
> | ---------- | ----------: | -----------: | -----------: |
> | 0 | A | 40 | 0.9 |
> | 1 | B | 25 | 0.8 |
> | 3 | D | 30 | 0.6 |

- Drop the rows by specific indexes using `drop()`.  
  - Note that the [drop](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.drop.html) function can drop specified labels from rows or columns.
```python
df.drop( over_20_index )

# or 
# df.drop( [0,1,3] )
```
> | | Col_1 | Col_2 | Col_3 | 
> | ---------- | ----------: | -----------: | -----------: |
> | 2 | C | 20 | 0.7 |
> | 4 | A | 15 | 0.5 |
 
- Drop the columns using `drop()`.  
```python
df.drop( columns=['Col_1','Col_3'] )
```
> | | Col_2 |
> | ---------- | ----------: | 
> | 0 | 40 |  
> | 1 | 25 |
> | 2 | 20 | 
> | 3 | 30 |
> | 4 | 15 |

- Sort the dataframe by multiple columns using [`sort_values()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.sort_values.html).     
```python
df.sort_values( by=['Col_1'], ascending=True, inplace=False )
```
> | | Col_1 | Col_2 | Col_3 | 
> | ---------- | ----------: | -----------: | -----------: |
> | 0 | A | 40 | 0.9 | 
> | 4 | A | 15 | 0.5 |
> | 1 | B | 25 | 0.8 |
> | 2 | C | 20 | 0.7 |
> | 3 | D | 30 | 0.6 |

```python
df.sort_values( by=['Col_1','Col_2'], ascending=True, inplace=False )
```
> | | Col_1 | Col_2 | Col_3 | 
> | ---------- | ----------: | -----------: | -----------: |
> | 4 | A | 15 | 0.5 | 
> | 0 | A | 40 | 0.9 |
> | 1 | B | 25 | 0.8 |
> | 2 | C | 20 | 0.7 |
> | 3 | D | 30 | 0.6 |

---         
---       

| | Col_1 | Col_2 | Col_3 | 
| ---------- | ----------: | -----------: | -----------: |
| 0 | A | 1 | False | 
| 1 | B | 20 | True |
| 2 | C | 300 | False |

- Repest rows in a DataFrame using [`numpy.repeat()`](https://numpy.org/doc/stable/reference/generated/numpy.repeat.html).     
```python
df.loc[np.repeat(df.index.values, 2)]
```
> | | Col_1 | Col_2 | Col_3 | 
> | ---------- | ----------: | -----------: | -----------: |
> | 0 | A | 1 | False | 
> | 0 | A | 1 | False | 
> | 1 | B | 20 | True | 
> | 1 | B | 20 | True |
> | 2 | C | 300 | False |
> | 2 | C | 300 | False |

```python
df.loc[np.repeat(df.index.values[1], 2)]
```
> | | Col_1 | Col_2 | Col_3 | 
> | ---------- | ----------: | -----------: | -----------: |
> | 1 | B | 20 | True | 
> | 1 | B | 20 | True |

---         
---       

| | Col_1 | 
| ---------- | ----------: | 
| 0 | 1 | 
| 1 | 2 | 
| 2 | 3 | 
| 3 | 4 | 
| 4 | 5 | 
| 5 | 6 | 

- Shift index in a DataFrame using [`DataFrame.shift()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.shift.html#pandas-dataframe-shift). 
```python
df['shift_Col_1'] = df['Col_1'].shift( periods=2 )
```
> | | Col_1 | shift_Col_1 | 
> | ---------- | ----------: | ----------: | 
> | 0 | 1 | NaN |
> | 1 | 2 | NaN |
> | 2 | 3 | 1 |
> | 3 | 4 | 2 |
> | 4 | 5 | 3 |
> | 5 | 6 | 4 |

- Rolling window calculations using [`DataFrame.rolling()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.rolling.html).
```python
df['rolling_Col_1'] = df['Col_1'].rolling( window=3 ).mean()
```
> | | Col_1 | rolling_Col_1 | 
> | ---------- | ----------: | ----------: | 
> | 0 | 1 | NaN |
> | 1 | 2 | NaN |
> | 2 | 3 | 2 |
> | 3 | 4 | 3 |
> | 4 | 5 | 4 |
> | 5 | 6 | 5 |

Back to [Contents](#Contents)

## Others
- `zip()` method takes iterables (can be zero or more), aggregates them in a tuple, and return it.
```python
A_list = ['A1','A2','A3']
B_list = ['B1','B2','B3']
for a, b in zip( A_list, B_list ):
    print( a, b )
```
> A1 B1   
> A2 B2   
> A3 B3  

```python
A_list = ['A1','A2','A3','A4']
B_list = ['B1','B2']
for a, b in zip( A_list, B_list ):
    print( a, b )
```
> A1 B1   
> A2 B2  

- `Enumerate()` method adds a counter to an iterable and returns it in a form of enumerate object. 
```python
list_ = ['A','B','C']
for i, a in enumerate( list_ ):
    print( i, a )
# or   
# for e in enumerate( list_ ) :
#     print( e[0], e[1] )
```
> 0 A  
> 1 B  
> 2 C  
 
- `shutil.rmtree()` function deletes an entire folder (that is not empty).   
    - Note that the [shutil](https://docs.python.org/3/library/shutil.html) module offers a number of high-level operations on files and collections of files.
```python
import shutil
shutil.rmtree( FolderPath )
```

Back to [Contents](#Contents)

## Examples
- Highest Common Factor(最大公因數)  
```python
def hcf(x,y):
   for i in range( min(x,y)+1, 0, -1 ) :
       if x%i==0 and y%i==0:
           break
   return i
```
```python
def hcf(x,y):
    while y:
        r = x%y
        x = y
        y = r
    return x 
```

- Index of Minimum/Maximum Value in DataFrame
```python
# Create a data frame
df = pd.DataFrame( {'ID':['A','B','C','D','E'],'Score':[20,300,20,np.nan,300]},
                   index=[1,2,3,4,5] )
df
```
|  | ID | Score | 
| ---------- | :----------: | -----------: | 
| 1 | A | 20 | 
| 2 | B | 300 | 
| 3 | C | 20 | 
| 4 | D | NaN | 
| 5 | E | 300 |  
   
(i) Get the index of first occurrence of minimum in 'Score' column by [pandas.DataFrame.idxmin](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.idxmin.html)
```python
df['Score'].idxmin()
```
> 1

(ii) Get the index of first occurrence of maximum in 'Score' column by [pandas.DataFrame.idxmax](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.idxmax.html)
```python
df['Score'].idxmax()
```
> 2

(iii) Get the index of maximum in 'Score' column      
```python
df[ df['Score']==df['Score'].max() ].index
```
> Int64Index([2, 5], dtype='int64')

(iv) Select the value in 'ID' column having the maximum of 'Score' column  
```python
df.loc[ df['Score']==df['Score'].max(), 'ID' ]
```
> 2    B  
> 5    E  
> Name: ID, dtype: object  

- Calculate the difference between two consecutive rows of the column by [pandas.DataFrame.shift](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.shift.html)
```python
# Create a data frame
df = pd.DataFrame( {'Col_1':[1,3,5,7,9,11]} )
df['diff_Col_1'] = df['Col_1'] - df['Col_1'].shift( periods=1 )  
df
```
> |  | Col_1 | diff_Col_1 | 
> | ---------- | :----------: | -----------: | 
> | 0 | 1 | NaN | 
> | 1 | 3 | 2 | 
> | 2 | 5 | 2 | 
> | 3 | 7 | 2 | 
> | 4 | 9 | 2 |  
> | 5 | 11 | 2 |  

- if-elif-else in DataFrame
```python
# Create a data frame
df = pd.DataFrame( {'Score':[np.nan,10,20,30,50,70,90]} )
df
```
| | Score | 
| ---------- | ----------: | 
| 0 | NaN | 
| 1 | 10 | 
| 2 | 20 | 
| 3 | 30 | 
| 4 | 50 |  
| 5 | 70 |  
| 6 | 90 |  

(i) if-elif-else in one line  
```python
df['Rank'] = df.apply( lambda x: 'A' if x['Score']<30 else ('B' if x['Score']<60 else 'C'), axis=1 )
df
```
> | | Score | Rank |
> | ---------- | ----------: | -----------: | 
> | 0 | NaN | C | 
> | 1 | 10 | A |
> | 2 | 20 | A |
> | 3 | 30 | B |
> | 4 | 50 | B |  
> | 5 | 70 | C | 
> | 6 | 90 | C | 

(ii) [numpy.where()](https://numpy.org/doc/stable/reference/generated/numpy.where.html)
```python
df['Rank'] = np.where( df['Score']<30, 'A', np.where(df['Score']<60, 'B', 'C') )
df
```
> | | Score | Rank |
> | ---------- | ----------: | -----------: |   
> | 0 | NaN | C |   
> | 1 | 10 | A |
> | 2 | 20 | A |
> | 3 | 30 | B |
> | 4 | 50 | B |  
> | 5 | 70 | C | 
> | 6 | 90 | C | 

(iii) [numpy.select()](https://numpy.org/doc/stable/reference/generated/numpy.select.html)
```python
df['New Score'] = np.select( 
    condlist = [df['Score']<50, (df['Score']>=50)&(df['Score']<=70)], 
    choicelist = [df['Score']+10, df['Score']+15], 
    default = df['Score']+8 
    )
    
df
```
> | | Score | New Score |   
> | ---------- | ----------: | ----------: |   
> | 0 | NaN | NaN |   
> | 1 | 10 | 20 |  
> | 2 | 20 | 30 |  
> | 3 | 30 | 40 |  
> | 4 | 50 | 65 |    
> | 5 | 70 | 85 |   
> | 6 | 90 | 98 |   

Back to [Contents](#Contents)
