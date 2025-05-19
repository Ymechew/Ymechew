- 👋 Hi, I’m @Ymechew
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Ymechew/Ymechew is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import random
def generate_bingo_card():
# የቢንጎ ካርድ (5x5 ሰንጠረዥ) ይፈጥራል
card = {
"B": random.sample(range(1, 16), 5),
"I": random.sample(range(16, 31), 5),
"N": random.sample(range(31, 46), 5),
"G": random.sample(range(46, 61), 5),
"O": random.sample(range(61, 76), 5)
}
return card
def print_bingo_card(card):
# የቢንጎ ካርድን በቅርብ ያትማል
print(" B    I    N    G    O")
print("-----------------------")
for i in range(5):
row = []
for letter in ["B", "I", "N", "G", "O"]:
row.append(str(card[letter][i]).rjust(2))
print(" | ".join(row))
if i < 4:
print("-----------------------")
def play_bingo():
print(" 🎉 ወደ ቢንጎ ጨዋታ በPython እንኳን ደህና መጡ!\n")
player_card = generate_bingo_card()
generate_bingo_card()
    
print("\n**የእርስዎ ቢንጎ ካርድ:**")
print_bingo_card(player_card)
    
input("\nአስፈላጊ ቁጥሮች ለመጥለፍ 'Enter' አድርግ...")
    
called_numbers = set()
while True:
# ቁጥር ይጥለፋል (1-75 መካከል)
number = random.randint(1, 75)
while number in called_numbers:
number = random.randint(1, 75)
called_numbers.add(number)
# የትኛው ፊደል እንደሆነ ይወስናል (BINGO)
letter = ""
if 1 <= number <= 15:
letter = "B"
elif 16 <= number <= 30:
letter = "I"
elif 31 <= number <= 45:
letter = "N"
elif 46 <= number <= 61:
letter = "G"
else:
letter = "O"
print(f"\nተጠርቷል: {letter}-{number}")

# ቁጥሩ በካርድዎ ላይ ካለ ያሻግራል
for key in player_card:
if number in player_card[key]:
player_card[key][player_card[key].index(number)] = "X"

        # ካርድዎን እንደገና ያትማል
print("\n**የእርስዎ ካርድ:**")
print_bingo_card(player_card)
        
# አሸናፊነትን ያረጋግጡ
def check_win(card):
# �ለስያይ ረድፍ/አምድ/ዲያግናል ያረጋግጣል
for i in range(5):
if all(isinstance(card[letter][i], str) for letter in ["B", "I", "N", "G", "O"]):  # ረድፍ
return True
for letter in ["B", "I", "N", "G", "O"]:  # አምድ
if all(isinstance(num, str) for num in card[letter]):
return True
if all(isinstance(card[letter][i], str) for i, letter in enumerate(["B", "I", "N", "G", "O"])):  # ዲያግናል
return True
return False

if check_win(player_card):
print("\n🎊 አሸናፊ! ቢንጎ ጨውተዋል!")
brak
input("\nለቀጣዩ ቁጥር 'Enter' አድርግ...")
# ጨዋታውን ይጀምሩ
