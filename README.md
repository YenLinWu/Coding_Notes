# Coding Notes

# Python  
## Contents
* [String](#String)
* [List](#List)
* [Others](#Others)

### String
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

### List 
- Convert list to string   
```python
list_ = ['A','B','C']
string = '/'.join(list_)
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
list_ .pop()
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

### Others
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

