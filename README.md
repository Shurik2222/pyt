print("Добро пожаловать в игру крестики-нолики!")
print("Игрок 1 - X, Игрок 2 - O")
print("Игровое поле пронумеровано следующим образом:")
print(" 1 | 2 | 3 ")
print("-----------")
print(" 4 | 5 | 6 ")
print("-----------")
print(" 7 | 8 | 9 ")

board = [[" " for _ in range(3)] for _ in range(3)]
current_player = "X"

def print_board():
    """Печатаем текущее состояние игрового поля."""
    for row in board:
        print(" | ".join(row))
        print("-" * 9)

def check_winner():
    """Проверяем, есть ли победитель."""
    # Проверка строк
    for row in board:
        if row[0] == row[1] == row[2] != " ":
            return row[0]
    
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] != " ":
            return board[0][col]
    
    if board[0][0] == board[1][1] == board[2][2] != " ":
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] != " ":
        return board[0][2]
  
    if all(cell != " " for row in board for cell in row):
        return "ничья"
    return None

while True:
    print_board()
    position = input(f"Игрок {current_player}, введите номер клетки (1-9): ")

    
    if position.isdigit() and 1 <= int(position) <= 9:
        pos = int(position) - 1
        row = pos // 3
        col = pos % 3
        if board[row][col] == " ":
            board[row][col] = current_player
        else:
            print("Эта клетка уже занята. Попробуйте ещё раз!")
            continue
    else:
        print("Некорректный ввод. Попробуйте ещё раз!")
        continue

    winner = check_winner()
    if winner:
        print_board()
        if winner == "ничья":
            print("Ничья!")
        else:
            print(f"Игра завершилась! Победил игрок {winner}!")
        break

    
    current_player = "O" if current_player == "X" else "X"


start = input("Начать игру? (да/нет): ")
if start.lower() == "да":
    
    pass
else:
    print("До свидания!")


# Спрашиваем, хотим ли мы начать игру
start = input("Начать игру? (да/нет): ")
if start.lower() == "да":
    # Перезапуск игры здесь, если нужно
    pass
else:
    print("До свидания!")
