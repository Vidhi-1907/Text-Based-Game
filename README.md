# Text-Based-Game


# This is marvel universe text based game.
# This will led you to on different adventures with different charcters.
# Name: Vidhi Babariya
# Date: 10/06/2024


import time

# Function headers
def display_menu(character_selected):
    """
    Displays the main menu options.
    """
    print("\nMarvel Universe Game Menu")
    if not character_selected:
        print("1. Choose a Character")
    if character_selected:
        print("2. Go on an Adventure")
    print("3. Quit")

def choose_character():
    """
    Allows the player to choose a character.
    """
    characters = ["Spider-Man", "Black Widow", "Thor", "Iron Man"]
    print("\nChoose your character:")
    for index, character in enumerate(characters, start=1):
        print(f"{index}. {character}")
    
    while True:
        try:
            choice = int(input("Enter the number of your choice: "))
            if 1 <= choice <= len(characters):
                print_with_delay(f"\nYou have chosen {characters[choice-1]}! Prepare yourself for an epic adventure...")
                time.sleep(1)
                print_with_delay("The fate of the Marvel Universe lies in your hands.")
                return characters[choice-1]
            else:
                print("Invalid choice. Please try again.")
        except ValueError:
            print("Invalid input. Please enter a number.")

def adventure_event(character):
    """
    Simulates an adventure event based on the chosen character.
    """
    events = {
        "Spider-Man": [
            ("Spider-Man needs help defusing a bomb in the city. Will you assist?", 
             [("Assist", "Your cautious approach helps you identify a secondary trap. Crisis averted!"),
              ("Ignore", "You refuse to help. Later, you see the news of Spider-Man's heroic solo effort and feel a pang of regret.")]),
            ("Hostages are trapped in a building. Do you help Spider-Man in rescuing them?", 
             [("Rescue", "You successfully rescue the hostages together with Spider-Man."),
              ("Avoid", "You refuse, and Spider-Man manages to save the hostages alone.")]),
            ("The Vulture is wreaking havoc in the city. Do you assist Spider-Man in capturing him?", 
             [("Assist", "You provide cover fire, helping Spider-Man subdue the Vulture."),
              ("Ignore", "You refuse, and Spider-Man struggles but eventually captures the Vulture alone.")]),
            ("Spider-Man discovers a hidden lair of the Sinister Six. Do you join him to investigate?", 
             [("Investigate", "Your stealth helps you avoid detection and gather valuable intel."),
              ("Avoid", "You stay behind, missing out on the action.")]),
            ("A runaway train threatens the city. Do you join Spider-Man to stop it?", 
             [("Help", "You and Spider-Man stop the train just in time."),
              ("Avoid", "You refuse, and Spider-Man barely manages to stop the train alone.")]),
        ],
        "Black Widow": [
            ("Black Widow needs your help on a covert mission. Do you join?", 
             [("Join", "Your stealthy approach avoids detection, and the mission is a success."),
              ("Refuse", "Black Widow completes the mission solo, but you wonder what might have been.")]),
            ("There's a Hydra base that needs infiltrating. Will you assist Black Widow?", 
             [("Infiltrate", "You successfully infiltrate the base and gather crucial information."),
              ("Decline", "You refuse, and Black Widow goes alone, but she faces great difficulty.")]),
            ("A plot to assassinate a world leader has been uncovered. Do you help stop it?", 
             [("Prevent", "Your ambush plan works perfectly, and you prevent the assassination."),
              ("Refuse", "You refuse, and Black Widow manages to stop the assassination alone.")]),
            ("Stolen SHIELD intel needs retrieving. Do you assist?", 
             [("Retrieve", "You retrieve the intel without raising any alarms."),
              ("Decline", "Black Widow retrieves the intel alone, but it was a close call.")]),
            ("A Hydra operative needs to be captured. Will you help?", 
             [("Capture", "Your teamwork leads to the successful capture of the operative."),
              ("Decline", "You refuse, and Black Widow captures the operative, but it was a tough battle.")]),
        ],
        "Thor": [
            ("Asgard is under attack. Will you join Thor in defending it?", 
             [("Defend", "You and Thor repel the invaders and save Asgard."),
              ("Ignore", "You refuse, and Thor defends Asgard with the help of other warriors.")]),
            ("A powerful relic is missing. Do you help Thor in retrieving it?", 
             [("Retrieve", "Your adventure leads you to recover the relic successfully."),
              ("Ignore", "Thor retrieves the relic alone, but it was a perilous journey.")]),
            ("Thor invites you to a duel of strength. Do you accept?", 
             [("Accept", "Your clever strategy earns Thor's admiration, though you don't win the duel."),
              ("Decline", "You respectfully decline. Thor acknowledges your decision.")]),
            ("A secret realm has been discovered. Do you join Thor in exploring it?", 
             [("Explore", "Your cautious approach helps you navigate the dangers."),
              ("Ignore", "You stay behind, missing out on the discovery.")]),
            ("Loki is causing trouble again. Do you assist Thor in stopping him?", 
             [("Help", "Together, you outsmart Loki and foil his plans."),
              ("Ignore", "Thor stops Loki alone, but it was a difficult task.")]),
        ],
        "Iron Man": [
            ("Iron Man is testing a new suit. Do you help?", 
             [("Help", "Your suggestion improves the suit's safety protocols, earning Tony's respect."),
              ("Ignore", "Iron Man respects your choice but you miss out on an incredible experience.")]),
            ("A secret Hydra lab has been discovered. Do you help investigate?", 
             [("Investigate", "Your covert approach helps you gather critical data."),
              ("Ignore", "You refuse, and Iron Man faces the dangers alone.")]),
            ("Tony Stark needs help upgrading his AI system. Do you assist?", 
             [("Assist", "Your coding skills help improve the AI significantly."),
              ("Ignore", "You refuse, and Iron Man upgrades the AI alone.")]),
            ("Iron Man needs backup in a fight against the Mandarin. Do you join?", 
             [("Help", "Together, you defeat the Mandarin and save the day."),
              ("Ignore", "You refuse, and Iron Man struggles but manages to defeat the Mandarin.")]),
            ("A new villain threatens the city. Do you help Iron Man stop them?", 
             [("Fight", "Your teamwork leads to the villain's defeat."),
              ("Ignore", "Iron Man stops the villain, but it was a tough battle.")]),
        ],
    }

    for event in events[character]:
        print_with_delay(f"\n{event[0]}")
        for index, option in enumerate(event[1], start=1):
            print(f"{index}. {option[0]}")
        
        while True:
            try:
                choice = input("Enter your choice: ")
                if choice.lower() in [opt[0].lower() for opt in event[1]]:
                    print_with_delay(next(opt[1] for opt in event[1] if opt[0].lower() == choice.lower()))
                    break
                elif choice.lower() == "quit":
                    return "quit"
                else:
                    print("Invalid choice. Please try again.")
            except ValueError:
                print("Invalid input. Please enter a valid choice.")
        
        if choice.lower() in ["refuse", "ignore", "decline"]:
            print_with_delay("You have refused to continue the adventure.")
            return "refuse"

    print_with_delay("Your adventure has come to an end.")
    return "end"

def print_with_delay(sentence):
    """
    Prints a sentence with a delay between each word for dramatic effect.
    """
    for word in sentence.split():
        print(word, end=' ', flush=True)
        time.sleep(0.3)
    print()

def number_selection():
    """
    Prompts the player to select a number at the start of the game.
    """
    print("Welcome to the Marvel Universe Game!")
    print("Before we begin, please select a number between 1 and 10.")
    while True:
        try:
            number = int(input("Enter your number: "))
            if 1 <= number <= 10:
                print_with_delay(f"You selected {number}. Let's see what adventures await you...")
                time.sleep(1)
                break
            else:
                print("Invalid choice. Please choose a number between 1 and 10.")
        except ValueError:
            print("Invalid input. Please enter a number.")

def main():
    """
    Main function to run the game.
    """
    number_selection()
    character = None
    character_selected = False
    while True:
        display_menu(character_selected)
        try:
            choice = int(input("Enter the number of your choice: "))
            if not character_selected and choice == 1:
                character = choose_character()
                character_selected = True
            elif character_selected and choice == 2:
                result = adventure_event(character)
                if result in ["refuse", "end"]:
                    print_with_delay("Do you want to select a new character or quit the game?")
                    print("1. Select a new character")
                    print("2. Quit the game")
                    while True:
                        try:
                            choice = int(input("Enter your choice: "))
                            if choice == 1:
                                character = choose_character()
                                break
                            elif choice == 2:
                                print_with_delay("Thank you for playing! Goodbye!")
                                return
                            else:
                                print("Invalid choice. Please try again.")
                        except ValueError:
                            print("Invalid input. Please enter a number.")
            elif choice == 3:
                print_with_delay("Thank you for playing! Goodbye!")
                break
            else:
                print("Invalid choice. Please try again.")
        except ValueError:
            print("Invalid input. Please enter a number.")

# Run the game
if __name__ == "__main__":
    main()
