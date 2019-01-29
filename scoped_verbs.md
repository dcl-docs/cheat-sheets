Scoped verbs
================

Suffixes
--------

| suffix | use when                                                         |
|:-------|:-----------------------------------------------------------------|
| \_all  | you want to apply the verb to all columns                        |
| \_at   | you want to apply the verb to specified columns                  |
| \_if   | you want to apply the verb to all the columns with some property |

Examples
--------

### `mutate()`, `summarize()`, `select()`, and `rename()`

#### Named functions

<table>
<colgroup>
<col width="10%" />
<col width="26%" />
<col width="62%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Verb</th>
<th align="left">Example</th>
<th align="left">Example explanation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">summarize_all</td>
<td align="left">summarize_all(mean)</td>
<td align="left">finds the mean of all variables</td>
</tr>
<tr class="even">
<td align="left">summarize_at</td>
<td align="left">summarize_at(vars(x, y), mean)</td>
<td align="left">finds the mean of variables x and y</td>
</tr>
<tr class="odd">
<td align="left">summarize_if</td>
<td align="left">summarize_if(is.double, mean)</td>
<td align="left">finds the mean of all double variables</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">mutate_all</td>
<td align="left">mutate_all(as.character)</td>
<td align="left">converts all variables to characters</td>
</tr>
<tr class="even">
<td align="left">mutate_at</td>
<td align="left">mutate_at(vars(x, y), as.character)</td>
<td align="left">converts variables x and y to characters</td>
</tr>
<tr class="odd">
<td align="left">mutate_if</td>
<td align="left">mutate_if(is.factor, as.character)</td>
<td align="left">converts all factor variables to characters</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">rename_all</td>
<td align="left">rename_all(str_to_lower)</td>
<td align="left">changes all column names to lowercase</td>
</tr>
<tr class="even">
<td align="left">rename_at</td>
<td align="left">rename_at(vars(X, Y), str_to_lower)</td>
<td align="left">changes the names of columns X and Y to x and y</td>
</tr>
<tr class="odd">
<td align="left">rename_if</td>
<td align="left">rename_if(is.double, str_to_lower)</td>
<td align="left">changes the names of double columns to lowercase</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">select_all</td>
<td align="left">select_all(str_to_lower)</td>
<td align="left">selects all columns and changs their names to lowercase (better to use rename_all())</td>
</tr>
<tr class="even">
<td align="left">select_at</td>
<td align="left">select_at(vars(X, Y), str_to_lower)</td>
<td align="left">selects just columns X and Y and changes their names to x and y</td>
</tr>
<tr class="odd">
<td align="left">select_if</td>
<td align="left">select_if(is.double, str_to_lower)</td>
<td align="left">selects just double columns and changes their names to lowercase</td>
</tr>
</tbody>
</table>

#### Extra arguments

| verb           | example                                        | example\_explanation                                                                                                           |
|:---------------|:-----------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| summarise\_if  | summarize\_if(is.double, mean, na.rm = TRUE)   | finds the mean, excluding NAs, of all double variables                                                                         |
| summarize\_all | summarize\_all(mean, trim = 0.1, na.rm = TRUE) | finds the mean of all variables, exluding NAs. Removes the bottom and top 10% of values of each variable before computing mean |

#### Anonymous functions

| verb           | example                             | example\_explanation                                       |
|:---------------|:------------------------------------|:-----------------------------------------------------------|
| summarize\_all | summarize\_all(~ sum(is.na(.)))     | determines the number of NAs in each column                |
| select\_if     | select\_if(~ n\_distinct(.) &gt; 1) | selects only the columns with more than one distinct value |

### `filter()`

<table>
<colgroup>
<col width="10%" />
<col width="38%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">verb</th>
<th align="left">example</th>
<th align="left">example_explanation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">filter_all</td>
<td align="left">filter_all(all_vars(!is.na(.))</td>
<td align="left">finds rows without any NAs</td>
</tr>
<tr class="even">
<td align="left">filter_all</td>
<td align="left">filter_all(any_vars(!is.na(.))</td>
<td align="left">finds rows with at least one non-NA value</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">filter_at</td>
<td align="left">filter_at(vars(x, y), all_vars(!is.na(.))</td>
<td align="left">finds rows where both x and y are non-NA</td>
</tr>
<tr class="odd">
<td align="left">filter_at</td>
<td align="left">filter_at(vars(x, y), any_vars(!is.na(.))</td>
<td align="left">finds rows where at least one of x and y is non-NA</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left">filter_if</td>
<td align="left">filter_if(is.double, all_vars(!Is.na(.))</td>
<td align="left">finds rows where all double variables are non-NA</td>
</tr>
<tr class="even">
<td align="left">filter_if</td>
<td align="left">filter_if(is.double, any_vars(!Is.na(.))</td>
<td align="left">finds rows where at least one double variable is non-NA</td>
</tr>
</tbody>
</table>
