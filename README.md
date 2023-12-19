# Imports
import requests
import random
import time

from colorama import Fore

# Startup messages 
print(Fore.YELLOW + f"*Made by ilAHMq. Big thanks to V3.*")
print(Fore.WHITE + f"*This is my passion project, but I'm not sure if I'll still have the passion to update it in the future.*")
print(Fore.LIGHTGREEN_EX + f"*The tool will start searching for usernames after 5 seconds and will pause for 10 seconds if it finds an available username..*")
print(Fore.CYAN + f"*Current version: v1.0.*")
print(Fore.LIGHTMAGENTA_EX + f"**Instagram: https://www.instagram.com/ilradnabq/")
print(Fore.LIGHTGREEN_EX + f"**Some usernames might not work due to Instagram's username rules, such as those that start with a period or an underscore. Please remember that this is version 1.0.")

# Stops for 5s then starts looking for Usernames
time.sleep(5)

# Loops the process over and over until the program is closed.
while True:
    user = ""

    # The characters, symbols and such that he will use as the Username and how many digits is the Username
    for character in random.choices("abcdefghijklmnopqrstuvwxyz0123456789._", k=4):
           user = user + character

    # {user} is the Username that the tool came up with. It'll search for the Username and see if it's available or not 
    response = requests.get(f"https://instagram.com/{user}/")

    # Tells you if the Username is taken or untaken
    if (response.status_code == 200):
            print(Fore.RED + f"Invalid username. Taken: {user}" + Fore.RESET)
    elif (response.status_code == 404):
            print(Fore.GREEN + f"Valid username. Untaken: {user}" + Fore.RESET)
            time.sleep(10)
    # Makes the tool stop for 120s if it gets blocked by Instagram        
    else:
           print(Fore.CYAN + f"Request blocked by: Instagram. The tool will retry to send a request to Instagram to continue looking for usernames after 120s." + Fore.RESET)
           time.sleep(120)
