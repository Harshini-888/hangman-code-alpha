import random

# Predefined word list (5 words)
words = ["python", "laptop", "keyboard", "mouse", "monitor"]

# Select random word
word = random.choice(words)

guessed_letters = []
incorrect_guesses = 0
max_attempts = 6

print(" Welcome to Hangman Game!")

# Game loop
while incorrect_guesses < max_attempts:
    display_word = ""

    # Display guessed letters and underscores
    for letter in word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word)

    # Check win condition
    if "_" not in display_word:
        print("🎉 Congratulations! You guessed the word:", word)
        break

    guess = input("Enter a letter: ").lower()

    # Validate input
    if len(guess) != 1 or not guess.isalpha():
        print("⚠ Please enter a single valid letter.")
        continue

    if guess in guessed_letters:
        print("⚠ You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess not in word:
        incorrect_guesses += 1
        print(" Wrong guess!")
        print("Remaining attempts:", max_attempts - incorrect_guesses)

else:
    print("Game Over! The word was:", word)
