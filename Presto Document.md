# Presto Document


## W3 School_String Functions
1.获取首字母的美国信息交换标准代码: ASCII( ) Function
```html
SELECT Customername, ASCII(Customername) AS NumcodeOfFirstChar
FROM Customers;
```
2.获取字节的长度：The CHAR_LENGTH() function return the length of a string (in characters), equal to CHARACTER_LENGTH()
SELECT Customername, CHAR_LENGTH(Customername) AS LengthOfName
FROM Customers;

3.组合字段：CONCAT
Syntax: CONCAT(expression1, expression2, expression3...)

```html
SELECT CONCAT(Address, " ", PostalCode, " ", City) AS Address
FROM Customers;
```
组合字段之间用逗号隔开

4.组合字段并且在字段中间增加分隔符: CONCAT_WS
Syntax: (separator, expression1, expression2, expression3)

5.返回字符在列表里的位置： FIELD

* The FIELD() function returns the index position of a value in a list of values.

* This function performs a case-insensitive search.

* Note: If the specified value is not found in the list of values, this function will return 0. If value is NULL, this function will return 0.

Syntax: (Value, val1, val2, val3...)

