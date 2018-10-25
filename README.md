# Game
import random # imports the random numbers used in the dmg and crt
yhp = 20  # hero health
ghp = 10  # gob health
dmg = random.randint(1, 4)           # possible attack dmg rand
crt = random.randint(1, 100) # crits range
r1 = random.randint(1,3)
if(r1 == 1)
monster = "goblin"
else
  if(r1 == 2)
    monster = "Highway man"
    else
      monster = "wolf"
print("you see a", monster, "in your path! ")
action = input("would you like to run or atk?")
while ghp > 0 and action == "atk" and yhp > 0: # loop runs if gob or user not dead and if user says atk
    if action == "atk":
        if crt >= 98:  # checking for crt
            ghp = (ghp - dmg) - 2  # subtracting for crt damage
            print("you hit the", monster, "for CRITICAL damage!!")
            if ghp <= 0:
                print("Good job you slayed the", monster, "!!")
            else:
                print("The", monster, "now has", ghp, " health left!")          # saying how much hp the gob has
                print("The", monster, "is attacking!!")
                yhp = (yhp - 2)                                            # gobs attack
                if yhp <= 0:
                    print("YOU DIED")
                else:
                    print("you now have", yhp, "left!!")                 # hp you have left
                    action = input("would you like to run or atk?")
        else:
            ghp = ghp - dmg      # reg damage
            print("you hit the", monster)
            if ghp <= 0:
                print("Good job you slayed the", monster,"!!")
            else:
                print("The", monster, "now has", ghp, " health left!")
                print("The", monster, "is attacking!!")
                yhp = (yhp - 2)                              # gob turn
                if yhp <= 0:
                    print("YOU DIED")
                else:
                    print("you now have", yhp, "left!!")
                    action = input("would you like to run or atk?")
if action == "run":    # if user types run than ends the loop
    print("Wow its was only a", monster, "...... what a scaredy cat!")
