import urllib.request
import ssl

def readWebPage(url):
    '''
    this function takes one parameter, the URL from which to read the text,
    and it returns a list where each element is a word in the text found on the website.
    The function should read the contents of the website into a string and convert the string to a list of words.
    You might find the .split() method useful to split a string into a list of words.
    (Try this:  "the quick brown fox".split() and see what you end up with).
    Be sure to check that the website is found and opened properly using exceptions.
    '''
    ssl._create_default_https_context = ssl._create_unverified_context
    http = url
    response = urllib.request.urlopen(http)
    data = response.read().decode('utf-8') #read data
    new_data = str(data)
    New_list = new_data.split() #set data as a list
    return print(New_list)  #return list

def convertToDictionary(wordList):
    '''
    this function takes one parameter – a list of strings (each word in the text found on the website).
    It returns a dictionary of key/value pairs where the value is a list of words that all begin with the same letter and are the same length.
    '''
    global longestWordLength
    dictionary = {}
    for words in wordList:
        char = words[0]
        if char in dictionary:
            dictionary[char].append(words)
        else:
            dictionary[char] = [words]
    return dictionary



# def removePunctuation(wordList):


def main():
    url = 'https://www.cs.queensu.ca/home/cords2/cs.txt'
    readWebPage(url)
    wordList = readWebPage(url)
    convertToDictionary(wordList)


main()
