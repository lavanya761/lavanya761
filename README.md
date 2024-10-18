import random
import tkinter as tk
from tkinter import messagebox

# Choices
choices = ["rock", "paper", "scissors"]

# Initialize scores
user_score = 0
computer_score = 0

# Function to play a round
def play(user_choice):
    global user_score, computer_score

    computer_choice = random.choice(choices)
    result = ""
    
    # Determine the winner
    if user_choice == computer_choice:
        result = "It's a tie!"
    elif (user_choice == "rock" and computer_choice == "scissors") or \
         (user_choice == "scissors" and computer_choice == "paper") or \
         (user_choice == "paper" and computer_choice == "rock"):
        result = "You win!"
        user_score += 1
    else:
        result = "You lose!"
        computer_score += 1
    
    # Display result
    messagebox.showinfo("Result", f"You chose {user_choice}, computer chose {computer_choice}.\n{result}")
    score_label.config(text=f"User: {user_score}  Computer: {computer_score}")

# Setup GUI
window = tk.Tk()
window.title("Rock, Paper, Scissors")

# Score label
score_label = tk.Label(window, text="User: 0  Computer: 0", font=('Arial', 14))
score_label.pack(pady=10)

# Buttons for user choices
for choice in choices:
    button = tk.Button(window, text=choice.capitalize(), width=10, font=('Arial', 14),
                       command=lambda choice=choice: play(choice))
    button.pack(pady=5)

# Start the GUI loop
window.mainloop()
