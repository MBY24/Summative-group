#this is for the second project 

#Hussain's lovely code: 

word_list = []

with open('words_alpha.txt','r') as f:
    for line in f:
        word_list.append(line)
        
#Assuming that you'd pass the whole list: 


#Helping function

def one_letter_difference(word, another_word): 
    #It's because every word in the given data base ends with new line ("\n")
    #I wanted to make the number of characters equal and avoid the confusion
    #That's why I added a new line for the passed word
    
    word = word + "\n"
    dif = 0
    
    for i in range(len(word)): 
        if(word[i] != another_word[i]): 
            dif = dif + 1
        
    if (dif == 1): 
        return True
    else:
        return False
    
        
def find_neighbors(word, list): 
    new_list = []
    #filtering all the words with the same length as the argument word
    for w in list: 
        if(len(w) == len(word) + 1): 
            if (one_letter_difference(word, w)):
                new_list.append(w)
    return new_list
#find word_ladder
def main():
    with open("words_alpha.txt", "r") as file:
        word_list = [word.strip() for word in file]
    start_word = input("Enter the start word: ").upper()
    end_word = input("Enter the end word: ").upper()
    start_time = time.time()
    ladder = word_ladder(start_word, end_word, word_list)
    end_time = time.time()
