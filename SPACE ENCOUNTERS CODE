#initial setup code
import pygame
import random
import math
from pygame import mixer
#init commands
pygame.init()
mixer.init()
win = pygame.display.set_mode((500,500))
pygame.display.set_caption("first Game")



#some initail varibles
i=0
x=0
x2=x
y=425
y3=[]
score=0
score_x=5
score_y=5
y2=425
width=40
height=60
vel=2.5
vel_enemy=[]
min_win=20
max_win=420
x3=[]
bullet_status='not fire'
vel_bullet=4
number_enemies=3
enemy_image=[]
hero_ship=pygame.image.load('hero.png')
background=pygame.image.load('space.jpg')
caption=pygame.font.SysFont('Arial',20)
lives_screen=pygame.font.SysFont('Arial',20)
game_status=pygame.font.SysFont('Arial',60)
lives=3
lives_x=5
lives_y=29
game_levelx=5
game_levely=53
game_level='easy'
game_level_display=pygame.font.SysFont('Arial',20)
screenwidth=500
#background score courtesy:(evanking YT)
mixer.music.load('back_sound.mp3')
mixer.music.play(-1)


def redrawgamewindow():#refreshes game window after every iteration
    win.fill((0,0,0))
    win.blit(background,(0,0))
    if bullet_status=='fire':
        pygame.draw.circle(win,(255,0,0),(int(x2),int(y2)),6)
     
    win.blit(hero_ship,(x,y))
    score_display=caption.render('score :'+ str(score),True,(255,255,255))
    win.blit(score_display,(score_x,score_y))
    lives_display=lives_screen.render('lives:'+str(lives),True,(255,255,255))
    win.blit(lives_display,(lives_x,lives_y))
    game_level_display_show=game_level_display.render('level:'+ game_level,True,(255,255,255))
    win.blit(game_level_display_show,(game_levelx,game_levely))
    pygame.display.flip()
def game_over():#this runs when you lose all your lives
    game_status_display=game_status.render('GAME OVER',True,(255,255,255))
    win.blit(game_status_display,(75,250))
    pygame.display.flip()

    



for i in range(number_enemies):#this is part of the enemy respawn mechanism
    x3.append(random.randint(20,440))
    y3.append(0)
    vel_enemy.append(0.8)
    enemy_image.append(pygame.image.load('alien.png'))


            








        

    
        

    


#game loop
run=True
while run:
    
    pygame.time.delay(1)
    
    for event in pygame.event.get():
        if event.type==pygame.QUIT:
            run=False
    #checks which keyboard key is pressed
    if pygame.key.get_pressed():
        keys=pygame.key.get_pressed()
        if keys[pygame.K_LEFT] and x>vel:
            x=x-vel
        if keys[pygame.K_RIGHT] and x<screenwidth-width-vel:
            x=x+vel
        if keys[pygame.K_SPACE]:
            if bullet_status=='not fire':
                x2=x+32
                bullet_status='fire'
       
                
    #bullet mechanism
    if y2>0: 
       if bullet_status=='fire':
           y2=y2-vel_bullet
    elif y2<=0:
        
        bullet_status='not fire'
        y2=425
        x2=x+32
    for i in range(number_enemies):#enemy mechanism and hit detection
        
        if y3[i]<=420:
            if score>25 and score<100:
                vel_enemy[i]=1.3
                vel=3.5
                vel_bullet=8
                game_level='hard'
            if score==26:
               lives=3
            elif score==101:
                lives=4
            elif score==201:
                lives=6
                
            
            elif score>100 and score<200:
                vel_enemy[i]=1.5
                vel=5
                vel_bullet=11
                game_level='ultra hard'
                
                
            elif score>200:
                vel_enemy[i]=2
                vel=7
                vel_bullet=15
                gane_level='God speed'
                
                
            else:
                vel_enemy[i]=0.8
        elif y3[i]>420:
            lives=lives-1
            y3[i]=0

           
            
        
        
        y3[i]=y3[i]+vel_enemy[i]
        
        #hit box detection
        distance=math.sqrt(((x2-(int(x3[i])+32))**2)+((y2-(int(y3[i])+32))**2))
        if distance<50:
            y2=425
            bullet_status='not fire'
            x3[i]=random.randint(20,440)
            y3[i]=0
            score=score+1

    
        
            
        
        
        
        win.blit(enemy_image[i],(x3[i],y3[i]))
        pygame.display.flip()
    if lives<=0:# when you die
         game_over()
         pygame.time.delay(1000)
         run=False
    redrawgamewindow()    
    
    
      
pygame.quit()


