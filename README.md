# Game
import random  # imports the random numbers used in the dmg and crt

yhp = 20  # hero health
score = 0
gold = 0
while yhp > 0:
    ghp = random.randint(7, 15)  # monster health
    r1 = random.randint(1, 5)
    if r1 == 1:
        monster = "Goblin"
    else:
        if r1 == 2:
            monster = "Highway Man"
        else:
            if r1 == 3:
                monster = "Wolf"
            else:
                if r1 == 4:
                    monster = "Green Slime"
                else:
                    if r1 == 5:
                        monster = "Pesky Bird"
    print("You see a", monster, "in your path! It has", ghp, "health!")
    action = input("What would you like to do? [atk] [run]")

    while ghp > 0 and action == "atk" and yhp > 0:  # loop runs if gob or user not dead and if user says atk
        dmg = random.randint(1, 5)
        crt = random.randint(1, 100)

        if action == "atk":
            if crt >= 85:  # checking for crt
                ghp = (ghp - dmg) - 3  # subtracting for crt damage
                print("\nYou hit the", monster, "for CRITICAL", dmg + 3, "damage!!")
                if ghp <= 0:
                    print("Good job! You slayed the", monster, "!!")
                    score = score + 1
                    gold = gold + random.randint(5, 15)

                else:
                    print("The", monster, "now has", ghp, "health remaining!")  # saying how much hp the gob has
                    print("The", monster, "is attacking!!")
                    yhp = (yhp - 2)  # gobs attack
                    if yhp <= 0:
                        print("YOU DIED")
                        print("You slayed", score, "monsters in your lifespan!")
                        print("Over the course of your adventure you earned", gold,"gold coins!")
                    else:
                        print("You now have", yhp, "health left!!")  # hp you have left
                        action = input("What would you like to do? [atk] [run]\n\n")
            else:
                ghp = ghp - dmg  # reg damage
                print("\nYou hit the", monster, "for", dmg, "damage!")
                if ghp <= 0:
                    print("Good job! You slayed the", monster, "!!")
                    score = score + 1
                    gold = gold + random.randint(1, 10)
                else:
                    print("The", monster, "now has", ghp, "health remaining!")
                    print("The", monster, "is attacking!!")
                    yhp = (yhp - 2)  # gob turn
                    if yhp <= 0:
                        print("\n- YOU DIED -")
                        print("You slayed", score, "monsters in your lifespan!")
                        print("Over the course of your adventure you earned", gold, "gold coins!")
                    else:
                        print("You now have", yhp, "health left!!")
                        action = input("What would you like to do? [atk] [run]")
if action == "run":  # if user types run than ends the loop
    print("Wow! It was only a little ", monster, "... What a scaredy cat!"
