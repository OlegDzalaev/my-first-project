# крестики-нолики
def greet():
    print("------------------")
    print("Приветсвуем вас")
    print("в игре")
    print("крестики-нолики")
    print("------------------")
    print("формат ввода: x y")
    print("x - ноемр строки")
    print("y - номер столбца")

def show_pole():
    print("  0  1  2")
    for i in range(3):
        print(f"{i} {pole[i][0]}, {pole[i][1]}, {pole[i][2]}")


def ask():
    while True:
        x, y = map(int, input("           Ваш ход: ").split())
        if 0 <= x <= 2 and 0 <= y <= 2:
            if pole[x][y] == " ":
                return x, y
            else:
                print("Клетка занята")
        else:
            print("Выход за диапазон")

def check_win():
    win_cord = [((0, 0), (0, 1), (0, 2)), ((1, 0), (1, 1), (1, 2)), ((2, 0), (2, 1), (2, 2)),((0, 2), (1, 1), (2, 0)), ((0, 0), (1, 1), (2, 2)),((0, 0), (1, 0), (2, 0)),
    ((0, 1), (1, 1), (2, 1)), ((0, 2), (1, 2), (2, 2))]
    for cord in win_cord:
        symbols = []
    for c in cord:
        symbols.append(pole[c[0]][c[1]])
        if symbols == ["X", "X", "X"]:
            print("Выиграл X")
            return True
        if symbols == ["0", "0", "0"]:
            print("Выиграл 0")
            return True
    return False

greet()
pole = [[" ", " ", " "],
        [" ", " ", " "],
        [" ", " ", " "]]
count = 0
while True:
    count += 1
    show_pole()
    if count % 2 == 1:
        print(" Ходит крестик! ")
    else:
        print(" Ходит нолик! ")

    x, y = ask()

    if count % 2 == 1:
        pole[x][y] = "X"
    else:
        pole[x][y] = "0"

    if check_win():
        break

    if count == 9:
        print("Ничья")
        break
