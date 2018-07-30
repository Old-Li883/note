# python代码风格规范

## 行长度

每行不超过80个字符

不要用反斜杠接行

括号可以隐式接行

## 空行

顶级定义间空一行

## 空格

括号内无空格

逗号，分号，冒号前无空格，后有空格

括号左边无空格

二元操作左右两边有空格

=表示参数时，无空格

## 开头

main函数要以#开头

## 文档注释

```
def fetch_bigtable_rows(big_table, keys, other_silly_variable=None):
    """Fetches rows from a Bigtable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by big_table.  Silly things may happen if
    other_silly_variable is not None.

    Args:
        big_table: An open Bigtable Table instance.
        keys: A sequence of strings representing the key of each table row
            to fetch.
        other_silly_variable: Another optional variable, that has a much
            longer name than the other args, and which does nothing.

    Returns:
        A dict mapping keys to the corresponding table row data
        fetched. Each row is represented as a tuple of strings. For
        example:

        {'Serak': ('Rigel VII', 'Preparer'),
         'Zim': ('Irk', 'Invader'),
         'Lrrr': ('Omicron Persei 8', 'Emperor')}

        If a key from the keys argument is missing from the dictionary,
        then that row was not found in the table.

    Raises:
        IOError: An error occurred accessing the bigtable.Table object.
    """
    pass
```

## 字符串

避免出现+

保持字符串引用的统一性，全用单引号，或全用双引号

## 文件

with语句打开文件

## 将要做某事

TODO注释

## 导入

每一个import独占一行

## 命名

每一个类以大写字母开头

每一个模块用小写字母加下划线的格式

## main

加入`if __name__ == '__main__'`