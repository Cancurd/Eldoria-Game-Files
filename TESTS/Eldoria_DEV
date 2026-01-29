# Eldoria RPG
# Made by Justin Wang ^-^
import random
import time
import sys
import os
import colorama
from colorama import Fore, Back, Style

colorama.init(autoreset=True)

# Phrases
win_phrases = [
    " OBLIBERATED THE ",
    " DEFEATED THE ",
    " SMASHED THE ",
    " TERMINATED THE ",
    " DESTROYED THE ",
    " EXTERMINATED THE "
]

lose_phrases = [
    " DEFEATED "
    " DESTROYED "
    " OBLIBERATED "
]


# Gameloop Variables
run = True
menu = True
play = False

# Player Stat Variables
dragon_key = False
fight = False
standing = False

warrior_menu = False
wizard_menu = False
trickster_menu = False
classChoose = False
select = False
origin_select = False

# Shop Variables
buy = False
Blacksmith = False

# Quest Variables
speak = False
Dragon = False
score = 0
sword_name = "EXCALIBUR"

# Inventory Variables
sellcheck = False
sellin = False
inventory = False


# Special Ability Variables
storm_ability = False
shadow_ability = False
eclip_ability = False
cooldown = False

# Health bars
bars = 20
remaining_health_symbol = "█"
lost_health_symbol = "_"

# hp bar colors
color_green = "\033[92m"
color_yellow = "\33[33m"
color_red = "\033[91m"
color_blue = "\33[34m"
hp_color = color_green
color_default = "\033[0m"

# Player Stats
level = 1
HP = 100
HPMAX = 100
ATK = 10
band = 3
med = 3
gold = 10
x = 2
y = 3
copper = 0
iron = 0
stone = 0
player_class = 0
rage = 15
fireball = 10
bolt = 10
crit_hit = round(ATK*1.5)
a_count = 0
k_count = 0
d_daggers = 15
backstab = ATK * 4

# Map
#  x = 0       x = 1         x = 2       x = 3     x = 4     x = 5     x = 6
map = [["plains", "plains", "plains", "lumberjack", "forest",    "mountain", "mountain", "valley", "cave"],  # y = 0
       ["forest", "farmer", "blacksmith", "forest",   "forest",     "hills",   "mountain", "valley", "mountain"],  # y = 1
       ["forest", "fields", "bridge", "plains",   "hills",    "valley",  "hills", "town", "shop"],  # y = 2
       ["valley", "shop",   "town",   "mayor",   "plains", "blacksmith", "shop", "hills", "mountain"],  # y = 3
       ["valley", "fields", "fields", "plains",   "hills",   "town", "mountain", "mountain", "valley"],  # y = 4
       ["fields", "shop",    "town",   "plains", "hills", "mountain", "mountain", "valley", "hills"],  # y = 5
       ["lake", "bridge",   "bridge", "fields", "fields", "valley",    "valley", "valley", "hills"],    #y = 6
       ["lake",   "fields", "plains", "blacksmith",  "forest", "valley", "hills", "hills", "mountain"],
       ["fields", "plains", "plains", "plains", "forest", "valley", "valley", "hills", "mountain"]]  # y = 7
y_len = len(map) - 1
x_len = len(map[0]) - 1

#Biomes
biom = {
    "plains": {
        "t": "PLAINS",
        "e": True},
    "forest": {
        "t": "FOREST",
        "e": True},
    "fields": {
        "t": "FIELDS",
        "e": False},
    "bridge": {
        "t": "BRIDGE",
        "e": True},
    "town": {
        "t": "TOWN CENTER",
        "e": False},
    "shop": {
        "t": "SHOP",
        "e": False},
    "mayor": {
        "t": "MAYOR",
        "e": False},
    "cave": {
        "t": "CAVE",
        "e": False},
    "mountain": {
        "t": "MOUNTAIN",
        "e": True},
    "hills": {
        "t": "HILLS",
        "e": True},
    "lake": {
        "t": "LAKE",
        "e": False},
    "valley": {
        "t": "VALLEY",
        "e": True},
    "blacksmith": {
        "t": "BLACKSMITH",
        "e": False},
    "farmer": {
        "t": "FARMER",
        "e": False},
    "lumberjack": {
        "t": "LUMBERJACK",
        "e": False
    }
       
}

e_list = ["GOBLIN", "ORC", "GIANT", "TROLL", ]

# Enemies
mobs = {
    "GOBLIN": {
        "hp": random.randint(15, 20),
        "atk": random.randint(5, 10),
        "go": random.randint(5, 10)
    },
    "ORC": {
        "hp": random.randint(25, 35),
        "atk": random.randint(15, 20),
        "go": random.randint(10, 20)
    },
    "GIANT": {
        "hp": random.randint(25, 40),
        "atk": random.randint(15, 25),
        "go": random.randint(18, 21)
    },
    "TROLL": {
        "hp": random.randint(15, 25),
        "atk": random.randint(9, 15),
        "go": random.randint(15, 20)
    },
    "SLIME": {
        "hp": random.randint(19, 24),
        "atk": random.randint(13, 17),
        "go": random.randint(19, 30)
    },
    "DRAGON": {
        "hp": 1500,
        "atk": random.randint(35, 50),
        "go": 650
    }
}


def clear():
    os.system("cls")


def draw():
    print(Fore.CYAN + "Xx-----------------------xX")

# Save file
def save():
    list = [
        name,
        str(level),
        str(HP),
        str(ATK),
        str(x),
        str(y),
        str(dragon_key),
        str(player_class),
        str(origin)      
    ]

    file = open("saves.txt", "w")

    for item in list:
        file.write(item + "\n")
    file.close()

# Saving Inventory
def inv():
    inv_list = [
        str(med),
        str(band),
        str(stone),
        str(copper),
        str(iron),
        str(gold)
    ]

    inv_file = open("inventory.txt", "w")

    for items in inv_list:
        inv_file.write(items + "\n")
    inv_file.close()

# Selling Stuff
def sell():
    global name, med, band, stone, copper, iron, gold, inventory, sellin

    i = open("inventory.txt", "r")
    inv_list = i.readlines()
    if len(inv_list) > 0:
        med = int(inv_list[0][:-1])
        band = int(inv_list[1][:-1])
        stone = int(inv_list[2][:-1])
        copper = int(inv_list[3][:-1])
        iron = int(inv_list[4][:-1])
        gold = int(inv_list[5][:-1])

        while sellin:
            draw()
            clear()
            print(Fore.CYAN + "||SELL ITEMS||")
            draw()
            print("SWORD: " + sword_name)
            print(Fore.RED + "0 - BACK")
            print(Fore.YELLOW + "GOLD: " + str(gold))
            print(Fore.CYAN + "1 - BANDAGES: " + str(band))
            print(Fore.CYAN + "2 - MEDKITS: " + str(med))
            print(Fore.CYAN + "3 - STONE: " + str(stone))
            print(Fore.CYAN + "4 - COPPER: " + str(copper))
            print(Fore.CYAN + "5 - IRON:" + str(iron))
            draw()

            sell_item = input("> ")

            if sell_item == "0":
                sellin = False
            if sell_item == "1":
                if band > 0:
                    clear()
                    b = int(input("HOW MANY BANDAGES WOULD YOU LIKE TO SELL?"))
                    if b <= band:
                        band -= b
                        gold += b*10
                        print("YOU HAVE SOLD", b, "BANDAGE(S)!")
                        input("> ")
                    elif b > band:
                        print("TOO MANY BANDAGES")
                        input("> ")
                    elif b < 0:
                        print("INVALID NUMBER")
                        input("> ")
                else:
                    print("NOT ENOUGH BANDAGES")
                    sellin = False
                    inventory = True

            if sell_item == "2":
                if med > 0:
                    m = int(input("HOW MANY MEDKITS WOULD YOU LIKE TO SELL?"))
                    if m <= med:
                        med -= m
                        gold += m*20
                        print("YOU HAVE SOLD", m, "MEDKIT(S)")
                        input("> ")
                    elif m > med:
                        print("TOO MANY MEDKITS")
                    elif m < 0:
                        print("INVALID NUMBER")
                else:
                    print("NOT ENOUGH MEDKITS")
                sellin = False
                inventory = True


            if sell_item == "3":
                if stone > 0:
                    s = int(input("HOW MUCH STONE WOULD YOU LIKE TO SELL?"))
                    if s <= stone:
                        stone -= s
                        gold += s*15
                        print("YOU HAVE SOLD", s, "PIECE(S) OF STONE")
                        input("> ")
                    elif s > stone:
                        print("TOO MUCH STONE")
                    elif s < 0:
                        print("INVALID NUMBER")
                else:
                    print("NOT ENOUGH STONE")
                sellin = False
                inventory = True

            if sell_item == "4":
                if copper > 0:
                    c = int(input("HOW MUCH COPPER WOULD YOU LIKE TO SELL?"))
                    if c <= copper:
                        copper -= c
                        gold += c*20
                        print("YOU HAVE SOLD", c, "PIECE(S) OF COPPER")
                    elif c > copper:
                        print("TOO MUCH STONE")
                    elif c < 0:
                        print("INVALID NUMBER")
                else:
                    print("NOT ENOUGH COPPER")
            sellin = False
            inventory = True

# Healing
def heal(amount):
    global HP
    if HP + amount < HPMAX:
        HP += amount
    else:
        HP = HPMAX
    print(name + "'s HP REFILLED TO " + str(HP) + "!")



# Fighting
def battle():
    global fight, play, run, HP, med, gold, Dragon, band, hp_color, hp, hpmax, eclip_ability, shadow_ability, storm_ability, rage, fireball, bolt, a_count, k_count, crit_hit_check, crit_hit, backstab, d_daggers, stone, copper, iron
    crit_hit_check = 0

    a_count = 1

    if not Dragon:
        enemy = random.choice(e_list)
    else:
        enemy = "DRAGON"
    hp = mobs[enemy]["hp"]
    hpmax = hp
    atk = mobs[enemy]["atk"]
    g = mobs[enemy]["go"]

    while fight:
        clear()
        draw()
        print(Fore.CYAN + "DEFEAT THE " + enemy + "!")
        draw()
        remaining_hp_bars = round(HP/HPMAX*bars)
        lost_hp_bars = bars - remaining_hp_bars
        print("LEVEL: " + str(level))
        print(enemy + "'S HP: " + str(hp) + "/" + str(hpmax))
        print(f"HEALTH: {HP} / {HPMAX}")
        print(f"|{color_green}{remaining_hp_bars * remaining_health_symbol}" f"{lost_hp_bars * lost_health_symbol}{color_default}|")
        print(Fore.YELLOW + "BANDAGES: " + str(band))
        print(Fore.RED + "MEDKITS: " + str(med))
        draw()
        print(Fore.RED + "1 - ATTACK")
        if band > 0:
            print(Fore.BLUE + "2 - USE BANDAGE (30HP)")
        if med > 0:
            print(Fore.GREEN + "3 - USE MEDKIT (50HP)")
        if player_class == 1:
            print(" ")
            print(Fore.GREEN + "||SKILLS||")
            print(Fore.RED + "4 - RAGE")
        elif player_class == 2:
            print(" ")
            print(Fore.YELLOW + "||SPELLS||")
            print(Fore.GREEN + "4 - LIGHTNING BOLT")
            print(Fore.GREEN + "5 - FIREBALL")
            print(Fore.GREEN + "6 - LIGHT PRISM")
        elif player_class == 3:
            print(" ")
            print(Fore.GREEN + "||SKILLS||")
            print(Fore.BLUE + "4 - BACKSTAB")
            print(Fore.BLUE + "5 - DOUBLE DAGGERS")

        choice = input("> ")

        if choice == "1":
            if origin == 3:
                crit_hit_check = random.randint(0,12)
                if crit_hit_check == 1:
                    hp -= ATK * 2
                    print(Fore.GREEN + name + " DEALT " + str(round(ATK * 1.5)) + " DAMAGE TO THE " + enemy + " WITH A CRITICAL HIT!")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red
                            input("Press Enter - ")
                            
                else:
                    hp -= ATK
                    print(Fore.GREEN + name + " DEALT " + str(ATK) + " DAMAGE TO THE " + enemy + "!")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red
                            input("Press Enter - ") 
                        
            else:
                if HP > 0:
                    hp -= ATK
                    print(Fore.RED + name + " DEALT " + str(ATK) + " DAMAGE TO THE " + enemy + ".")
                    HP -= atk
                    print(Fore.RED + "The " + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                    input("Press Enter -  ")

                    HP = max(HP, 0)
                    hp = max(hp, 0)

                    if HP > 0.66 * HPMAX:
                        hp_color = color_green
                    elif HP > 0.33 * HPMAX:
                        hp_color = color_yellow
                    else:
                        hp_color = color_red
                        
            
        elif choice == "2":
            if band > 0:
                band -= 1
                heal(30)
                HP -= atk
                print(enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
            else:
                print(Fore.CYAN + "NO BANDAGES IN INVENTORY")
            input("Press Enter -  ")

        elif choice == "3":
            if med > 0:
                med -= 1
                heal(50)
                HP -= atk
                print(enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
            else:
                print(Fore.RED + "NO MEDKITS IN INVENTORY")
            input("Press Enter -  ")
        
        elif choice == "4":
            if player_class == 1:
                if a_count > 0:
                    a_count -= 1
                    hp -= rage
                    print(Fore.RED + name + " USED FRENZY AND DEALT " + str(rage) + " DAMAGE TO THE " + enemy + ".")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red
                       
                else:
                    print(Fore.RED + "YOU HAVE USED ALL ABILITIES!")
                    input("Press Enter -  ")
            
            elif player_class == 2:
                if a_count > 0:
                    a_count -= 1
                    hp -= bolt
                    print(Fore.YELLOW + name + "USED LIGHTNING BOLT AND DEALT " + str(bolt) + " DAMAGE TO THE " + enemy + ".")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red
                           
                else:
                    print(Fore.RED + "YOU HAVE USED ALL ABILITIES!")
                    input("Press Enter -  ")
            
            elif player_class == 3:
                if a_count > 0:
                    a_count -= 1
                    hp -= bolt
                    print(Fore.RED + name + " USED BACKSTAB AND DEALT " + str(backstab) + " DAMAGE TO THE " + enemy + "!")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red
                        
                elif a_count <= 0:
                    print(Fore.RED + "YOU HAVE USED ALL ABILITIES!")
                    input("Press Enter - ")
                        
        elif choice == "5":
            if player_class == 2:
                if a_count > 0:
                    a_count -= 1
                    hp -= fireball
                    print(Fore.LIGHTRED_EX + name + " USED FIREBALL AND DEALT " + str(fireball) + " DAMAGE TO THE " + enemy + ".")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red
                elif a_count <= 0:
                    print(Fore.RED + "YOU HAVE USED ALL ABILITIES!")
                    input("Press Enter - ")


            elif player_class == 3:
                if a_count > 0:
                    a_count -= 1
                    hp -= d_daggers
                    print(Fore.LIGHTRED_EX + name + " USED USED DOUBLE DAGGERS AND DEALT " + str(d_daggers) + " DAMAGE TO THE " + enemy + ".")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red

                elif a_count <= 0:
                    print(Fore.RED + "YOU HAVE USED ALL ABILITIES!")
                    input("Press Enter -  ")
        
        elif choice == "6":
            if player_class == 2:
                if a_count > 0:
                    a_count -= 1
                    atk - round(atk/4)
                    print(Fore.LIGHTYELLOW_EX + name + " USED LIGHT PRISM AND REDUCED 25% DAMAGE FROM THE " + enemy + ".")
                    if HP > 0:
                        HP -= atk - round(atk/4)
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red

                elif a_count <= 0:
                    print(Fore.RED + "YOU HAVE USED ALL ABILITIES!")
                    input("Press Enter -  ")
        
        elif choice == "4":
            if player_class == 3:
                if a_count > 0:
                    a_count -= 1
                    hp -= backstab
                    print(Fore.LIGHTYELLOW_EX + name + " USED BACKSTAB AND WRECKED THE " + enemy + ".")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red

                elif a_count <= 0:
                    print(Fore.RED + "YOU HAVE USED ALL ABILITIES!")
                    input("Press Enter -  ")
        
        elif choice == "5":
            if player_class == 3:
                if a_count > 0:
                    a_count -= 1
                    hp -= d_daggers
                    print(Fore.LIGHTYELLOW_EX + name + " THREW TWO DAGGERS AT THE " + enemy + ".")
                    if HP > 0:
                        HP -= atk
                        print(Fore.RED + enemy + " DEALT " + str(atk) + " DAMAGE TO " + name + ".")
                        input("Press Enter -  ")

                        HP = max(HP, 0)
                        hp = max(hp, 0)

                        if HP > 0.66 * HPMAX:
                            hp_color = color_green
                        elif HP > 0.33 * HPMAX:
                            hp_color = color_yellow
                        else:
                            hp_color = color_red
                            
                elif a_count >= 0:
                    print(Fore.RED + "YOU HAVE USED UP ALL OF YOUR ABILITIES!")
                    input("Press Enter -  ")
        

        if HP <= 0:
            print(name + " GOT WRECKED BY " + enemy)
            draw()
            fight = False
            play = False
            run = False
            draw()
            print(Fore.RED + "GAME OVER")
            draw()
            input("Press Enter -  ")
            clear()
            score = 0
            score = int(ATK + gold + copper + iron + stone)
            print("SCORE: ", score)
            

        elif hp <= 0:
            clear()
            draw()
            print(Fore.YELLOW + name + random.choice(win_phrases) + enemy + "!")
            draw()
            a_count = 0
            k_count += 1
            fight = False
            gold += g
            print(Fore.YELLOW + "YOU FOUND " + str(g) + Fore.YELLOW + " GOLD")
            prize = random.randint(1,8)
            if prize == 1:
                if origin == 3:
                    medical_prize = 0
                    medical_prize = random.randint(2,3)
                    band += medical_prize
                    print(Fore.CYAN + "YOU FOUND " + medical_prize + " BANDAGES")
                    input("Press Enter -  ")
                    clear()
                else: 
                    band += 1
                    print(Fore.CYAN + "YOU FOUND A BANDAGE")
                    input("Press Enter -  ")
                    clear() 
            elif prize == 2:
                if origin == 3:
                    medical_prize = 0
                    medical_prize = random.randint(2,3)
                    med += medical_prize
                    print(Fore.CYAN + "YOU HAVE FOUND " + str(medical_prize) + " MEDKIS")
                    input("Press Enter - ")
                    clear()
                else:
                    med += 1
                    print(Fore.CYAN + "YOU HAVE FOUND A MEDKIT")
                    input("Press Enter - ")
                    clear()
            elif prize == 3:
                if player_class == 3:
                    item_prize = 0
                    item_prize = random.randint(3,7)
                    stone += item_prize
                    print(Fore.CYAN + "YOU HAVE FOUND " + str(item_prize) + " PIECES(S) OF STONE")
                    input("Press Enter -  ")
                    clear()
                else:
                    stone_found = random.randint(1,5)
                    stone += stone_found
                    print(Fore.CYAN + "YOU HAVE FOUND " + str(stone_found) + " PIECES(S) OF STONE")
                    input("Press Enter -  ")
                    clear()
            elif prize == 4:
                if player_class == 3:
                    item_prize = 0
                    item_prize = random.randint(3,7)
                    copper += item_prize
                    print(Fore.CYAN + "YOU HAVE FOUND " + str(item_prize) + " PIECES OF COPPER")
                    input("Press Enter -  ")
                    clear()
                else:
                    copper_found = random.randint(1,5)
                    copper += copper_found
                    print(Fore.CYAN + "YOU HAVE FOUND " + str(copper_found) + " PIECE(S) OF COPPER")
                    input("Press Enter -  ")
                    clear()
            elif prize == 5:
                if player_class == 3:
                    item_prize = 0
                    item_prize = random.randint(3,7)
                    iron += item_prize
                    print(Fore.CYAN + "YOU HAVE FOUND " + str(item_prize) + " PIECES OF IRON")
                    input("Press Enter -  ")
                    clear()
                else:
                    iron_found = random.randint(1,5)
                    iron += iron_found
                    print(Fore.CYAN + "YOU HAVE FOUND " + str(iron_found) + " PIECES(S) OF IRON")
                    input("Press Enter -  ")
                    clear()
            elif enemy == "DRAGON":
                draw()
                Dragon = False
                play = False
                run = False
                score = (band + med + ATK + HP + gold)
                print("SCORE: ", score)


# Buying
def shop():
    global buy, gold, band, med, ATK, HPMAX, HP
    
    while buy:
        clear()
        draw()
        print("WELCOME TO THE SHOP")
        draw()
        print(Fore.GREEN + "HP: " + str(HPMAX))
        print(Fore.YELLOW + "GOLD: " + str(gold))
        print(Fore.BLUE + "BANDAGES: " + str(band))
        print(Fore.BLUE + "MEDKITS: " + str(med))
        print(Fore.RED + "ATK: " + str(ATK))
        draw()
        print(Fore.RED + "1 - BUY BANDAGE (30HP) - 10 GOLD")
        print(Fore.BLUE + "2 - BUY MEDKIT (50HP) - 15 GOLD")
        print(Fore.GREEN + "3 - GET MORE HP (+10HP) - 20 GOLD")
        print(Fore.LIGHTRED_EX + "4 - LEAVE")
        draw()

        choice = input("# ")

        if choice == "1":
            if gold >= 10:
                band += 1
                gold -= 10
                print(Fore.GREEN + "YOU HAVE BOUGHT A BANDAGE")
            else:
                print(Fore.RED + "NOT ENOUGH GOLD")
            input("> ")
        elif choice == "2":
            if gold >= 15:
                med += 1
                gold -= 15
                print(Fore.GREEN + "YOU HAVE BOUGHT A MEDKIT")
            else:
                print(Fore.RED + "NOT ENOUGH GOLD")
            input("> ")
        elif choice == "3":
            if gold >= 20:
                HPMAX += 10
                HP = HPMAX
                gold -= 20
                print(Fore.GREEN + "YOU UPGRADED YOUR HEALTH")
            else:
                print(Fore.RED + "NOT ENOUGH GOLD")
            input("> ")
        elif choice == "4":
            buy = False


# Upgrading sword
def blacksmith():
    global gold, ATK, sword_name, Blacksmith, storm_ability, eclip_ability, shadow_ability

    while Blacksmith:
        clear()
        draw()
        print(Fore.MAGENTA + "WELCOME TO THE BLACKSMITH")
        draw()
        print(Fore.YELLOW + "GOLD: " + str(gold))
        print(Fore.RED + "ATK: " + str(ATK))
        draw()
        print(Fore.RED + "1 - UPGRADE SWORD (+5 ATK) - 8 GOLD")
        print(Fore.BLUE + "2 - BUY NEW SWORD (COST VARIES)")
        print(Fore.LIGHTRED_EX + "3 - LEAVE")
        draw()

        choice = input("# ")

        if choice == "1":
            if gold >= 8:
                ATK += 5
                gold -= 8
                print(Fore.GREEN + "YOU HAVE UPGRADED YOUR SWORD!")
            else:
                print(Fore.RED + "NOT ENOUGH GOLD")
            input("> ")
        elif choice == "2":
            clear()
            draw()
            print(Fore.LIGHTGREEN_EX + "PLEASE CHOOSE A SWORD!")
            draw()
            print(Fore.YELLOW + "GOLD: " + str(gold))
            print(Fore.RED + "ATK: " + str(ATK))
            print(Fore.RED + "SWORD: " + sword_name)
            draw()
            print(Fore.RED + "1 - STORMBRINGER (20 ATK) - 20 GOLD")
            print(Fore.RED + "2 - SHADOWFANG (30 ATK) - 25 GOLD")
            print(Fore.RED + "3 - ECLIPSION (45 ATK) - 40 GOLD")
            print(Fore.LIGHTRED_EX + "4 - BACK")
            draw()

            choice_2 = input("# ")

            if choice_2 == "1":
                if gold >= 20:
                    ATK = 20
                    gold -= 20
                    print(Fore.GREEN + "SWORD: STORMBRINGER")
                    sword_name = "STORMBRINGER"
                    shadow_ability = False
                    eclip_ability = False
                    storm_ability = True
                else:
                    print(Fore.RED + "NOT ENOUGH GOLD")
            
            if choice_2 == "2":
                if gold >= 25:
                    ATK = 30
                    gold -= 25
                    print(Fore.GREEN + "SWORD: SHADOWFANG")
                    sword_name = "SHADOWFANG"
                    shadow_ability = True
                    eclip_ability = False
                    storm_ability = False
                else:
                    print(Fore.RED + "NOT ENOUGH GOLD")

            if choice_2 == "3":
                if gold >= 40:
                    ATK = 45
                    gold -= 40
                    print(Fore.GREEN + "SWORD: ECLIPSION")
                    sword_name = "ECLIPSION"
                    shadow_ability = False
                    eclip_ability = True
                    storm_ability = False
                else:
                    print(Fore.RED + "NOT ENOUGH GOLD")
               
        elif choice == "3":
            Blacksmith = False


# Boss Quest
def mayor():
    global speak, dragon_key, Dragon

    while speak:
        clear()
        draw()
        print("HELLO THERE TRAVELER!")
        if ATK < 60 and HPMAX < 150:
            print(Fore.RED + "YOU AREN'T STRONG ENOUGH YET. COME BACK ONCE YOU'VE GROWN STRONGER.")
            print(Fore.YELLOW + "TIP: TRY GETTING OVER 60 ATK, AT LEAST 150 HP, AND GET A SPECIAL ABILITY FROM THE BLACKSMITH!")
            dragon_key = False
            speak = False
        elif ATK >= 60 and HPMAX >= 150:
            print(Fore.CYAN + "YOU ARE READY TO TAKE ON THE DRAGON. GO TO THE VERY TOP RIGHT CORNER OF THE MAP. I BELIEVE IN YOU...")
            Dragon = False
            dragon_key = True
            speak = False

        draw()
        print("1 - LEAVE")
        draw()

        choice = input("# ")

        if choice == "1":
            speak = False


# Boss fight
def cave():
    global Dragon, fight, dragon_key

    while Dragon:
        clear()
        draw()
        print(Fore.LIGHTBLACK_EX + "YOU ARE IN THE CAVE.")
        draw()
        if dragon_key:
            print(Fore.GREEN + "1 - USE DRAGON KEY")
        print(Fore.RED + "2 - TURN BACK")
        draw()

        choice = input("> ")

        if choice == "1":
            if dragon_key:
                Dragon = True
                fight = True
                battle()
        elif choice == "2":
            Dragon = False

# Origin Select

def o_select():
    global player_class, menu, play, HPMAX, ATK, origin_select, ori, orig, origin, attack, hitpointmax, HP, band, med
    origin_select = True

    while origin_select:
        clear()
        draw()
        print("WHERE IS YOUR CHARACTER FROM?")
        draw()
        print(Fore.GREEN + "1 - NOMADSVILLE: THESE AREN'T YOUR REGULAR NOMADS, THEY HAVE TRAINED FOR YEARS AND HAVE A +25% ATTACK")
        print(Fore.LIGHTRED_EX + "2 - HEALHURSTANS: PEOPLE FROM HERE HAVE STRONG MEDICAL ABILITIES AND HAVE +10% HP AND 5 MEDKITS AND BANDAGES")
        print(Fore.CYAN + "3 - BATTLEFORGANS: THESE ARE WEAK WARRIORS BUT HAVE A +30% CHANCE OF A CRITICAL HIT")
        print(Fore.LIGHTRED_EX + "4 - BACK")

        ori = input("> ")

        if ori == "4":
            origin_select = False
            clear()
            c_select()

        if ori == "1":
            clear()
            draw()
            print(" ")
            print(Fore.RED + r""" 
        _    .  ,   .           .
    *  / \_ *  / \_      _  *        *   /\'__        *
      /    \  /    \,   ((        .    _/  /  \  *'.
 .   /\/\  /\/ :' __ \_  `          _^/  ^/    `--.
    /    \/  \  _/  \-'\      *    /.' ^_   \_   .'\  *
  /\  .-   `. \/     \ /==~=-=~=-=-;.  _/ \ -. `_/   \
 /  `-.__ ^   / .-'.--\ =-=~_=-=~=^/  _ `--./ .-'  `-
/        `.  / /       `.~-^=-=~=^=.-'      '-._ `._
""")

            draw()
            print(Fore.RED + "||NOMAD||")
            draw()
            print("||STATS||")
            print(Fore.GREEN + "+25% ATK")
            print(Fore.RED + "-10% HP")
            print(" ")
            draw()

            orig = input("IS THIS YOUR ORIGIN? YES/NO")

            if orig.lower() == "yes":
                origin = 1
                HPMAX = hitpointmax - round(hitpointmax/10)
                ATK = ATK + round(ATK/10)
                origin_select = False
                play = True
                HP = HPMAX
            elif orig.lower() == "no":
                clear()
                o_select()
        
        elif ori == "2":
            clear()
            draw()
            print(" ")
            print(Fore.RED + r"""

      |___________________________________
|-----|- - -|''''|''''|''''|''''|''''|'&&\|__
|- -  |  cc 6    5    4    3    2    1 &&& __]==----------------------
|-----|________________________________&&/|
      |``````````````````````````````````` 

""")  
            draw()
            print(Fore.RED + "||HEALHURSTAN||")
            draw()
            print("||STATS||")
            print(Fore.GREEN + "+25% HP")
            print(Fore.RED + "-10% ATTACK")
            print(Fore.YELLOW + "COMES WITH 5 MEDKITS AND BANDAGES")
            print(" ")
            draw()

            orig = input("IS THIS YOUR ORIGIN? YES/NO")

            if orig.lower() == "yes":
                origin = 2
                HPMAX = hitpointmax + round(hitpointmax/4)
                HP = HPMAX
                ATK = ATK - round(ATK/10)
                band = 5
                med = 5
                origin_select = False
                play = True
            elif orig.lower() == "no":
                clear()
                o_select()
        
        elif ori == "3":
            clear()
            draw()
            print(" ")
            print(Fore.RED + r"""       
       .---.
  ___ /_____\
 /\.-`( '.' )
/ /    \_-_/_
\ `-.-"`'V'//-.
 `.__,   |// , \
     |Ll //Ll|\ \
     |__//   | \_\
    /---|[]==| / /
    \__/ |   \/\/
    /_   | Ll_\|
     |`^~~~^`|
     |   |   |
     |   |   |
     |   |   |
     |   |   |
     L___l___J
       |_ | _|
       ___|___
      ^^^^^^^

""")
            draw()
            print(Fore.RED + "||BATTLEFORGAN||")
            draw()
            print("||STATS||")
            print(Fore.RED + "-25% ATTACK")
            print(Fore.GREEN + "+30% CHANCE CRITICAL HIT")
            print(Fore.CYAN + "LUCKY LOOT - GETS MORE MEDKITS AND BANDAGES")
            print(" ")
            draw()

            orig = input("IS THIS YOUR ORIGIN? YES/NO")

            if orig.lower() == "yes":
                origin = 3
                HPMAX = hitpointmax
                HP = HPMAX 
                ATK = ATK - round(ATK/4)
                origin_select = False
                play = True
            elif orig.lower() == "no":
                clear()
                o_select()

# Class Select
def warrior():
    global player_class, hitpointmax, attack, select, warrior_menu
    select = False
    warrior_menu = True
    while warrior_menu:
            clear()
            draw()
            print(Fore.RED + r"""
         !
        .-.
      __|=|__
     (_/`-`\_)
     //\___/\\
     <>/   \<>
      \|_._|/
       <_I_>
        |||
       /_|_\

    """)
            draw()
            print(Fore.RED + "||WARRIOR||")
            draw()
            print(" ")
            print("||STATS||")
            print(Fore.GREEN + "+25% ATTACK")
            print(Fore.GREEN + "+25% HP")
            print(" ")
            print(Fore.YELLOW + "||SKILLS||")
            print("----------")
            print(Fore.RED + "RAGE: UNLEASH MASSIVE DAMAGE UPON THE ENEMY")

            p_class = input("IS THIS YOUR CLASS? YES/NO: ")

            if p_class.lower() == "yes":
                player_class = 1
                hitpointmax = 125
                attack = 14
                warrior_menu = False
                o_select()
            elif p_class.lower() == "no":
                clear()
                warrior_menu = False
                c_select()

def wizard():
    global player_class, hitpointmax, attack, select, wizard_menu
    select = False
    wizard_menu = True
    while wizard_menu:
            clear()
            draw()
            print(Fore.RED + r"""              
                _,._      
    .||,       /_ _\\     
    \.`',/      |'L'| |    
    = ,. =      | -,| L    
    / || \    ,-'\"/,'`.   
    ||     ,'   `,,. `.  
    ,|____,' , ,;' \| |  
    (3|\    _/|/'   _| |  
    ||/,-''  | >-'' _,\\ 
    ||'      ==\ ,-'  ,' 
    ||       |  V \ ,|   
    ||       |    |` |   
    ||       |    |   \  
    ||       |    \    \ 
    ||       |     |    \
    ||       |      \_,-'
    ||       |___,,--")_\
    ||         |_|   ccc/
    ||        ccc/       
    ||                
    """)
            draw()
            print(Fore.BLUE + "||WIZARD||")
            draw()
            print(" ")
            print("||STATS||")
            print(Fore.GREEN + "-20% DAMAGE FROM ENEMIES")
            print(Fore.GREEN + "+10% ATTACK")
            print(" ")
            print(Fore.MAGENTA + "||SPELLS||")
            print("----------")
            print(Fore.LIGHTCYAN_EX + "LIGHT PRISM: BLIND YOUR ENEMIES AND REDUCE THEIR DAMAGE BY 25%")
            print(Fore.LIGHTCYAN_EX + "FIREBALL: BLAST YOUR ENEMIES WITH A BURNING BALL OF FIRE")
            print(Fore.LIGHTCYAN_EX + "LIGHTNING BOLT: STRIKE YOUR ENEMIES WITH A BLAST OF LIGHTNING")
            draw()

            p_class = input("IS THIS YOUR CLASS? YES/NO: ")

            if p_class.lower() == "yes":
                wizard_menu = False
                player_class = 2
                hitpointmax = 100
                attack = 11
                o_select()
            elif p_class.lower() == "no":
                clear()
                wizard_menu = False
                c_select()

def trickster():
    global hitpointmax, select, attack, player_class, trickster_menu
    select = False
    trickster_menu = True
    while trickster_menu:
        clear()
        draw()
        print(Fore.RED + r"""        
        ____        
    (____)
    /____\
    |___.-~-.-~-.
    |__(  __|__  )_
    |/ \/\_/^\._)/ \
    (  (__{(@)}\_)  )
    |\_/ (/(_)\_))_/
______|_(  (__)_)_/ )
/_________\_/  |  \_/
|/   /' |\  /'-~'~-'\|
|  (| \/ |
|   `\   |
    `\  `\  |    ___
    `\  `\|  /' ..'>
    ___`\  `\: ,' /'
/' _ /''`\  '__'
< .'./'   |  |
`~' |    |  |
    |    |/'
    |    |
    |    |
    |    |
        \  /
        \/
""")
        draw()
        print(Fore.MAGENTA + "||TRICKSTER||")
        draw()
        print(" ")
        print(Fore.GREEN + "+10% CHANCE CRITICAL HIT")
        print(Fore.GREEN + "LUCKY LOOT - GETS MORE ITEMS")
        print(" ")
        print(Fore.MAGENTA + "||ABILITIES||")
        print("----------")
        print(Fore.LIGHTCYAN_EX + "BACKSTAB - x3 ATTACK")
        print(Fore.LIGHTCYAN_EX + "DOUBLE DAGGERS - LAUNCH TWIN DAGGERS AT YOUR OPPONENT")

        p_class = input("IS THIS YOUR CLASS? YES/NO")

        if p_class.lower() == "yes":
            trickster_menu = False
            player_class = 3
            hitpointmax = 90
            o_select()
        elif p_class.lower() == "no":
            clear()
            trickster_menu = False
            c_select()

# Class Select Menu
def c_select():
    global player_class, menu, play, select, HPMAX, ATK, attack, hitpointmax
    select = True

    while select:
        draw()
        print("WHICH CLASS DO YOU SPECIALIZE IN?")
        draw()
        print(Fore.LIGHTRED_EX + "1 - WARRIOR")
        print(Fore.BLUE + "2 - WIZARD")
        print(Fore.GREEN + "3 - TRICKSTER")
        print(Fore.RED + "4 - BACK")

        special = input("> ")

        if special == "1":
            warrior()
            select = False
        elif special == "2":
            wizard()
            select = False
        elif special == "3":
            trickster()
            select = False
        elif special == "4":
            select = False
            menu = True

# Main gameloop
while run:
    while menu:
        clear()
        print("© Copyright 2024 Justin Wang")
        print(Fore.CYAN + r"""
            
    ___________.__       .___           .__         
    \_   _____/|  |    __| _/___________|__|____    
    |    __)_ |  |   / __ |/  _ \_  __ \  \__  \    
    |        \|  |__/ /_/ (  <_> )  | \/  |/ __ \_  
    /_______  /|____/\____ |\____/|__|  |__(____  /  
        \/            \/                    \/  
    """)
        draw()
        print(Fore.CYAN + "1 - NEW GAME")
        print(Fore.YELLOW + "2 - LOAD GAME")
        print(Fore.GREEN + "3 - INSTRUCTIONS (READ ME!)")
        print(Fore.GREEN + "4 - CREDITS")
        print(Fore.RED + "5 - QUIT GAME")
        draw()

        choice = input("> ")
        
        if choice == "1":
            clear()
            draw()
            name = input("WELCOME, START BY STATING YOUR NAME: ")
            menu = False
            clear()
            c_select()
            
        elif choice == "2":
            try:
                f = open("saves.txt", "r")
                load_list = f.readlines()
                if len(load_list) == 11:
                    name = load_list[0][:-1]
                    HP = int(load_list[1][:-1])
                    ATK = int(load_list[2][:-1])
                    band = int(load_list[3][:-1])
                    med = int(load_list[4][:-1])
                    gold = int(load_list[5][:-1])
                    x = int(load_list[6][:-1])
                    y = int(load_list[7][:-1])
                    dragon_key = bool(load_list[8][:-1])
                    player_class = int(load_list[9][:-1])
                    origin = int(load_list[10][:-1])
                    print("WELCOME BACK, " + name + "!")
                    input("> ")
                    menu = False
                    play = True
                else:
                    print("Corrupt save file!")
                    input("> ")
            except OSError:
                print("No loadable save file!")
                input("> ")
        elif choice == "3":
            clear()
            draw()
            print("WELCOME TRAVELER. IN THIS GAME WORLD, YOU\n ARE TASKED TO DEFEAT THE BOSS IN THE CAVE. \n UPGRADING YOUR STATS WILL HELP YOU BE ABLE TO GET QUESTS \n WHICH YOU CAN GET FROM THE MAYOR. THE CONTROLS ARE \n VERY SIMPLE, JUST TYPE IN NUMBERS. HAVE FUN! \n GAME DEVS")
            print("CONTROLS: \n TYPE IN THE NUMBERS NEXT TO THE TEXT TO DO IT. IF YOU SEE A >, \n IT MEANS YOU HAVE TO PRESS ENTER")
            draw()
            choice = ""
            input("> ")
            
        elif choice == "4":
            clear()
            print(Fore.GREEN + "||Credits||")
            print(Fore.GREEN + "-----------")
            print(" ")
            print(Fore.CYAN + "DEVELOPER: JUSTIN WANG")
            print(Fore.GREEN + "DEBUGGERS: SEAN - YASH")
            print(Fore.LIGHTRED_EX + "BETA TESTERS: CASEY, HENRAY")
            print(Fore.BLUE + "ASCII ART: asciiart.eu by jgs")
            print(Fore.YELLOW + "THANK YOU FOR PLAYING ELDORIA RPG")
            input("> ")
        
        elif choice == "5":
            quit()

    while play:
        save()  # autosave
        inv() #inv autosave
        clear()

        if not standing:
            if biom[map[y][x]]["e"]:
                if random.randint(0, 100) < 30:
                    fight = True
                    battle()

        if play:
            draw()
            print("LOCATION: " + biom[map[y][x]]["t"])
            draw()
            print("NAME: " + name)
            print("SWORD: " + sword_name)
            print(Fore.GREEN + "HP: " + str(HP) + "/" + str(HPMAX))
            print(Fore.RED + "ATK: " + str(ATK))
            print(Fore.CYAN + "BANDAGES: " + str(band))
            print(Fore.CYAN + "MEDKITS: " + str(med))
            print(Fore.YELLOW + "GOLD: " + str(gold))
            print("COORD:", x, y)
            draw()
            print(Fore.CYAN + "0 - SAVE AND QUIT")
            if y > 0:
                print(Fore.LIGHTBLUE_EX + "1 - NORTH")
            if x < x_len:
                print(Fore.LIGHTBLUE_EX + "2 - EAST")
            if y < y_len:
                print(Fore.LIGHTBLUE_EX + "3 - SOUTH")
            if x > 0:
                print(Fore.LIGHTBLUE_EX + "4 - WEST")
            if band > 0:
                print(Fore.CYAN + "5 - USE BANDAGE (30HP)")
            if med > 0:
                print(Fore.CYAN + "6 - USE MEDKIT (50HP)")
            print(Fore.LIGHTBLACK_EX + "7 - ACCESS INVENTORY")
            if map[y][x] == "shop" or map[y][x] == "mayor" or map[y][x] == "cave" or map[y][x] == "blacksmith":
                print(Fore.CYAN + "8 - ENTER")
            draw()

            dest = input("# ")

            if dest == "0":
                clear()
                play = False
                menu = True
                save()
            elif dest == "1":
                if y > 0:
                    y -= 1
                    standing = False
            elif dest == "2":
                if x < x_len:
                    x += 1
                    standing = False
            elif dest == "3":
                if y < y_len:
                    y += 1
                    standing = False
            elif dest == "4":
                if x > 0:
                    x -= 1
                    standing = False
            elif dest == "5":
                if band > 0:
                    band -= 1
                    heal(30)
                else:
                    print("NO BANDAGES!")
                input("> ")
                standing = True
            elif dest == "6":
                if med > 0:
                    med -= 1
                    heal(50)
                else:
                    print("NO MEDKITS!")
                input("> ")
                standing = True
            elif dest == "7":
                clear()
                inventory = True
                draw()
                print(Fore.CYAN + "||INVENTORY||")
                print(Fore.GREEN + "1 - VIEW INVENTORY")
                print(Fore.GREEN + "2 - SELL ITEMS")
                print(Fore.RED + "3 - EXIT")
                draw()

                while inventory:                
                    choice = input("> ")

                    if choice == "1":
                        inventory = False
                        view_inv = True
                        while view_inv:
                            try:
                                a = open("inventory.txt", "r")
                                inv_list = a.readlines()
                                if len(inv_list) > 0:
                                    med = int(inv_list[0][:-1])
                                    band = int(inv_list[1][:-1])
                                    stone = int(inv_list[2][:-1])
                                    copper = int(inv_list[3][:-1])
                                    iron = int(inv_list[4][:-1])
                                    gold = int(inv_list[5][:-1])

                                    clear()
                                    draw()
                                    print("||INVENTORY||")
                                    draw()
                                    print(Fore.GREEN + "MEDKITS: " + str(med))
                                    print(Fore.GREEN + "BANDAGES: " + str(band))
                                    print(Fore.LIGHTBLACK_EX + "STONE: " + str(stone))
                                    print(Fore.LIGHTBLACK_EX + "COPPER: " + str(copper))
                                    print(Fore.LIGHTBLACK_EX + "IRON: " + str(iron))
                                    print(Fore.YELLOW + "GOLD: " + str(gold))
                                    draw()

                                    choice = input(Fore.RED + "1 - BACK")
                                    if choice == "1":
                                        view_inv = False

                            except OSError:
                                print(Fore.RED + "INVENTORY NOT LOADABLE")

                    elif choice == "2":
                        sell()

                    elif choice == "3":
                        inventory = False

            elif dest == "8":
                if map[y][x] == "shop":
                    buy = True
                    shop()
                if map[y][x] == "mayor":
                    speak = True
                    mayor()
                if map[y][x] == "cave":
                    Dragon = True
                    cave()
                if map[y][x] == "blacksmith":
                    Blacksmith = True
                    blacksmith()
            else:
                standing = True        
