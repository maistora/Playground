#!/usr/bin/python3.3
import os
import time
from time import sleep
from random import Random

BOARD_SIZE = 40

def print_board(board, wait = False, sleep = False):
    os.system(['clear', 'cls'][os.name == 'nt'])
    print('=' * (BOARD_SIZE + 2), end = '|\n')
    for row in board:
        print(*['o' if x else ' ' for x in row], end = ' |\n', sep = '')
    # input("Press enter to continue.")


def create_board(fill_rate = 0.3):
    rand = Random()
    return [[int(x and x != BOARD_SIZE + 1 and y and y != BOARD_SIZE + 1
             and rand.normalvariate(0.5, 0.2) < fill_rate) for x in range(0, BOARD_SIZE + 2)] for y in range(0, BOARD_SIZE + 2)]


def step_board(board):
    direct = [
        [-1, 0],    # up
        [0, 1],     # right
        [1, 0],     # down
        [0, -1],    # left
        [-1, -1],   # up left
        [-1, 1],    # up right
        [1, 1],     # down right
        [1, -1]     # down left
        ]
    live_counter = 0
    new_board = empty_board_creator(BOARD_SIZE)
    for i in range(1, len(board) - 1):
        for j in range(1, len(board[i]) - 1):
            for k in range(0, 8):
                if board[i + direct[k][0]][j + direct[k][1]] % 2 != 0:
                    live_counter = live_counter + 1
            if board[i][j] % 2 == 0 and live_counter == 3:
                new_board[i][j] = 1
            elif board[i][j] % 2 == 1:
                if live_counter < 2 or live_counter > 3:
                    new_board[i][j] = 0
                else:
                    new_board[i][j] = board[i][j]
            live_counter = 0
    for i in range(1, len(board) - 1):
        for j in range(1, len(board[i]) - 1):
            board[i][j] = new_board[i][j]


def empty_board_creator(n):
    return [[0 for x in range(0, n + 2)] for y in range(0, n + 2)]


if __name__ == '__main__':
    board = create_board()
    while True:
        step_board(board)
        sleep(0.3)
        print_board(board)
