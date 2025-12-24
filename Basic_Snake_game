import pygame import time import random

pygame.init()        #Initialize pygame

white = (255, 255, 255) black = (0, 0, 0) red = (213, 50, 80) green = (0, 255, 0) blue = (50, 153, 213)    #Define colors

width, height = 600, 400 screen = pygame.display.set_mode((width, height)) pygame.display.set_caption("Snake Game")    #  Screen dimensions

snake_block = 10 snake_speed = 15 clock = pygame.time.Clock()    #Snake properties

font_style = pygame.font.SysFont("bahnschrift", 25)   #Font styles

def draw_snake(snake_block, snake_list): for block in snake_list: pygame.draw.rect(screen, green, [block[0], block[1], snake_block, snake_block])

def message(msg, color, position): text = font_style.render(msg, True, color) screen.blit(text, position)

def game_loop(): game_over = False game_close = False

x, y = width / 2, height / 2
x_change, y_change = 0, 0
snake_list = []
length_of_snake = 1

food_x = round(random.randrange(0, width - snake_block) / 10.0) * 10.0
food_y = round(random.randrange(0, height - snake_block) / 10.0) * 10.0

while not game_over:
    while game_close:
        screen.fill(black)
        message("Game Over! Press Q-Quit or C-Play Again", red, [width / 6, height / 3])
        pygame.display.update()

        for event in pygame.event.get():
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_q:
                    game_over = True
                    game_close = False
                if event.key == pygame.K_c:
                    game_loop()

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                x_change = -snake_block
                y_change = 0
            elif event.key == pygame.K_RIGHT:
                x_change = snake_block
                y_change = 0
            elif event.key == pygame.K_UP:
                y_change = -snake_block
                x_change = 0
            elif event.key == pygame.K_DOWN:
                y_change = snake_block
                x_change = 0

    # Boundary conditions
    if x >= width or x < 0 or y >= height or y < 0:
        game_close = True

    x += x_change
    y += y_change
    screen.fill(blue)

    pygame.draw.rect(screen, red, [food_x, food_y, snake_block, snake_block])
    snake_list.append([x, y])

    if len(snake_list) > length_of_snake:
        del snake_list[0]

    for block in snake_list[:-1]:
        if block == [x, y]:
            game_close = True

    draw_snake(snake_block, snake_list)
    pygame.display.update()

    if x == food_x and y == food_y:
        food_x = round(random.randrange(0, width - snake_block) / 10.0) * 10.0
        food_y = round(random.randrange(0, height - snake_block) / 10.0) * 10.0
        length_of_snake += 1

    clock.tick(snake_speed)

pygame.quit()
quit()
game_loop()
