# moon
import pygame
import time

# Initialize pygame
pygame.init()

# Screen settings
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("🚀 Rocket to the Moon 🌕")

# Load images
rocket_img = pygame.image.load("rocket.png")  # Add an image of a rocket
rocket_img = pygame.transform.scale(rocket_img, (60, 120))
moon_img = pygame.image.load("moon.png")  # Add an image of the moon
moon_img = pygame.transform.scale(moon_img, (100, 100))

# Rocket settings
rocket_x = WIDTH // 2 - 30
rocket_y = HEIGHT - 130
speed = 2

def draw_scene(y_position):
    screen.fill((0, 0, 20))  # Dark background for space
    screen.blit(moon_img, (WIDTH // 2 - 50, 50))  # Moon position
    screen.blit(rocket_img, (rocket_x, y_position))
    pygame.display.flip()

def launch_rocket():
    global rocket_y
    running = True
    while running:
        screen.fill((0, 0, 20))
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
        
        if rocket_y > 80:
            rocket_y -= speed
        else:
            running = False  # Stop when reaching the moon
        
        draw_scene(rocket_y)
        time.sleep(0.02)  # Adjust speed of animation

    print("🚀 The rocket has reached the moon! 🌕")

# Run the animation
launch_rocket()
pygame.quit()
