# Binary Search

Author: Jeffery John
#easy #General-skills #picoCTF2024 #shell #browser_web_shell #ls
#### Description

Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses. Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools! You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/5/challenge.zip)

Additional details will be available after launching your challenge instance.
`ssh -p 53412 ctf-player@atlas.picoctf.net` Using the password `1ad5be0d`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

```sh
#!/bin/bash
            # Generate a random number between 1 and 1000
            target=$(( (RANDOM % 1000) + 1 ))

            echo "Welcome to the Binary Search Game!"
            echo "I'm thinking of a number between 1 and 1000."

            # Trap signals to prevent exiting
            trap 'echo "Exiting is not allowed."' INT
            trap '' SIGQUIT
            trap '' SIGTSTP

            # Limit the player to 10 guesses
            MAX_GUESSES=10
            guess_count=0

            while (( guess_count < MAX_GUESSES )); do
                read -p "Enter your guess: " guess

                if ! [[ "$guess" =~ ^[0-9]+$ ]]; then
                    echo "Please enter a valid number."
                    continue
                fi

                (( guess_count++ ))

                if (( guess < target )); then
                    echo "Higher! Try again."
                elif (( guess > target )); then
                    echo "Lower! Try again."
                else
                    echo "Congratulations! You guessed the correct number: $target"

                    # Retrieve the flag from the metadata file
                    flag=$(cat /challenge/metadata.json | jq -r '.flag')
                    echo "Here's your flag: $flag"
                    exit 0  # Exit with success code
                fi
            done

            # Player has exceeded maximum guesses
            echo "Sorry, you've exceeded the maximum number of guesses."
            exit 1  # Exit with error code to close the connection
```

modified code # Commented out traps that might not be supported`# trap '' SIGQUIT`
`# trap '' SIGTSTP`
and Instead of retrieving a flag from a file, I've added a placeholder message `FLAG{congrats_you_guessed_it}` that gets printed when the user guesses the correct number

```sh
#!/bin/bash

# Generate a random number between 1 and 1000
target=$(( (RANDOM % 1000) + 1 ))

echo "Welcome to the Binary Search Game!"
echo "I'm thinking of a number between 1 and 1000."

# Trap signals to prevent exiting
trap 'echo "Exiting is not allowed."' INT

# Commented out traps that might not be supported
# trap '' SIGQUIT
# trap '' SIGTSTP

# Limit the player to 10 guesses
MAX_GUESSES=10
guess_count=0

while (( guess_count < MAX_GUESSES )); do
    read -p "Enter your guess: " guess

    if ! [[ "$guess" =~ ^[0-9]+$ ]]; then
        echo "Please enter a valid number."
        continue
    fi

    (( guess_count++ ))

    if (( guess < target )); then
        echo "Higher! Try again."
    elif (( guess > target )); then
        echo "Lower! Try again."
    else
        echo "Congratulations! You guessed the correct number: $target"

        # Placeholder for flag (since file and jq are not available)
        echo "Here's your flag: FLAG{congrats_you_guessed_it}"
        exit 0  # Exit with success code
    fi
done

# Player has exceeded maximum guesses
echo "Sorry, you've exceeded the maximum number of guesses."
exit 1  # Exit with error code to close the connection

```

online
```sh
ssh -p 53412 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 900
Lower! Try again.
Enter your guess: 750
Lower! Try again.
Enter your guess: 650
Higher! Try again.
Enter your guess: 710
Lower! Try again.
Enter your guess: 690
Lower! Try again.
Enter your guess: 680
Higher! Try again.
Enter your guess: 685
Lower! Try again.
Enter your guess: 682
Congratulations! You guessed the correct number: 682
Here's your flag: picoCTF{g00d_gu355_3af33d18}
Connection to atlas.picoctf.net closed.
```