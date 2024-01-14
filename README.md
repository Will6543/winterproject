import random
import time
import os

#clear function
def clear():
  os.system('cls||clear')


#saving coins earnt from previously playing
f = open("coins.txt", "a")
f.close()
f = open("coins.txt", "r")
coinString = f.read()
if coinString == "":
  coins = 1000
  coinString = str(coins)
  f = open("coins.txt", "w")
  f.write(coinString)
  f.close()
else:
  coins = int(coinString)
f.close()
yourteamrating = 75

# defender name, position, rating 
defenderName  = ["M.Kante","D.Johnson","S.Miller","J.Chen","W.He","M.Das","L.Stone", "E.Martin", "J.Walker", "T.White", "N.Harris", "F.Anderson", "M.Thompson", "C.Mitchell", "R.Wright", "S.Baker", "L.Parker", "P.Roberts"]
defenderCountry = ["Ethiopia","England","England","China","China","India","England", "Spain", "Italy", "Canada", "Argentina", "South Korea", "Egypt", "Sweden", "Netherlands", "Russia", "Greece", "Chile"]
defenderPosition = ["DEF","DEF","DEF","DEF","DEF","DEF","DEF", "DEF","DEF","DEF","DEF","DEF","DEF","DEF","DEF","DEF","DEF"]
defenderRating = ['75', '79', '82', '81', '91', '71', '80', '62', '75', '69', '73', '78', '67', '76', '70', '61', '71', '80']
defenderChance = [1, 1, 2, 2, 3, 1, 1]

# midfielder name, position, rating
midfielderName  = ["S.Steven","D.Bolton","A.Ayalew","M.Yousef","M.Zacharia","L.Moss","L.Son", "L.Williams", "Q.Andrews", "M.Smith", "M.Brown", "M.Jones", "M.Davis", "M.Garcia", "Y.Miller", "J.Wilson", "O.Anderson", "W.Thomas"]
midfielderCountry = ["England","England","Ghana","Egypt","India","England","South Korea", "England", "Scotland", "China", "Sweden", "France", "France", "Germany", "Senegal", "Saudi Arabia", "India","England"]
midfielderPosition = ["MID","MID","MID","MID","MID","MID","MID", "MID", "MID", "MID", "MID", "MID", "MID", "MID", "MID", "MID", "MID"]
midfielderRating = ['72', '83', '80', '69', '94', '73', '88', '73' ,'78', '81', '79', '72', '75', '71', '70', '72', '65', '74']

# attacker name, position, rating 
attackerName  = ["K.Jayawardene","M.Tucker","L.Das","V.Kumar","J.Edwards","M.Star","S.Khalil", "A.Johnson", "S.Williams", "M.Brown", "J.Taylor", "K.Jones", "D.Miller", "H.Davis", "B.Wilson", "G.Evans", "L.Anderson", "C.Martinez"]
attackerCountry = ["Sri Lanka","England","India","India","England","Poland","Egypt", "U.S.A.", "England", "France", "Germany", "Japan", "Canada", "Brazil", "Australia", "China", "India", "Mexico"]
attackerPosition = ["ATT","ATT","ATT","ATT","ATT","ATT","ATT", "ATT", "ATT", "ATT", "ATT", "ATT", "ATT", "ATT", "ATT", "ATT", "ATT", "ATT"]
attackerRating = ['75', '79', '82', '81', '91', '71', '80', '63', '78', '72', '66', '70', '75', '61', '69', '79', '68', '71']

# teams
teamName = ["Leamington Lions","Warwick Warriors","Stratford Saints","Croydon Cats","Telford Tigers","Coventry Cougars","Birmingham Bears","London Leopards","Manchester Mandems","Bristol Bulls","Oxford Opponents","Sheffield Spiders","Cambridge Cheetahs"]
teamRating = [60, 91, 90, 85, 81, 73, 70, 65, 60, 83, 50, 76, 86]

# function for home page
def homePage(coins):
  clear()
  print("")
  print("HOME")
  print("")
  print("Play     - 1")
  print("Store    - 2")
  print("My Squad - 3 (under construction)")
  print("")
  print("Current Coin Balance: " + str(coins))
  inputNum = input("Enter the number of what you would like to do! ")
  while inputNum != "1" and  inputNum != "2" and inputNum != "3":
    print("")
    print("Please enter a valid option!")
    time.sleep(1.5)
    clear()
    print("")
    print("HOME")
    print("")
    print("Play     - 1")
    print("Store    - 2")
    print("My Squad - 3 (under construction)")
    print("")
    print("Current Coin Balance: " + str(coins))
    inputNum = input("Enter the number of what you would like to do! ")
  if inputNum == "2":
    print(storePage(coins))
  elif inputNum == "1":
    print(playPage(coins))
  elif inputNum == "3":
    print("")
    print("Oops! It looks like this feature is still in development! Try again soon!")
    time.sleep(3)
    print(homePage(coins))

# function for store page
def storePage(coins):
  clear()
  print("")
  print("STORE")
  print("")
  print("Defender Pack - 300 coins    - 1")
  print("Midfielder Pack - 300 coins  - 2")
  print("Attacker Pack - 300 coins    - 3")
  print("Return to Home               - 4")
  print("")
  print("Current Coin Balance: " + str(coins))
  inputNum = input("Enter the number of what you would like to do! ")
  while inputNum != "1" and inputNum != "2" and inputNum != "3" and inputNum != "4":
    print("")
    print("Please enter a valid option!")
    print("")
    inputNum = input("Enter the number of what you would like to do! ")
  if inputNum == "1":
    print(defenderPack(coins))
  elif inputNum == "2":
    print(midfielderPack(coins))
  elif inputNum == "3":
    print(attackerPack(coins))
  elif inputNum == "4":
    print(homePage(coins))



# set up the random pack for defenders, midfielders and attackers
def defenderChance():
  import random
  defpickNum = random.randint(0,17)
  return defpickNum

def midfielderChance():
  import random
  midpickNum = random.randint(0,17)
  return midpickNum

def attackerChance():
  import random
  attpickNum = random.randint(0,17)
  return attpickNum

# set up the packing methods for all positions
def defenderPack(coins):
  decision = input("Are you sure you would like to purchase this defender pack? (y/n) ")
  while decision != "y" and decision != "n":
    print("")
    print("Please enter a valid option!")
    print("")
    decision = input("Are you sure you would like to purchase this defender pack? (y/n) ")
  import time
  if coins < 300:
    time.sleep(1)
    print("")
    print("Loading...")
    time.sleep(1)
    print("")
    print("ERROR: You do not have enough coins to purchase this item!")
    print("")
    time.sleep(3)
    decision = "n"
  if decision == "y":
    defenderNum = defenderChance()
    time.sleep(1)
    print("")
    print("Loading...")
    time.sleep(3)
    print("")
    print("Country - " + defenderCountry[defenderNum])
    time.sleep(1)
    print("Position - " + defenderPosition[defenderNum])
    time.sleep(1)
    print(defenderRating[defenderNum] + " OVR")
    time.sleep(1)
    print("Name - " + defenderName[defenderNum])
    print("")
    time.sleep(2)
    print("Saving player...")
    time.sleep(3)
    f = open("defendername.txt", "a")
    f.write(defenderName[defenderNum] + '\n')
    f.close()
    f = open("defenderrating.txt", "a")
    f.write(defenderRating[defenderNum] + '\n')
    f.close()
    f = open("defenderposition.txt", "a")
    f.write(defenderPosition[defenderNum] + '\n')
    f.close()
    f = open("defendercountry.txt", "a")
    f.write(defenderCountry[defenderNum] + '\n')
    f.close()
    print("")
    print("Player saved to my squad")
    coins = coins - 300
    coinString = str(coins)
    f = open("coins.txt", "w")
    f.write(coinString)
    f.close()
    time.sleep(1)
    print("Current coin balance: " + str(coins))
    time.sleep(1)
    decision2 = input("Do you want to open another defender pack or return to homepage? (p/h) ")
    while decision2 != "p" and decision2 != "h":
        print("Please enter a valid option!")
        print("")
        decision2 = input("Do you want to open another defender pack or return to homepage? (p/h) ")
    if decision2 == "p":
      defenderPack(coins)
    elif decision2 == "h":
      homePage(coins)
  elif decision == "n":
    print(storePage(coins))

def midfielderPack(coins):
  decision = input("Are you sure you would like to purchase this midfielder pack? (y/n) ")
  while decision != "y" and decision != "n":
    print("")
    print("Please enter a valid option!")
    print("")
    decision = input("Are you sure you would like to purchase this midfielder pack? (y/n) ")
  import time
  if coins < 300:
    time.sleep(1)
    print("")
    print("Loading...")
    time.sleep(1)
    print("")
    print("ERROR: You do not have enough coins to purchase this item!")
    print("")
    time.sleep(3)
    decision = "n"
  if decision == "y":
    midfielderNum = midfielderChance()
    time.sleep(1)
    print("")
    print("Loading...")
    time.sleep(3)
    print("")
    print("Country - " + midfielderCountry[midfielderNum])
    time.sleep(1)
    print("Position - " + midfielderPosition[midfielderNum])
    time.sleep(1)
    print(midfielderRating[midfielderNum] + " OVR")
    time.sleep(1)
    print("Name - " + midfielderName[midfielderNum])
    print("")
    time.sleep(2)
    print("Saving player...")
    time.sleep(3)
    f = open("midfieldername.txt", "a")
    f.write(midfielderName[midfielderNum] + '\n')
    f.close()
    f = open("midfielderrating.txt", "a")
    f.write(midfielderRating[midfielderNum] + '\n')
    f.close()
    f = open("midfielderposition.txt", "a")
    f.write(midfielderPosition[midfielderNum] + '\n')
    f.close()
    f = open("midfieldercountry.txt", "a")
    f.write(midfielderCountry[midfielderNum] + '\n')
    f.close()
    print("")
    print("Player saved to My Squad")
    coins = coins - 300
    coinString = str(coins)
    f = open("coins.txt", "w")
    f.write(coinString)
    f.close()
    time.sleep(1)
    print("Current coin balance: " + str(coins))
    time.sleep(1)
    decision2 = input("Do you want to open another midfielder pack or return to homepage? (p/h) ")
    while decision2 != "p" and decision2 != "h":
        print("")
        print("Please enter a valid option!")
        print("")
        decision2 = input("Do you want to open another midfielder pack or return to homepage? (p/h) ")
        print("")
    if decision2 == "p":
      print(midfielderPack(coins))
    elif decision2 == "h":
      print(homePage(coins))
  else:
    print(storePage(coins))

def attackerPack(coins):
  decision = input("Are you sure you would like to purchase this attacker pack? (y/n) ")
  while decision != "y" and decision != "n":
    print("")
    print("Please enter a valid option!")
    print("")
    decision = input("Are you sure you would like to purchase this attacker pack? (y/n) ")
  import time
  if coins < 300:
    time.sleep(1)
    print("")
    print("Loading...")
    time.sleep(1)
    print("")
    print("ERROR: You do not have enough coins to purchase this item!")
    print("")
    time.sleep(3)
    decision = "n"
  if decision == "y":
    attackerNum = attackerChance()
    time.sleep(1)
    print("")
    print("Loading...")
    time.sleep(3)
    print("")
    print("")
    print("Country - " + attackerCountry[attackerNum])
    time.sleep(1)
    print("Position - " + attackerPosition[attackerNum])
    time.sleep(1)
    print(attackerRating[attackerNum] + " OVR")
    time.sleep(1)
    print("Name - " + attackerName[attackerNum])
    print("")
    time.sleep(2)
    print("Saving player...")
    time.sleep(3)
    f = open("attackername.txt", "a")
    f.write(attackerName[attackerNum] + '\n')
    f.close()
    f = open("attackerrating.txt", "a")
    f.write(attackerRating[attackerNum] + '\n')
    f.close()
    f = open("attackerposition.txt", "a")
    f.write(attackerPosition[attackerNum] + '\n')
    f.close()
    f = open("attackercountry.txt", "a")
    f.write(attackerCountry[attackerNum] + '\n')
    f.close()
    print("")
    print("Player saved to My Squad")
    coins = coins - 300
    coinString = str(coins)
    f = open("coins.txt", "w")
    f.write(coinString)
    f.close()
    time.sleep(1)
    print("Current coin balance: " + str(coins))
    time.sleep(1)
    print("")
    decision2 = input("Do you want to open another attacker pack or return to homepage? (p/h) ")
    while decision2 != "p" and decision2 != "h":
        print("")
        print("Please enter a valid option!")
        print("")
        decision2 = input("Do you want to open another attacker pack or return to homepage? (p/h) ")
        print("")
    if decision2 == "p":
      print(attackerPack(coins))
    elif decision2 == "h":
      print(homePage(coins))
  else:
    print(storePage(coins))

# play page function
def playPage(coins):
  clear()
  print("")
  print("PLAY")
  print("")
  print("Randomly generating an opponent...")
  time.sleep(5)
  teamNum = random.randint(0,12)
  opponent = teamName[teamNum]
  print("")
  print("You are playing against the " + opponent + "!")
  time.sleep(1)
  print("Opposition Team Rating: " + str(teamRating[teamNum]))
  time.sleep(2)
  print("")
  userInput = input("Do you want to start the game or return to homepage? (s/h)? ")
  while userInput != "s" and userInput != "h":
    print("")
    print("Please enter a valid option!")
    print("")
    userInput = input("Do you want to start the game or return to homepage? (s/h)? ")
  if userInput == "s":
    yourGoal = 0
    oppGoal = 0
    print("")
    print("The match is beginning in a few seconds...")
    time.sleep(3)
    print("")
    matchstart = input("Press enter to start the game")
    print("")
    print("The match has started!")
    time.sleep(2)
    for x  in range(91):
      randomNum1 = random.randint(1,30)
      if teamRating[teamNum] > 94:
        randomNum2 = random.randint(1,10)
      elif teamRating[teamNum] > 89 and teamRating[teamNum] < 95:
        randomNum2 = random.randint(1,15)
      elif teamRating[teamNum] > 84 and teamRating[teamNum] < 90:
        randomNum2 = random.randint(1,20)
      elif teamRating[teamNum] > 79 and teamRating[teamNum] < 85:
        randomNum2 = random.randint(1,25)
      elif teamRating[teamNum] > 74 and teamRating[teamNum] < 80:
        randomNum2 = random.randint(1,30)
      elif teamRating[teamNum] > 69 and teamRating[teamNum] < 75:
        randomNum2 = random.randint(1,35)
      elif teamRating[teamNum] > 64 and teamRating[teamNum] < 70:
        randomNum2 = random.randint(1,40)
      elif teamRating[teamNum] > 59 and teamRating[teamNum] < 65:
        randomNum2 = random.randint(1,45)
      elif teamRating[teamNum] > 54 and teamRating[teamNum] < 60:
        randomNum2 = random.randint(1,50)
      elif teamRating[teamNum] < 55:
        randomNum2 = random.randint(1,55)
      if randomNum1 == 2:
        timeX = str(x)
        yourGoal = yourGoal + 1
        goalString = str(yourGoal)
        oppString = str(oppGoal)
        print(timeX + " - Wow! Your team scored a goal!")
        print("  - Score: " + yourteamname + " " + goalString + " - " + oppString + " " + opponent)
        time.sleep(2)
      elif randomNum2 == 9:
        timeX = str(x)
        oppGoal = oppGoal + 1
        goalString = str(yourGoal)
        oppString = str(oppGoal)
        print(timeX + " - Oh No! " + opponent + " scored a goal!")
        print("  - Score: " + yourteamname + " " + goalString + " - " + oppString + " " +  opponent)
        time.sleep(2)
      else:
        timeX = str(x)
        print(timeX)
        time.sleep(0.3)
    print("Full time!")
    time.sleep(2)
    print("")
    print("The match has ended! The final score:")
    time.sleep(1)
    print(yourteamname + " " + goalString + " - " + oppString + " " +  opponent)
    if goalString > oppString:
      if yourteamrating < teamRating[teamNum]:
        coins = coins + 200
        coinString = str(coins)
        f = open("coins.txt", "w")
        f.write(coinString)
        f.close()
        time.sleep(0.5)
        print("Coins gained: +200")
      elif yourteamrating == teamRating[teamNum]:
        coins = coins + 150
        coinString = str(coins)
        f = open("coins.txt", "w")
        f.write(coinString)
        f.close()
        time.sleep(0.5)
        print("Coins gained: +150")
      elif yourteamrating > teamRating[teamNum]:
        coins = coins + 100
        coinString = str(coins)
        f = open("coins.txt", "w")
        f.write(coinString)
        f.close()
        time.sleep(0.5)
        print("Coins gained: +100")
    elif goalString == oppString:
      coins = coins + 50
      coinString = str(coins)
      f = open("coins.txt", "w")
      f.write(coinString)
      f.close()
      time.sleep(0.5)
      print("Coins gained: +50")
    else:
      time.sleep(0.5)
      print("Coins gained: +0")
    print("Current coin balnce: " + str(coins))
    print("")
    decision3 = input("Do you want to play again or return to homepage? (p/h) ")
    while decision3 != "p" and decision3 != "h":
      print("")
      print("Please enter a valid option!")
      print("")
      decision3 = input("Do you want to play again or return to homepage? (p/h) ")
      print("")
    if decision3 == "p":
      print(playPage(coins))
    elif decision3 == "h":
      print(homePage(coins))
  elif userInput == "h":
    print(homePage(coins))

# start the program
print("FOOTBALL MANAGER")
print("")
print("Welcome to Football Manager!")
print("")
yourteamname = input("Please enter your team name! ")
print("")
print("Welcome to Football Manager, " + yourteamname + "!")
time.sleep(2.5)
print(homePage(coins))


