import time
from random import random
from random import seed
from tkinter import StringVar,Entry
import tkinter as tk
import math
import pandas as pd
import matplotlib.pyplot as plt
import os
import winsound
import pygame

class GUI:
    
    #------------------INITIAL---------------------------------------------------------------------------------------------------------
    
    
    def __init__(self, parent):
        
        self.window=parent
        self.started = 0
        self.V0=0
        self.acc=6
        self.defAlt=100
        self.t=0
        self.ind=0
        self.labelBackground = tk.Label(parent, text="",bg="black",width=1080,height=1080)
        self.labelBackground.place(x=0,y=0)
        
        #self.frames = [tk.PhotoImage(file='C:/Users/koray/Desktop/2ba695fd5ecada4d9b337b35e3b7ffbe.gif',format = 'gif -index %i' %(i)) for i in range(25)]
        #self.label2 = tk.Label(image=self.frames[0])
        #self.label2.place(x=0,y=0)
        
#         self.rocket = tk.PhotoImage(file='C:/Users/koray/Desktop/Roket Logo/edit.png')
#         self.labelRocket = tk.Label(image=self.rocket,borderwidth=0, highlightthickness=0)
#         self.labelRocket.place(x=500,y=500)

        self.hurot = tk.PhotoImage(file='C:/Users/koray/Desktop/DataS/hurot2.png')        
        self.labelHurot = tk.Label(image=self.hurot,borderwidth=0,highlightthickness=0)
        self.labelHurot.place(x=510,y=120)
    
    
        self.buttonQuit = tk.Button(parent, text="Quit", bg="white",font="Arial 15",width=9,command=lambda : [self.window.destroy(),pygame.mixer.music.stop()])
        self.buttonQuit.grid(row=0,column=0)
        
        self.music = tk.Button(parent, text="Play Music", bg="white",font="Arial 15",width=9,command=lambda : self.play_sound())
        self.music.grid(row=1,column=0)
        
        self.musicPause = tk.Button(parent, text="Pause Music", bg="white",font="Arial 15",width=9,command=lambda : pygame.mixer.music.pause())
        self.musicPause.grid(row=2,column=0)

        self.labelDateTime = tk.Label(parent, text="Date/Time:",bg="white", font="Arial 20",width=26,borderwidth=2)
        self.labelDateTime.grid(row=0,column=1)

        self.labelAltGps = tk.Label(parent, text="Altitude/GPS:",bg="white", font="Arial 20",width=26,borderwidth=2)
        self.labelAltGps.grid(row=1,column=1)
        
        self.labelDynamics = tk.Label(parent, text="Dynamics:",bg="white", font="Arial 20",width=26,borderwidth=2)
        self.labelDynamics.grid(row=2,column=1)
        
        self.labelDate = tk.Label(parent, text="Date",bg="white", font="Arial 20",width=26,borderwidth=2)
        self.labelDate.grid(row=0,column=2)
        
        self.labelLaunch = tk.Label(parent, text="Launch",bg="white", font="Arial 20",width=26)
        self.labelLaunch.grid(row=0,column=3)
        
        self.labelAlt = tk.Label(parent, text="Alt",bg="orange", font="Arial 20",width=26,borderwidth=2)
        self.labelAlt.grid(row=1,column=2)
        
        self.labelGps = tk.Label(parent, text="GPS:50°46 35.3 N 6°04 42.2",bg="orange", font="Arial 20",width=26,borderwidth=2)
        self.labelGps.grid(row=1,column=3)
        
        self.labelAcc = tk.Label(parent, text="Acc",bg="white", font="Arial 20",width=26,borderwidth=2)
        self.labelAcc.grid(row=2,column=2)
        
        self.labelVelocity = tk.Label(parent, text="Velocity",bg="white", font="Arial 20",width=26,borderwidth=2)
        self.labelVelocity.grid(row=2,column=3)
        
        self.labelDate.after(1000, self.refresh_label)
        
        
#-----------------------------------------------------------------FUNCTIONS START-----------------------------------------------------------
        
    def flight_sim(self):
        self.t=self.t+0.01
        self.defAlt = self.defAlt + self.V0*0.01 + (self.acc*0.0001)/2
        self.V0=self.V0+self.acc*0.01
        if self.acc >= 0:
            self.acc = self.acc -0.005
        else:
            self.acc = self.acc -0.001/self.t
    def play_sound(self):
        pygame.mixer.music.load('Naruto Theme - The Raising Fighting Spirit.mp3') #Loading File Into Mixer
        pygame.mixer.music.play(0)
        
    def dateData(self):
        year,mon,day,hour,min,sec,a,b,c = time.localtime()
        infoDate = f"Date/Time: {year} {mon} {day} sa:{hour} dk:{min} s:{sec} "
        return f"System Clock: {hour}:{min}:{sec} "
    def readGps():
        return 0
    def readAcc(self):
        if  self.acc<=0:
            self.labelAcc.configure(text="Acceleration: %f (m/s^2)" % self.acc,bg="red")
        else:
            self.labelAcc.configure(text="Acceleration: %f (m/s^2)" % self.acc,bg="green")
    def readVelocity(self):
        if  self.V0<=0:
            self.labelVelocity.configure(text="Velocity: %f (m/s^2)" % self.V0,bg="red")
        else:
            self.labelVelocity.configure(text="Velocity: %f (m/s^2)" % self.V0,bg="green")
            
#     def refresh_frames(self):
#         self.frame = self.frames[self.ind]
#         self.ind += 1
#         self.ind = self.ind%25
#         self.label2.configure(image=self.frame)

    def configurations(self):
        
        self.labelDate.configure(text=self.seconds)
        
        self.labelLaunch.configure(text="Launched Since: %i s" % self.started)
        
        self.labelAlt.configure(text="Altitude: %f (m)" % self.defAlt)
        

            
#-------------------------------------------------------------FUNCTION END--------------------------------------------------------------------            
            
            
    def refresh_label(self):
        self.seconds = self.dateData()
                
        self.flight_sim()
                
        self.started = self.started +1/50
        
        self.configurations()
        self.readAcc()
        self.readVelocity()
        
        self.labelDate.after(20, self.refresh_label)
        
if __name__ == "__main__":
    root = tk.Tk()
    root.geometry("1366x768")
    root.title("Hacettepe Rocket Science Telemetry")
    pygame.init()
    timer = GUI(root)
    root.mainloop()
