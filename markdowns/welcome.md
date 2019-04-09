import sys
import time
import random
import pickle

class Instance():
	cycle = 0
	count = None
	level = None

#define how to build the files needed
def build():
	open("Cretamen_questions.py", "w+")
	print("Preparing to run...")
	setup()

#Ask if the user wants to build the file. 
#They might want to do this to customize it and wipe and corrupion.
def init():
	print ("Do you want to build the nessecary files? y/n Use this only for the first time.")
	buildyesno = raw_input()
	if buildyesno == "y":
		build()
	elif buildyesno == "n":
		print ("Preparing to run...")
		setup()
	else:
		print("Try again. Please enter y for yes or n for no.")
		init() 

#makes list that will be asked
def getList(level, count):
	from Cretamen_questions import imported
	organizedInput = []
	returnData = []
	for item in imported:
		if (item[0] == int(level)):
			organizedInput.append(item)
	random.shuffle(organizedInput, random.random)
	for i in range(int(count)):
		a = organizedInput[i]
		returnData.append(a)
	return returnData

def setup():
	Instance.count = int(raw_input("How many questions would you like to ask? "))
	Instance.level = int(raw_input("What level would you like to be quized on? "))

init()
