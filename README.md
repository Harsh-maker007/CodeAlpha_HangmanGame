# CodeAlpha_HangmanGame
import random

# Step 1: Predefined word list
words = ["apple", "tiger", "dance", "train", "plant"]

# Step 2: Pick a random word
secret_word = random.choice(words)
guessed_letters = []
tries = 6

# Step 3: Game loop
print(" Welcome to HUNGAMA! Guess the word letter by letter.")
print(f"You have {tries} incorrect guesses allowed.\n")

while tries > 0:
    display_word = ""
    for letter in secret_word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "
    print("Word:", display_word.strip())

    # Check if the player has guessed the word
    if all(letter in guessed_letters for letter in secret_word):
        print("\n Congratulations! You guessed the word:", secret_word)
        break

    # Ask for user input
    guess = input("Guess a letter: ").lower()

    # Check valid input
    if len(guess) != 1 or not guess.isalpha():
        print("Enter a single alphabet letter.\n")
        continue

    # Check if already guessed
    if guess in guessed_letters:
        print(" You've already guessed that letter.\n")
        continue

    guessed_letters.append(guess)

    # Check guess correctness
    if guess in secret_word:
        print("Good guess!\n")
    else:
        tries -= 1
        print(f"Wrong guess! Tries left: {tries}\n")

# Step 4: End game
if tries == 0:
    print(" Game Over! The word was:", secret_word)
