import tkinter as tk
from tkinter import messagebox
import re

# Function to check password strength
def check_password_strength():
    password = entry.get()
    strength_points = 0

    if len(password) >= 8:
        strength_points += 1
    if re.search(r'[A-Z]', password):
        strength_points += 1
    if re.search(r'[a-z]', password):
        strength_points += 1
    if re.search(r'[0-9]', password):
        strength_points += 1
    if re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        strength_points += 1

    # Determine strength and color
    if strength_points <= 2:
        result = "Weak"
        color = "red"
    elif strength_points in [3, 4]:
        result = "Strong"
        color = "orange"
    else:
        result = "Strong"
        color = "green"

    result_label.config(text=f"Password Strength: {result}", fg=color)

# Setup GUI window
root = tk.Tk()
root.title("Password Strength Checker")
root.geometry("400x200")
root.resizable(False, False)

# Heading
tk.Label(root, text="Enter Your Password:", font=("Arial", 14)).pack(pady=10)

# Input field
entry = tk.Entry(root, show="*", font=("Arial", 14), width=30)
entry.pack(pady=5)

# Check button
tk.Button(root, text="Check Strength", command=check_password_strength, font=("Arial", 12)).pack(pady=10)

# Result label
result_label = tk.Label(root, text="", font=("Arial", 14))
result_label.pack()

# Run GUI loop
root.mainloop()
