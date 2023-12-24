import random             
from words import objetos as ob 
from words import animais as an
from words import profissoes as pf 



HANGMAN_PICS = ['''
    --------
    |  |
    |  
    |
    |
    |
     ''', '''
    --------
    |  |
    |  0
    |
    |
    |
    ''' , '''
    --------
    |  |
    |  0
    | /
    |
    |
    ''', '''
    --------
    |  |
    |  0
    | /| 
    |
    |
    ''', '''
    --------
    |  |
    |  0
    | /|\ 
    |
    |
    ''', ''' 
    --------
    |  |
    |  0
    | /|\ 
    | /
    |
    ''', ''' 
    --------
    |  |
    |  0
    | /|\ 
    | / \ 
    |
    ''']

# Lista de palavras
words = 'mochila barba cabelo vertido roupa gato cachorro carro casa panda ovelha tartatura coelho rato corvo zebra'.split()

# Pede para o jogor escolher um tema, a palavra que ele vai ter que adivinhar vai estar relacionada ao tema.
def choose_words_theme(ob, an, pf):
    print()
    print('Escolha um dos temas')
    print('1 - Objetos')
    print('2 - Animais')
    print('3 - Profissões')
    tema = input('Escolha escolha um desses temas. Ex: 1 para Objetos: ')


    if tema == '1':
        return ob
    elif tema  == '2':
        return an
    else:
        return pf
     

# Pegar nome do jogador
def getplayerName():
    print()
    playerName = input('Digite o seu nome: ')
    return playerName 

# Função para retornar uma palavra aleatória da lista de palavras
def getRandomWord(wordlist):
    wordIndex = random.randint(0, len(wordlist) - 1)
    return wordlist[wordIndex]


def displayBoard(missedLetters, correctLetters, secretWord):
    print(HANGMAN_PICS[len(missedLetters)])
    print()

    print('Letras erradas:', end=' ')
    for letter in missedLetters:
        print(letter, end=' ')
    print()

    blanks = '_' * len(secretWord)

    # Troca os espaço vázios com as letras acertadas
    for i in range(len(secretWord)): 
        if secretWord[i] in  correctLetters:
            blanks = blanks[:i] + secretWord[i] + blanks[i+1:]

    # mostra palavra que precisa acertar com espaços entre cada letra
    for letter in blanks: 
        print(letter, end=' ')
    print()


# retorna a letra que o jogador colocou. Isso está aqui para ter certeza que o jogador colocou uma letra e nada diferente disso
def getGuess(alreadyGuessed):
    while True:
        print()
        print('Digite uma letra!')
        guess = input()
        guess = guess.lower()  
        if len(guess) != 1:
            print('Só vale colocar uma letra por vez')        
        elif guess in alreadyGuessed:
            print('Essa letra já foi! Tente outra')
        elif guess not in 'abcdefghijklmnopqrstuvwxyz':
            print('Só valem letras!')
        else: 
            return guess 

# A função vai retornar True se o jogador quiser jogar de novo, fora isso vai retornar False 
def playAgain():
    print('Você quer jogar de novo? (sim ou não):', end=' ')
    return input().lower().startswith('s')


print('   F  O  R  C  A')
playerName = getplayerName()
missedLetters = ''
correctLetters = ''
secretWord = getRandomWord(choose_words_theme(ob, an, pf))
gameIsDone = False

while True:
    displayBoard(missedLetters, correctLetters, secretWord)
    # Deixar o jogador colocar as letras
    guess = getGuess(missedLetters + correctLetters)

    if guess in secretWord:
        correctLetters = correctLetters + guess

        # ver se o jogador ganhou 
        foundAllLetters = True
        for i in range(len(secretWord)):
            if secretWord[i] not in correctLetters:
                foundAllLetters = False
                break
        if foundAllLetters:
            print()
            print(f'Sim! A palavra era {secretWord.upper()}. Parabéns {playerName} você ganhou!!!')
            gameIsDone = True 
    else:
        missedLetters =  missedLetters + guess

        # verificar se o jogador tentou muitas vezes e perdeu
        if len(missedLetters) == len(HANGMAN_PICS) - 1:
             displayBoard(missedLetters, correctLetters, secretWord)
             print()
             print('Desculpa ' + playerName + ' você ficou sem tentativas :( \nDepois de ' +
                       str(len(missedLetters)) + ' tentativas e ' +
                   str(len(correctLetters)) + ' Acertos, a palavra era "' + secretWord + '"')
             gameIsDone = True

    #Perguntar se o jogador que jogar de novo (mas só caso o jogo já tiver terminado)
    if gameIsDone:
        if playAgain():
            missedLetters = ''
            correctLetters = ''
            gameIsDone = False
            secretWord = getRandomWord(choose_words_theme(ob, an, pf))
        else: 
            break
