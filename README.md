# python
def triplets(n):
    arr = []
    for a in range(1,n):
        for b in range(a,n):
            for c in range(b,n):
                if(a+b == c):
                    arr.append([a,b,c])
    return arr

n = 10
result = triplets(n)
print(result)

//lensort
def lensort(list,size):
    result = []
    for i in range(0,len(list),size):
        result.append(list[i:i+size])

    return result

test_list = [1,2,3,4,5,3,2,4,5,7,8]
print(lensort(test_list,3))

//reverse
def reverse_lines(filename):
    with open(filename,'r') as file:
        lines = file.readlines()

    for line in reversed(lines):
        print(line)

filename = 'example.txt'
reverse_lines(filename)

//mutations
def insert_char(word,index,char):
    return word[:index] + char + word[index:]

def delete_char(word, index):
    return word[:index] + word[index+1:]

def replace_char(word,index,char):
    return word[:index] + char + word[index+1:]

def swap_char(word, index):
    if index >= len(word) -1:
        return word
    return word[:index] + word[index+1] + word[index] + word[index+2:]

def mutate(word):
    mutations = set()
    
    #insertion
    for i in range(len(word) + 1):
        for char in 'abcdefghijklmnopqrstuvwxyz':
            mutations.add(insert_char(word,i,char))

    #deletion
    for i in range(len(word)):
        mutations.add(delete_char(word,i))

    #replacement
    for i in range(len(word)):
        for char in 'abcdefghijklmnopqrstuvwxyz':
            if word[i] != char:
                mutations.add(replace_char(word,i,char))

    #swap
    for i in range(len(word)):
        mutations.add(swap_char(word,i))

    return mutations

word = "hello"
print(mutate(word))


    

def my_map(function, iterable):
    arr = []
    for item in iterable:
        arr.append(function(item))
    return arr

numbers = [1,2,3,4,5]
squared_numbers = my_map(lambda x: x**2, numbers)
print(squared_numbers)

def my_filter(function, iterable):
    arr = []
    for item in iterable:
        if function(item):
            arr.append(item)
    return arr

numbers = [1,2,3,4,5,6,7,8,9,10]
even_numbers  = my_filter(lambda x : x%2 == 0 , numbers)
print(even_numbers)


file = open("example.txt", 'r')
#content = file.read()
#print(content)
print('\n')

#line = file.readline()
#print(line)

#with open('example.txt','w') as output_file:
 #   output_file.write("KUCH NAYA HO JAAAYEE")

lines = ['Line 1\n', 'Line 2\n', 'Line 3\n']
 with open('example.txt', 'w') as output_files:
    output_files.writelines(lines)

file.close

def exsort(files):
    return sorted(files, key=lambda x: x.split('.')[-1])

files = ['document.txt', 'image.png', 'script.py']
print(exsort(files))


def find_duplicates(list):
    arr = set()
    duplicates = []
    for item in list:
        if item in arr and item not in duplicates:
            duplicates.append(item)
        else:
            arr.add(item)
    return duplicates

test_list = [1,2,3,4,5,6,7,8,7,2]
print(find_duplicates(test_list))

def parse_csv(file_path, delimiter = ','):
    parsed_data = []

    with open(file_path, 'r') as file:
        for line in file:
            line = line.strip()

            if line:
                row = line.split(delimiter)
                parsed_data.append(row)
    return parsed_data

file_path = "data.csv"
csv_data = parse_csv(file_path)
for row in csv_data:
    print(row)

def cnt_file_lines(fileName):
    cnt_words = 0
    cnt_lines = 0
    cnt_characters = 0

    file = open(fileName, 'r')

    for line in file:
        cnt_lines +=1
        cnt_characters +=len(line)
        words = line.split()
        cnt_words += len(words)
    return cnt_characters, cnt_lines,cnt_words

fileName = 'example.txt'
cnt_words,cnt_lines,cnt_characters = cnt_file_lines(fileName)
print(cnt_characters)
print(cnt_words)
print(cnt_lines)

def find_anagrams(wordList):
    anagram_groups = {}
    for word in wordList:
        sortedWord = ' '.join(sorted(word))
        if sortedWord in anagram_groups:
            anagram_groups[sortedWord].append(word)
        else:
            anagram_groups[sortedWord] = [word]

    return[group for group in anagram_groups.values() if len(group)>1]

word_list = ["eat", 'ate', "tea", 'hello', "world"]
anagram_groups = find_anagrams(word_list)

for group in anagram_groups:
    print("Anagrams:", group)
