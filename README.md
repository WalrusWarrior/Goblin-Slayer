# Game
import random # imports the random numbers used in the dmg and crt
yhp = 20  # hero health
ghp = 10  # monster health
r1 = random.randint(1,3)
if(r1 == 1):
  monster = "Goblin"
else:
    if(r1 == 2):
      monster = "Highway Man"
    else:
      monster = "Wolf"
print("You see a", monster, "in your path! ")
action = input("What would you like to do? 'atk' 'str' 'run'")
while ghp > 0 and action == "atk" or "str" and yhp > 0: # loop runs if gob or user not dead and if user says atk
  dmg = random.randint(1, 4)
  dmg2 = random.randint(0,7) # strong attack, takes some health away cus its so powerful
  crt = random.randint(1, 100)
  if action == "str":
        if crt >= 85:  # checking for crt
            ghp = (ghp - dmg2) - 2  # subtracting for crt damage
            print("You hit the", monster, "for CRITICAL", dmg2 + 2, " damage!!")
            print("However, you take 2 damage because of your strong attack.")
            if ghp <= 0:
                print("Good job! You slayed the", monster, "!!")
            else:
                print("The", monster, "now has", ghp, " health remaining!")          # saying how much hp the gob has
                print("The", monster, "is attacking!!")
                yhp = (yhp - 2 - 3)                                            # gobs attack
                if yhp <= 0:
                    print("YOU DIED")
                else:
                    print("You now have", yhp, "health left!!")                 # hp you have left
                    action = input("What would you like to do? 'atk' 'str' 'run'")
  else:
    if action == "atk":
        if crt >= 85:  # checking for crt
            ghp = (ghp - dmg) - 2  # subtracting for crt damage
            print("You hit the", monster, "for CRITICAL", dmg + 2, " damage!!")
            if ghp <= 0:
                print("Good job! You slayed the", monster, "!!")
            else:
                print("The", monster, "now has", ghp, " health remaining!")          # saying how much hp the gob has
                print("The", monster, "is attacking!!")
                yhp = (yhp - 2)                                            # gobs attack
                if yhp <= 0:
                    print("YOU DIED")
                else:
                    print("You now have", yhp, "health left!!")                 # hp you have left
                    action = input("What would you like to do? 'atk' 'str' 'run'")
        else:
            ghp = ghp - dmg      # reg damage
            print("You hit the", monster)
            if ghp <= 0:
                print("Good job! You slayed the", monster,"!!")
            else:
                print("The", monster, "now has", ghp, " health remaining!")
                print("The", monster, "is attacking!!")
                yhp = (yhp - 2)                              # gob turn
                if yhp <= 0:
                    print("YOU DIED")
                else:
                    print("You now have", yhp, "health left!!")
                    action = input("What would you like to do? 'atk' 'str' 'run'")
if action == "run":    # if user types run than ends the loop
    print("Wow! It was only a little ", monster, "... What a scaredy cat!")
