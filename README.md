# myrepo
"""
Tic-Tac-Toc program
By: Fabrizio Cossío
"""
from tkinter.tix import TCL_ALL_EVENTS


def main():
    player = second_player("")
    table = create_table()
    while not (win(table) or is_a_draw(table)):
        show_table(table)
        frist_player(player, table)
        player = second_player(player)
    show_table(table)
    print("You are the Winner!")

def create_table():
    table = []
    for square in range(9):
        table.append(square + 1)
    return table

def show_table(table):
    print()
    print(f"{table[0]}|{table[1]}|{table[2]}")
    print("-+-+-")
    print(f"{table[3]}|{table[4]}|{table[5]}")
    print("-+-+-")
    print(f"{table[6]}|{table[7]}|{table[8]}")

def is_a_draw(table):
    for square in range(9):
        if table[square] != "x" and table[square] != "o":
            return False
    return True

def win(table):
    return (table[0] == table[1] == table[2] or
            table[3] == table[4] == table[5] or 
            table[6] == table[7] == table[8] or
            table[0] == table[3] == table[6] or
            table[1] == table[4] == table[7] or
            table[2] == table[5] == table[8] or
            table[0] == table[4] == table[8] or
            table[2] == table[4] == table[6])

def frist_player(player, table):
    square = int(input(f"{player}'s turn to choose a square (1-9): "))
    table[square - 1] = player

def second_player(current):
    if current == "" or current == "o":
        return "x"
    elif current =="x":
        return "o"


if __name__ == "__main__":
    main()