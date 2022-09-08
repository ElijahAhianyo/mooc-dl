# Utils Common

[_Documentation generated by Documatic_](https://www.documatic.com)

<!---Documatic-section-Codebase Structure-start--->
## Codebase Structure

<!---Documatic-block-system_architecture-start--->
```mermaid
None
```
<!---Documatic-block-system_architecture-end--->

# #
<!---Documatic-section-Codebase Structure-end--->

<!---Documatic-section-utils.common.touch_dir-start--->
## [utils.common.touch_dir](3-utils_common.md#utils.common.touch_dir)

<!---Documatic-section-touch_dir-start--->
<!---Documatic-block-utils.common.touch_dir-start--->
<details>
	<summary><code>utils.common.touch_dir</code> code snippet</summary>

```python
def touch_dir(path):
    if not os.path.exists(path):
        os.makedirs(path)
    return os.path.normpath(path)
```
</details>
<!---Documatic-block-utils.common.touch_dir-end--->
<!---Documatic-section-touch_dir-end--->

# #
<!---Documatic-section-utils.common.touch_dir-end--->

<!---Documatic-section-utils.common.touch_file-start--->
## [utils.common.touch_file](3-utils_common.md#utils.common.touch_file)

<!---Documatic-section-touch_file-start--->
<!---Documatic-block-utils.common.touch_file-start--->
<details>
	<summary><code>utils.common.touch_file</code> code snippet</summary>

```python
def touch_file(path):
    if not os.path.exists(path):
        open(path, 'w').close()
    return os.path.normpath(path)
```
</details>
<!---Documatic-block-utils.common.touch_file-end--->
<!---Documatic-section-touch_file-end--->

# #
<!---Documatic-section-utils.common.touch_file-end--->

<!---Documatic-section-utils.common.repair_filename-start--->
## [utils.common.repair_filename](3-utils_common.md#utils.common.repair_filename)

<!---Documatic-section-repair_filename-start--->
<!---Documatic-block-utils.common.repair_filename-start--->
<details>
	<summary><code>utils.common.repair_filename</code> code snippet</summary>

```python
def repair_filename(filename):

    def to_full_width_chr(matchobj):
        char = matchobj.group(0)
        full_width_char = chr(ord(char) + +ord('？') - ord('?'))
        return full_width_char
    regex_path = re.compile('[\\\\/:*?"<>|]')
    regex_spaces = re.compile('\\s+')
    regex_non_printable = re.compile('[\\001\\002\\003\\004\\005\\006\\007\\x08\\x09\\x0a\\x0b\\x0c\\x0d\\x0e\\x0f\\x10\\x11\\x12\\x13\\x14\\x15\\x16\\x17\\x18\\x19\\x1a]')
    regex_sort = re.compile('^[第一二三四五六七八九十\\d]+[\\s\\d._\\-章课节讲]*[.\\s、\\-]\\s*\\d*')
    filename = regex_path.sub(to_full_width_chr, filename)
    filename = regex_spaces.sub(' ', filename)
    filename = regex_non_printable.sub('', filename)
    filename = regex_sort.sub('', filename)
    filename = filename.strip()
    return filename
```
</details>
<!---Documatic-block-utils.common.repair_filename-end--->
<!---Documatic-section-repair_filename-end--->

# #
<!---Documatic-section-utils.common.repair_filename-end--->

<!---Documatic-section-utils.common.get_size-start--->
## [utils.common.get_size](3-utils_common.md#utils.common.get_size)

<!---Documatic-section-get_size-start--->
<!---Documatic-block-utils.common.get_size-start--->
<details>
	<summary><code>utils.common.get_size</code> code snippet</summary>

```python
def get_size(path):
    if os.path.isfile(path):
        return os.path.getsize(path)
    elif os.path.isdir(path):
        size = 0
        for subpath in os.listdir(path):
            size += get_size(os.path.join(path, subpath))
        return size
    else:
        return 0
```
</details>
<!---Documatic-block-utils.common.get_size-end--->
<!---Documatic-section-get_size-end--->

# #
<!---Documatic-section-utils.common.get_size-end--->

<!---Documatic-section-utils.common.size_format-start--->
## [utils.common.size_format](3-utils_common.md#utils.common.size_format)

<!---Documatic-section-size_format-start--->
<!---Documatic-block-utils.common.size_format-start--->
<details>
	<summary><code>utils.common.size_format</code> code snippet</summary>

```python
def size_format(size, ndigits=2):
    flag = '-' if size < 0 else ''
    size = abs(size)
    units = ['Bytes', 'kB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB', 'BB']
    idx = len(units) - 1
    unit = ''
    unit_size = 0
    while idx >= 0:
        unit_size = 2 ** (idx * 10)
        if size >= unit_size:
            unit = units[idx]
            break
        idx -= 1
    return '{}{:.{}f} {}'.format(flag, size / unit_size, ndigits, unit)
```
</details>
<!---Documatic-block-utils.common.size_format-end--->
<!---Documatic-section-size_format-end--->

# #
<!---Documatic-section-utils.common.size_format-end--->

<!---Documatic-section-utils.common.get_string_width-start--->
## [utils.common.get_string_width](3-utils_common.md#utils.common.get_string_width)

<!---Documatic-section-get_string_width-start--->
<!---Documatic-block-utils.common.get_string_width-start--->
<details>
	<summary><code>utils.common.get_string_width</code> code snippet</summary>

```python
def get_string_width(string):
    try:
        length = len(string.encode('gbk'))
    except:
        length = len(string)
    return length
```
</details>
<!---Documatic-block-utils.common.get_string_width-end--->
<!---Documatic-section-get_string_width-end--->

# #
<!---Documatic-section-utils.common.get_string_width-end--->

[_Documentation generated by Documatic_](https://www.documatic.com)