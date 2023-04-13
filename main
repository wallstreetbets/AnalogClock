import pygame
import math
import datetime
import sys

BLACK = (0, 0, 0)
YELLOW = (255, 255, 155)
WHITE = (255, 255, 255)
RED = (255, 0, 0)

pygame.init()

width = 800
height = 600
size = (width, height)
screen = pygame.display.set_mode(size)
pygame.display.set_caption("Analog Clock")
clock = pygame.time.Clock()

origin = (size[0] // 2, size[1] // 2)
radius = 250


def convert_to_degree(circle_radius, theta):
    x = math.sin(2*math.pi*theta/360) * circle_radius
    y = math.cos(2*math.pi*theta/360) * circle_radius
    return x + origin[0], -(y - origin[1])


def print_text(text, text_size, position, color):
    font = pygame.font.SysFont("constantia", text_size, True, False)
    surface = font.render(text, True, color)
    text_rect = surface.get_rect(center=position)
    screen.blit(surface, text_rect)
    return None


def hour_line_tilting():
    tilting = 0
    time_check = current_time.minute
    if time_check > 11 < 20:
        tilting = 5
    if time_check > 21 < 30:
        tilting = 10
    if time_check > 31 < 40:
        tilting = 15
    if time_check > 41 < 50:
        tilting = 20
    if time_check > 51 < 58:
        tilting = 25
    if time_check == 59:
        tilting = 0
    return tilting


main = True

try:
    while main:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit() and sys.exit()
                main = False

        for number in range(1, 13):
            print_text(str(number), 22, convert_to_degree(radius - 40, number * 30), YELLOW)

        for line in range(0, 360, 6):
            if line % 5:
                # pygame.draw.line(screen, YELLOW, convert_to_degree(radius - 7, line), convert_to_degree(radius - 14, line), 2)
                pass
            else:
                pygame.draw.line(screen, YELLOW, convert_to_degree(radius - 7, line), convert_to_degree(radius - 20, line), 4)

        current_time = datetime.datetime.now()
        minute = current_time.minute * (360/60)
        hour = current_time.hour * (360/12)
        second = current_time.second * (360/60)
        day = current_time.day
        month = datetime.datetime.now().strftime('%b')

        print_text(str(day), 18, (width / 2 - 70, height / 2 - 30), WHITE)
        print_text(str(month), 20, (width / 2 - 115, height / 2 - 30), WHITE)
        print_text("Python Legion Software", 10, (width / 2, height - 130), WHITE)
        print_text("                           ®", 14, (width / 2, height - 140), WHITE)

        date_rectangle = pygame.draw.rect(screen, YELLOW, [width // 2 - 92, height // 2 - 42, 44, 20], 1)
        date_rectangle2 = pygame.draw.rect(screen, YELLOW, [width // 2 - 140, height // 2 - 42, 50, 20], 1)

        main_circle = pygame.draw.circle(screen, YELLOW, origin, radius + 8, 12)
        minute_line = pygame.draw.line(screen, YELLOW, origin, convert_to_degree(radius - 80, minute), 6)
        hourly_tilt = hour_line_tilting()
        hour_line = pygame.draw.line(screen, YELLOW, origin, convert_to_degree(radius - 140, hour + hourly_tilt), 8)
        center_circle = pygame.draw.circle(screen, YELLOW, origin, 12)
        center_red_circle = pygame.draw.circle(screen, RED, origin, 6)
        second_line = pygame.draw.line(screen, RED, origin, convert_to_degree(radius - 60, second))

        second_leg_line = pygame.draw.line(screen, RED, origin, convert_to_degree(radius - 300, second), 4)
        center_black_circle = pygame.draw.circle(screen, BLACK, origin, 2)

        pygame.display.flip()
        screen.fill(BLACK)
        clock.tick(10)


except:
    pass
