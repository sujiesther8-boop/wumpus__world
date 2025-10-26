<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>Name: SUJITHA ESTHER S                     </h3>
<h3>Register Number/Staff Id:212224060266                </h3>
<H3>Aim:</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h1>Problem Description</h1>
<hr>
<h2>Wumpus World</h2>
<hr>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)

<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe. 

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
</p>

<hr>
<h1>PROGRAM</h1>
python
wumpus=[["Save","Breeze","PIT","Breeze"],
        ["Smell","Save","Breeze","Save"],
        ["WUMPUS","GOLD","PIT","Breeze"],
        ["Smell","Save","Breeze","PIT"]]

Initial Variables
row, column = 0, 0  # Starting position
arrow = True  # Player has an arrow
player = True  # Game loop control
score = 0  # Initial score

while player:
    choice = input("press u to move up\npress d to move down\npress l to move left\npress r to move right\n")
    
    if choice == "u":
        if row != 0:
            row -= 1
        else:
            print("move denied")
        print("current location: ", wumpus[row][column], "\n")

    elif choice == "d":
        if row != 3:
            row += 1
        else:
            print("move denied")
        print("current location: ", wumpus[row][column], "\n")

    elif choice == "l":
        if column != 0:
            column -= 1
        else:
            print("move denied")
        print("current location: ", wumpus[row][column], "\n")

    elif choice == "r":
        if column != 3:
            column += 1
        else:
            print("move denied")
        print("current location: ", wumpus[row][column], "\n")

    else:
        print("move denied")

    if wumpus[row][column] == "Smell" and arrow:
        arrow_choice = input("do you want to throw an arrow-->\npress y to throw\npress n to save your arrow\n")
        
        if arrow_choice == "y":
            arrow_throw = input("press u to throw up\npress d to throw down\npress l to throw left\npress r to throw right\n")
            
            if arrow_throw == "u" and row > 0:
                if wumpus[row-1][column] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row-1][column] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)

            elif arrow_throw == "d" and row < 3:
                if wumpus[row+1][column] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row+1][column] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)

            elif arrow_throw == "l" and column > 0:
                if wumpus[row][column-1] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row][column-1] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)

            elif arrow_throw == "r" and column < 3:
                if wumpus[row][column+1] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row][column+1] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)

            arrow = False

    if wumpus[row][column] == "WUMPUS":
        score -= 1000
        print("\nWumpus here!!\nYou Die\nAnd your score is: ", score, "\n")
        break

    if wumpus[row][column] == 'GOLD':
        score += 1000
        print("Congratulations! You found the GOLD!\nYour score is: ", score)
        break

    if wumpus[row][column] == 'PIT':
        score -= 1000
        print("Ahhhhh!!!!\nYou fell in a pit.\nYour score is: ", score, "\n")
        break
        
<hr>
<h1>OUTPUT</h1>

![WhatsApp Image 2025-10-23 at 19 37 08_0c52e648](https://github.com/user-attachments/assets/8a5d0191-e1eb-4eb2-be4b-c8e22d7debab)
<h1>Sample Input and Output:</h1>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8696111a-a4a7-47cb-ba4b-43a4ef88573f)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/4be5bf06-79fa-4fa0-9334-38a33f06060b)

