import pygame
import sys

pygame.init()

width, height = 1000, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Slants Grand Prix")

white = (255, 255, 255)
red = (255, 0, 0)

player_size = 25
player_x = 180
player_y = 300
player_speed = 4
player_brake = 0.1
track_color = (50, 50, 50)
grass_color = (0, 225, 100)
RED = (200, 0, 0)
WHITE = (255, 255, 255)
YELLOW = (255, 255, 0)
LIGHT_BLUE = (0, 200, 255)
OFFWHITE = (254, 255, 255)
BLACK = (0, 0, 0)
LIGHT_GRAY = (200, 200, 200)
DARK_GRAY = (100, 100, 100)
INVISIBLE = (0, 0, 0, 0)

slants_track = [
    "                                                  ",
    "        &@&@&@&@&@&@&@              &@&@&@&@&@&@  ",
    "       @##############&            @############& ",
    "     @&################@          &#############@ ",
    "    *###################&        @##############& ",
    "  *$$########@&@&@&@#####@      &#####@&@&@#####@ ",
    "  *$$#######&      &#####&    &@#####@    &#####& ",
    " *$$*######@      @#####@    @#####@&     @#####@ ",
    "*$$* &!^!^!&    @&####@&    &#####&       &#####& ",
    "*$$* !^!^!^!  &@####@&     @#####@        @#####@ ",
    "*$$* @#####& @#####&      &#####&         &#####& ",
    "*$$* &#####@ &#####@     @#####@          @#####@ ",
    "*$$* @#####& @#####&    &#####&           &#####& ",
    "*$$* &#####@ &#####@   @#####@            @#####@ ",
    "*$$* @#####& @#####&  &#####&             &#####& ",
    "*$$* &#####@ &#####@  @#####@             @#####@ ",
    "*$$* @#####& @######@&######&   &@&@&@&@&@&#####& ",
    "*$$* &#####@  &############@   @################@ ",
    "*$$* @#####&   @##########&    &################& ",
    "*$$*&######@    &########@     @################@ ",
    "*$$$@#####&      @&@&@&@&      &#####@&@&@&@&@&@  ",
    "@#########@                     @####&            ",
    " &########&@&@&@&@&@&@&@&@&@&@&@&####@&@          ",
    " @#####################################&          ",
    " &#####################################@          ",
    "  @####################################&          ",
    "  &####################################@          ",
    "  @##################################@&           ",
    "   &@&@&@&@&@&@&@&@&@&@&@&@&@&@&@&@&@             ",
    "                                                  ",
]

track_y = 0
rectangle_width = 100
rectangle_height = 20
srectangle_width = 20
srectangle_height = 60

rectangle_x = 120
rectangle_y = 200


sec1rectangle_x = 400
sec1rectangle_y = 340

sec2rectangle_x = 860
sec2rectangle_y = 260

sec3rectangle_x = 120
sec3rectangle_y = 220

rectangle = pygame.Rect(rectangle_x, rectangle_y, rectangle_width, rectangle_height)
sec1 = pygame.Rect(sec1rectangle_x, sec1rectangle_y, srectangle_width, srectangle_height)
sec2 = pygame.Rect(sec2rectangle_x, sec2rectangle_y, rectangle_width, rectangle_height)
sec3 = pygame.Rect(sec3rectangle_x, sec3rectangle_y, rectangle_width, rectangle_height)


clock = pygame.time.Clock()

# Stopwatch variables
stopwatch_running = False
lap_running = False
stopwatch_time = False
Sector1_time = False
Sector1_total_time = False
Sector2_time = False
Sector2_total_time = False
Sector3_time = False
Sector3_total_time = False
start_time = 0

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    keys = pygame.key.get_pressed()

    if keys[pygame.K_LEFT] and player_x > 0:
        player_x -= player_speed
    if keys[pygame.K_RIGHT] and player_x < width - player_size:
        player_x += player_speed
    if keys[pygame.K_UP] and player_y > 0:
        player_y -= player_speed
    if keys[pygame.K_DOWN] and player_y < height - player_size:
        player_y += player_speed

    if keys[pygame.K_SPACE]:
        player_speed -= player_brake
        if player_speed < 0:
            player_speed = 0
    else:
        player_speed += player_brake
        if player_speed > 4:
            player_speed = 4

    # Clear the screen
    screen.fill(white)

    # Draw the track
    for i in range(len(slants_track)):
        for j in range(len(slants_track[i])):
            if slants_track[i][j] == "#":
                pygame.draw.rect(screen, track_color, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == "@":
                pygame.draw.rect(screen, red, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == "~":
                pygame.draw.rect(screen, track_color, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == "&":
                pygame.draw.rect(screen, WHITE, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == " ":
                pygame.draw.rect(screen, grass_color, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == "^":
                pygame.draw.rect(screen, OFFWHITE, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == "!":
                pygame.draw.rect(screen, BLACK, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == "$":
                pygame.draw.rect(screen, LIGHT_GRAY, (j * 20, i * 20, 20, 20))
            elif slants_track[i][j] == "*":
                pygame.draw.rect(screen, DARK_GRAY, (j * 20, i * 20, 20, 20))


    font = pygame.font.SysFont(None, 36)
    text = font.render("Slants GP", True, DARK_GRAY)
    screen.blit(text, (350, 500))
    pygame.draw.rect(screen, (track_color), rectangle)
    pygame.draw.rect(screen, (YELLOW), sec1)
    pygame.draw.rect(screen, (LIGHT_BLUE), sec2)
    pygame.draw.rect(screen, (red), sec3)
    pygame.draw.rect(screen, RED, (player_x, player_y, player_size, player_size))
    player_rect = pygame.Rect(player_x, player_y, player_size, player_size)
    collision = False

    for i in range(len(slants_track)):
        for j in range(len(slants_track[i])):
            if slants_track[i][j] in ["#", "^", "!"]:
                track_rect = pygame.Rect(j * 20, i * 20, 20, 20)
                if player_rect.colliderect(track_rect):
                    collision = True
                    if slants_track[i][j] in ["^", "!"] and not stopwatch_running:
                        stopwatch_running = True
                        start_time = pygame.time.get_ticks()
                        sec1_start = pygame.time.get_ticks()
                        if lap_running == True:
                            stopwatch_running = False
                    break

    if not collision:
        player_x = 180
        player_y = 300

        if stopwatch_running:
            start_time = pygame.time.get_ticks()
            elapsed_time = (pygame.time.get_ticks() - start_time) / 1000
            stopwatch_running = False
            Sector1_time = False
            Sector1_total_time = False
            Sector2_time = False
            Sector2_total_time = False
            Sector3_time = False
            Sector3_total_time = False

    elapsed_time = (pygame.time.get_ticks() - start_time) / 1000

    if player_rect.colliderect(sec1):
        if player_rect.colliderect(sec1):
            sec1_c = True
            Sector1_time = False
            Sector1_total_time = True
            Sector2_time = True
            sec2_start = pygame.time.get_ticks()
            elapsed_time1 = (pygame.time.get_ticks() - sec1_start) / 1000  

    if player_rect.colliderect(sec2):
        if player_rect.colliderect(sec2):
            sec2_c = True
            sec2_total_time = elapsed_time2
            Sector2_time = False
            Sector2_total_time = True
            Sector3_time = True
            sec3_start = pygame.time.get_ticks()

    if player_rect.colliderect(sec3) and elapsed_time > 8:
        if player_rect.colliderect(sec3):
            sec3_c = True
            sec3_total_time = elapsed_time3
            Sector3_time = False
            Sector3_total_time = True

    if player_rect.colliderect(rectangle) and elapsed_time > 8 and sec1_c == True and sec2_c == True and sec3_c == True:
        stopwatch_running = False
        lap_time = elapsed_time1 + elapsed_time2 + elapsed_time3
        lap_running = True

    if stopwatch_running:
        formatted_time = "{:.3f}".format(elapsed_time)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"Lap: {formatted_time}  ", True, BLACK)
        screen.blit(text, (100, 0))

    if lap_running:
        formatted_time = "{:.3f}".format(lap_time)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"Time: {formatted_time}  ", True, BLACK)
        screen.blit(text, (100, 0))

    if Sector1_time:
        elapsed_time1 = (pygame.time.get_ticks() - sec1_start) / 1000
        formatted_time = "{:.3f}".format(elapsed_time1)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"S1: {formatted_time}  ", True, BLACK)
        screen.blit(text, (300, 0))

    if Sector1_total_time:
        formatted_time = "{:.3f}".format(elapsed_time1)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"S1: {formatted_time}  ", True, BLACK)
        screen.blit(text, (300, 0))

    if Sector2_time:
        elapsed_time2 = (pygame.time.get_ticks() - sec2_start) / 1000
        formatted_time = "{:.3f}".format(elapsed_time2)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"S2: {formatted_time}  ", True, BLACK)
        screen.blit(text, (500, 0))

    if Sector2_total_time:
        formatted_time = "{:.3f}".format(elapsed_time2)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"S2: {formatted_time}  ", True, BLACK)
        screen.blit(text, (500, 0))

    if Sector3_time:
        elapsed_time3 = (pygame.time.get_ticks() - sec3_start) / 1000
        formatted_time = "{:.3f}".format(elapsed_time3)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"S3: {formatted_time}  ", True, BLACK)
        screen.blit(text, (700, 0))

    if Sector3_total_time:
        formatted_time = "{:.3f}".format(elapsed_time3)
        font = pygame.font.SysFont(None, 36)
        text = font.render(f"S3: {formatted_time}  ", True, BLACK)
        screen.blit(text, (700, 0))

    if elapsed_time > 15:
        start_time = pygame.time.get_ticks()
        elapsed_time = (pygame.time.get_ticks() - start_time) / 1000

    pygame.display.flip()

    # Cap the frame rate
    clock.tick(60)
