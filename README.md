# tic-tac-toe
board = [' ' for _ in range(9)]

def print_board():
    print()
    print(f'{board[0]} | {board[1]} | {board[2]}')
    print('--+---+--')
    print(f'{board[3]} | {board[4]} | {board[5]}')
    print('--+---+--')
    print(f'{board[6]} | {board[7]} | {board[8]}')
    print()

def check_winner(player):
    win_conditions = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8],
        [0, 3, 6], [1, 4, 7], [2, 5, 8],
        [0, 4, 8], [2, 4, 6]
    ]
    for condition in win_conditions:
        if all(board[i] == player for i in condition):
            return True
    return False

def check_draw():
    return ' ' not in board

def play_game():
    current_player = 'X'
    print_board()

    while True:
        try:
            move = int(input(f"Player {current_player}, choose a position (1-9): ")) - 1
            if move < 0 or move >= 9 or board[move] != ' ':
                print("Invalid move. Try again.")
                continue
        except ValueError:
            print("Please enter a number from 1 to 9.")
            continue

        board[move] = current_player
        print_board()

        if check_winner(current_player):
            print(f"Player {current_player} wins!")
            break
        elif check_draw():
            print("It's a draw!")
            break

        current_player = 'O' if current_player == 'X' else 'X'

play_game()
