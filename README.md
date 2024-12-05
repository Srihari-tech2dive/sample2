import math

def binary_search_game():
    print("Welcome to the Binary Search Guessing Game!")

    # Step 1: Get the range of numbers from the user
    low = int(input("Enter the lower bound of the range: "))
    high = int(input("Enter the upper bound of the range: "))
    
    # Validate the range
    if low >= high:
        print("The lower bound must be less than the upper bound. Please try again.")
        return

    # Step 2: Calculate the maximum number of attempts needed using binary search
    total_numbers = high - low + 1  # total numbers in the range
    max_attempts = math.ceil(math.log2(total_numbers))  # Calculate the binary search depth (log2)

    # Inform the user about the maximum attempts needed
    print(f"\nIt will take at most {max_attempts} attempts to guess a number between {low} and {high} using binary search.")

    # Step 3: Start the binary search guessing game
    attempts = 0
    while low <= high:
        attempts += 1
        guess = (low + high) // 2  # Program guesses the middle number
        
        # Ask the user if the guess is too high, too low, or correct
        print(f"\nAttempt {attempts}: Is your number {guess}?")
        feedback = input("Enter 'higher' if your number is higher, 'lower' if it's lower, or 'correct' if I guessed it right: ").lower()
        
        if feedback == 'correct':
            print(f"\nI found your number {guess} in {attempts} attempts!")
            break
        elif feedback == 'higher':
            low = guess + 1  # The target is higher, so adjust the range
        elif feedback == 'lower':
            high = guess - 1  # The target is lower, so adjust the range
        else:
            print("Invalid input. Please enter 'higher', 'lower', or 'correct'.")
            
# Run the game
