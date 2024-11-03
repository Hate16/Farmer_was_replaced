# Programming the Farming Drone (Report)
## Introduction
In The Farmer Was Replaced game, players will assume the role of robot farmers to replace the traditional farm, and the human farmer. All four players control their unique section of the farm, whether it be planting crops, taking care of animals or repairing tools. This includes planning and scheduling tasks to maximize productivity and profits in a farming operation, improving resource (land, people) usage and sometimes beating competitors (possibly in a trickier/illegal ways). Victory is determined by whoever has the highest yield or profit after a particular number of rounds have occurred, usually while having to deal with weather changes and other surprises throughout the game, as are the elements of farm life.

Objectives:
1.Conquer the Crops: The player then tries to ensure a high yield by harvesting as many crop types as possible.

2.Ensure Proper Resource Management: Resource management of water, energy and materials is crucial for sustaining and expanding the operations of the farm.

3.Selling Crops, Livestock Products or the Processed Goods – To beat the competition and reach the highest profit, players must sell in various rounds.

4.Adapt to Challenges: Players must deal with random occurrences, including changes in weather, equipment malfunctions, or crop diseases that complicate keeping a farm functioning.

5.Epic challenges or first to hit targets such as highest profit, largest crop yield, or most optimally set up farm.

# Table of Contents
- [Code Snippets and Explanation](#code-snippets-and-explanation)
- [Challenges and Learnings](#challenges-and-learnings)
- [References](#references)


# Code-Snippets-and-Explanation
Write and explain your code along with recordings.
## Step 1: Farming on 1 tile
**Code:**
while True:
	if can_harvest():
		harvest()
	else:
		do_a_flip()

**Explanation:**
The code runs an infinite number of times using the while loop where if we can harvest then the drone will harvest, if not then the drone
will just do a flip.
**Demo:**
Video Demo:
![alt text](./1%20x%201.png)

**Notes**
- Using the code above I was able to get enough hay, upgrading the speed and the grass.

## Step 2: Farming on 3x1 tile
**Code:**
while True:
	plant(Entities.Bush)
	move(South)
	harvest()
	move(South)
	harvest()
	move(North)
	harvest()
	move(North)
	harvest()
	do_a_flip()
	do_a_flip()
	if can_harvest():
		harvest()

**Explanation:**
This code makes the drone to plant the bush, then move to south and harvest, doing it twice and then the drone will move to the north
and harvest doing it twice too. Then after that the drone will do a flip twice becuase after two flips the bush we have planted will 
be ready to harvest.

**Demo:**
Video Demo:
![alt text](./3%20x%201.png)
**Notes**
- Using the code above I was able to get enough hay and bush.
- These features were unlocked too: senses and operators.

## Step 3: Farming on 3x3 tile
**Code:**
# all to move south
while True:
	for x in range(get_world_size()):
		move(East)
		trade(Items.Carrot_Seed)
		for y in range(get_world_size()):
			# Condition to exits
			if num_items(Items.Carrot) < 5000:
				if can_harvest():
					harvest()
					till()
					plant(Entities.Carrots)
				move(South)
			else:
				return

**Explanation:**
This code will will run in infinte loop. It will move across the world from west to east and it will go south. To plant the carrot we need
the carrot seed so we trade for it and then only plant the carrot. If the carrot is less than 5000 then it will keep harvesting whereas if
the carrot if more than 5000 then it will stop harvesting. One thing in this code is that it will not harvest it if the carrot is not ready
to be harvested.


**Demo:**
Video Demo:
![alt text](./3%20x%203.png)
**Notes**
- Using the code above I was able to get enough hay, bush and carrot, also upgrading the speed of the drone and expanding the land to 
  4x4
- These features were unlocked too: Debug, carrot and variable.

## Step 3: Farming on 4x4 tile
**Code:**
def move_to_origin():
	pass

def traverse_farm(cell_function):
	move_to_origin()
	for i in range(get_world_size()):
		for j in range(get_world_size()):
			cell_function()
			move(North)
		move(East)	 

def waiting_harvest():
	while not can_harvest():
		do_a_flip()
	harvest()	
	
def create_ground_type_function(target_ground_type):
	def set_ground_type():
		if get_ground_type() != target_ground_type:
			till()
	return set_ground_type

def create_planting_function(entity):
	def planting_function():
		plant(entity)
	return planting_function
	
def purchase_up_to(item, quantity):
	while num_items(item) < quantity:
		sucesful = trade(item)
		if not succesful:
			return False
	return True

**Explanation:**
It contains code that implements some functions related to a farming game in which there is movement to all types of ground, ability to
 plant crops in a ground, wait for crop harvest, and other features.and buy items. The traverse_farm function traverses the farm grid,
moving the character one cell at a time and calling a function on each. The cell method does not check whether we move off the grid. The 
waiting_harvest function has the character wait and perform the days for an action (e.g do a flip) until the crops open This creates an 
helper called create_ground_type_function and also another called create_planting_function functions which setup actions for tilling 
ground or planting a given crop Last but not least, purchase_up_to continues to purchase a givenN item until and the character holds a
limited number, or it was either terminates the trade, What we have here is close, but not quite the correct code; there is also plenty 
that can be done to add some safeguards to prevent infinite loops.

**Demo:**
Video Demo:
![alt text](./4%20x%204.png)
**Notes**
- Using the code above I was able to get enough carrot, upgrading the tree.
- These features were unlocked too: function, and watering.

# Challenges and Learnings
## Challenges
- The challange that i face were getting the code correct to run and loops where it could harvest continuse and some challange are time 
  too as i have to wait until i meet the need to unlock or upgrade.
- some challenge can be also laptop heat up as we have to wait until it fulfull the need it takes more time and laptop batterys consume 
  more and gets more heat up.
- As there is limitd clues it was harder for us to know to code to command correctly and as there is different references with different 
  solutions it was challanging for us to understand it.

## Learnings
- While playing this game i have learn to check errors and it helped me to gain more knowlege on loops, variables, operator and etc...
- And this game also helped in developing our planning stratiges as befor we harvest we need to know should it haevest and when to harvest.
- As the game it self us mainly based on programing it aims to develop more knowledge on programming and helped us to maintain a Adaptability

## References
List any resources, articles, or libraries you used or referenced while working on this project.
1. https://www.youtube.com/watch?v=-hdhyKf2aN8&list=PLateWiNrGEtoIy8aeWse6dQOCToetjXJg
2. https://www.youtube.com/watch?v=3Gk84cwjGzY