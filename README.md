import random  # imports the random numbers used in the dmg and crt

yhp = 20  # hero health
score = 0
gold = 0
potions = 0
actionlist = ["[atk]","[run]","[inv]","[esc]"]
while yhp > 0:
    ghp = random.randint(7, 15)  # monster health

    # Monster Selection
    mon = ["Goblin", "Highway Man", "Wolf", "Green Slime", "Pesky Bird"]
    m_ran = random.SystemRandom()
    monster = m_ran.choice(mon) # Holds the value of the monster until death.
    print("You see a", monster, "in your path! It has", ghp, "health!")

    action = input("What would you like to do? " + str(actionlist))
    if gold == 0 and potions == 0 and action == "inv":
        while action == "inv":
            print("\nyou have nothing in your inventory")
            action = input("What would you like to do? " + str(actionlist))
                                                                 # inventory lets you see potions + gold
    else:  # inventory
        if action == "inv":
            while action == "inv":
                print("you have:\n", gold, "gold coins\n", potions, "potions")
                action = input("What would you like to do? [atk] [run] [inv] [esc]")

    if gold >= 4 and action == "esc":  # escape allows you to run away from the monster but you leave behind some gold
        gold = gold - goldY
        print("\nYou escaped the monster but you lost", goldY, "gold coins!\t\t\t\t\t-", goldY, "GOLD")

    else:
        while action != "atk" and action != "run" and action != "inv" and action == "esc":
            print("You cannot escape from this monster!!")
            action = input("What would you like to do? " + str(actionlist))
            if gold == 0 and potions == 0 and action == "inv":
                while action == "inv":
                    print("\nyou have nothing in your inventory")
                    action = input("What would you like to do? [atk] [run] [inv] [esc]")
                                                     # this second inventory stops the monster from cycling if you go from esc to inventory
            else:  # inventory
                if action == "inv":
                    while action == "inv":
                        print("you have:\n", gold, "gold coins\n", potions, "potions")
                        action = input("What would you like to do? [atk] [run] [inv] [esc]")



    while action != "atk" and action != "run" and action != "inv" and action != "esc":
        print("Invalid input, Please try again!")
        action = input("What would you like to do? [atk] [run] [inv] [esc]")

    while ghp > 0 and action == "atk" and yhp > 0:  # loop runs if either are alive, atk and inv work
        dmg = random.randint(1, 5)     # the attack damage
        gdmg = random.randint(2, 4)    # the monster damage
        crt = random.randint(1, 100)   # the crit random
        goldY = random.randint(2, 4)   # gold you have the chance of losing
        goldM = random.randint(3, 5)   # gold monster gives out

        if action == "atk":
            if crt >= 85:  # checking for crt
                ghp = (ghp - dmg) - 3  # subtracting for crt damage
                print("\nYou hit the", monster, "for CRITICAL", dmg + 3, "damage!!")
                if ghp <= 0:
                    print("Good job! You slayed the", monster, "\t\t\t\t\t+", goldM, "GOLD")
                    score = score + 1
                    gold = gold + goldM
                    if monster == "Highway Man" or monster == "Goblin":
                        potions = potions + 1
                        print("You found a potion in their satchel!\t\t\t\t\t+1 HP POTION")
                else:
                    print("The", monster, "now has", ghp, "health remaining!")  # saying how much hp the gob has
                    print("The", monster, "is attacking!!")
                    yhp = (yhp - gdmg)  # gobs attack
                    if yhp <= 0:
                        print("YOU DIED")
                        print("You slayed", score, "monsters in your lifespan!")
                        print("Over the course of your adventure you earned", gold, "gold coins!")
                        print("You died with", potions, "unused potion(s)!")
                    else:
                        print("You now have", yhp, "health left!!")  # hp you have left
                        action = input("What would you like to do? " + str(actionlist))
                        if gold >= 4 and action == "esc":  # escape allows you to run away from the monster but you leave behind some gold
                            gold = gold - goldY
                            print("\nYou escaped the monster but you lost", goldY, "gold coins!\t\t\t\t\t-", goldY,
                                  "GOLD")

                        else:
                            while action != "atk" and action != "run" and action != "inv" and action == "esc":
                                print("You cannot escape from this monster!!")
                                action = input("What would you like to do? " + str(actionlist))
                                if gold == 0 and potions == 0 and action == "inv":
                                    while action == "inv":
                                        print("\nyou have nothing in your inventory")
                                        action = input("What would you like to do? " + str(actionlist))

                                else:  # inventory
                                    if action == "inv":
                                        while action == "inv":
                                            print("you have:\n", gold, "gold coins\n", potions, "potions")
                                            action = input("What would you like to do? " + str(actionlist))

                        while action != "atk" and action != "run" and action != "inv" and action != "esc":
                            print("Invalid input, Please try again!")
                            action = input("What would you like to do? " + str(actionlist))


            else:
                ghp = ghp - dmg  # reg damage
                print("\nYou hit the", monster, "for", dmg, "damage!")
                if ghp <= 0:
                    print("Good job! You slayed the", monster, "\t\t\t\t\t+", goldM, "GOLD")
                    score = score + 1
                    gold = gold + goldM
                    if monster == "Highway Man" or monster == "Goblin":
                        potions = potions + 1
                        print("You found a potion in their satchel!\t\t\t\t\t+1 HP POTION")
                else:
                    print("The", monster, "now has", ghp, "health remaining!")
                    print("The", monster, "is attacking!!")
                    yhp = (yhp - gdmg)  # gob turn
                    if yhp <= 0:
                        print("\n- YOU DIED -")
                        print("You slayed", score, "monsters in your lifespan!")
                        print("Over the course of your adventure you earned", gold, "gold coins!")
                        print("You died with", potions, "unused potion(s)!")
                    else:
                        print("You now have", yhp, "health left!!")
                        action = input("What would you like to do? " + str(actionlist))
                        if gold >= 4 and action == "esc":  # escape allows you to run away from the monster but you leave behind some gold
                            gold = gold - goldY
                            print("\nYou escaped the monster but you lost", goldY, "gold coins!\t\t\t\t\t-", goldY,
                                  "GOLD")

                        else:
                            while action != "atk" and action != "run" and action != "inv" and action == "esc":
                                print("You cannot escape from this monster!!")
                                action = input("What would you like to do? " + str(actionlist))
                                if gold == 0 and potions == 0 and action == "inv":
                                    while action == "inv":
                                        print("\nyou have nothing in your inventory")
                                        action = input("What would you like to do? " + str(actionlist))

                                else:  # inventory
                                    if action == "inv":
                                        while action == "inv":
                                            print("you have:\n", gold, "gold coins\n", potions, "potions")
                                            action = input("What would you like to do? " + str(actionlist))
                        while action != "atk" and action != "run" and action != "inv" and action != "esc":
                            print("Invalid input, Please try again!")
                            action = input("What would you like to do? " + str(actionlist))



    else:
        if action == "run":
            yhp = 0
            print("\n- YOU RAN AWAY -")
            print("You slayed", score, "monsters in your journey, before wimping out!")
            print("However, you were able to find", gold, "gold coins!")
            print("You ran off with", potions, "unused potion(s)!")
