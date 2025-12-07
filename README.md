[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/nmEA1V6F)
# pythonAssignment_sourceConvert
### Python 源文件改写。编写一个程序，读取random_int.py文件，将文件中所有除保留字外的小写字母换成大写字母，并将转化后的代码保存在另一个文件中。
@@ -1,5 +1,26 @@
# 在这个文件中编写代码实现题目要求的功能
import keyword  # 建议使用这个库处理关键字
reserved_words = set(keyword.kwlist)

# 以下内容自行完成
import keyword
def convert_source_file(input_path, output_path):
    with open(input_path, 'r', encoding='utf-8') as f:
        content = f.read()
    tokens = []
    current_word = []
    for char in content:
        if char.isalnum() or char == '_':
            current_word.append(char)
        else:
            if current_word:
                tokens.append(''.join(current_word))
                current_word = []
            tokens.append(char)
    if current_word:
        tokens.append(''.join(current_word))
    processed_tokens = []
    for token in tokens:
        if token in keyword.kwlist:
            processed_tokens.append(token)
        else:
            processed_tokens.append(token.upper())
    processed_content = ''.join(processed_tokens)
    with open(output_path, 'w', encoding='utf-8') as f:
        f.write(processed_content)
convert_source_file('random_int.py', 'converted_random_int.py')
