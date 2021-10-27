import pygame
import time
alarmDurn=10   # holds the duration for which alarm need to sound
alarmsPrcsd =0 # holds the number of times alarms has matured and sounded

def sound_alarm():    #This is the alarm sounding function using pygame package
	global alarmDurn
	print("Alarm sounding")
	pygame.init()
	pygame.mixer.music.load('alarm.wav')
	pygame.mixer.music.play(-1)
	time.sleep(alarmDurn)
	pygame.mixer.music.stop()

def alarm_process():  #Main function that processes alarms & keeps looping  till all alarms are processed 
	global alarmsPrcsd 
	while alarmsPrcsd < nrOfAlarms:
		actual_time=time.strftime("%H:%M")
		for i in range(0,nrOfAlarms):
				
			if actual_time==c[i]:
							
				print("Alarm no.",i+1," activated.The Current time is",actual_time)	
				sound_alarm()					
				alarmsPrcsd = alarmsPrcsd +1
				if alarmsPrcsd != nrOfAlarms:
					time.sleep(60)
					

	time.sleep(10)

nrOfAlarms=int(input("number of alarms to be set:"))
with open("alarms.txt","w") as alarms:
	for i in range(nrOfAlarms):
		
		inps=input("Set alarm in 24hr format of H:M")
		alarms.write(inps)
		alarms.write("\n")
		
with open("alarms.txt","r") as alarms:
	x=alarms.read()
	c=x.split("\n")

print("Set alarm times are:")
for i in range(len(c)):
	print(c[i])

alarm_process()


	


