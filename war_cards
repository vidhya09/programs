from random import shuffle
suite='H D S C'.split()
ranks='2 3 4 5 6 7 8 9 10 J Q K A'.split()

class Deck:
    def __init__(self):
        print("Creating new deck!!")
        self.allcards=[(s,r) for s in suite for r in ranks]

    def shuffle(self):
        print("Shuffling deck!")
        shuffle(self.allcards)

    def split_half(self):
        return (self.allcards[:26],self.allcards[26:])

class Hand:
    def __init__(self,cards):
        self.cards=cards

    def __str__(self):
        return "Contains {} cards".format(len(self.cards))

    def add(self, added_cards):
        self.cards.extend(added_cards)

    def remove_card(self):
        return self.cards.pop()

class Player:
    def __init__(self,name,hand):
        self.name=name
        self.hand=hand

    def play_card(self):
        drawn_card=self.hand.remove_card()
        print("{} Has placed {}".format(self.name,drawn_card))
        print("\n")
        return drawn_card

    def remove_war_cards(self):
        war_cards=[]
        if len(self.hand.cards)<3:
            return self.hand.cards
        else:
            for x in range(3):
                war_cards.append(self.hand.remove_card())
            return war_cards

    def still_has_cards(self):
        # print("Returns true if player still has cards")
        return len(self.hand.cards)!=0

print("WELCOME TO WAR!! LET'S BEGIN!!")
d=Deck()
d.shuffle()
half1,half2=d.split_half()


computer=Player("Computer",Hand(half1))
name=input("\nEnter your name:")
human=Player(name,Hand(half2))

total_rounds=0
war_count=0

while human.still_has_cards() and computer.still_has_cards():
    total_rounds+=1
    print("New Round!")
    print("Current Standings..")
    print(human.name+" has "+str(len(human.hand.cards)))
    print(computer.name+" has "+str(len(computer.hand.cards)))
    print("Play a card!")
    print("\n")

    table_cards=[]
    c_card=computer.play_card()
    h_card=human.play_card()

    table_cards.append(c_card)
    table_cards.append(h_card)

    if c_card[1]==h_card[1]:
        war_count+=1
        print("War")

        table_cards.extend(human.remove_war_cards())
        table_cards.extend(computer.remove_war_cards())

        if ranks.index(c_card[1])<ranks.index(h_card[1]):
            human.hand.add(table_cards)
        else:
            computer.hand.add(table_cards)
    else:
        if ranks.index(c_card[1])<ranks.index(h_card[1]):
            human.hand.add(table_cards)
        else:
            computer.hand.add(table_cards)

print("GAME OVER! NO OF ROUNDS "+str(total_rounds))
print("A war happend "+str(war_count)+" times")
