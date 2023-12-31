[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=9905812&assignment_repo_type=AssignmentRepo)
 > As you complete each section you **must** remove the prompt text. Every *turnin* of this project includes points for formatting of this README so keep it clean and keep it up to date. 
# Average Life of a UCR student
 
Authors:
Alexander Dobmeier, https://github.com/zanderdo
Stefan Vo, https://github.com/Stefan-Vo
Jared Banzuela: https://github.com/JaredBanzuela 
Matusala Kahsay: https://github.com/matu-kahsay

## Project Description
RPG that simulates the average day in the life of a UCR student. We will be implementing a GUI in which the user can interact with. It consists of various buttons and a text input section. The game allows you to choose your gender, school year, major and other characteristics in order to add variability in the game. This game also has a skill point system, where the major you choose impacts the amount of skill in a certain area ie..(intelligence, charisma, strength).This project will include pictures, scenarios, and many other aspects of life at UCR. Throughout the game the player will face various challenges that may hinder or deter you from accomplishing several key tasks. By completing these tasks it brings you closer to the goal of the game, which is to graduate successfully. 

Why is it interesting to us?
This project is important to us as it depicts the issue we face as UCR students. On the technical side, this project interests us as game development is a field that we naturally gravitated towards when deciding on a project idea and what better way to step our foot in the door of game development with a text based RPG game that will use a UI software. It is important that we learn the skills of creating a text based RPG game because we understand that the best way to get a sense of the environment of the computer science industry is to develop a complex software with multiple individuals in order to gauge the difficulty and necessary skills to be successful as a team.
languages/tools/technologies we plan to use
C++
Git
Github
VSCode
CMake
Google test Framework
Photoshop
Unreal Engine

input/output of our project:
The input will primarily be in the form of the user pressing buttons on the GUI to indicate what choices they would like to pick.  The output will be in the form of text and pictures of the UCR campus that give the player new options that will progress them through the game.
Features:
Stats (determined by the major the player chooses at the beginning of the game):
Strength
Charisma
Intelligence
Stamina
Health (starts at 100)

Options:
Talk
Run
Fight
Think

Talk:
When talk is chosen, a skill check on charisma is performed.  If the player passes they get by the obstacle, if not something negative happens (Lose health, go into fight or run, lose inventory item, etc.).  If your charisma is high enough, you can even get an item from the enemy,

Run:
When run is chosen, a skill check on stamina is performed.  If the player passes they get by the obstacle, if not something negative happens (Lose health, go into fight or run, lose inventory item, etc.)  Higher chance of going into fight if failed.

Fight:
When fight is selected, the game enters a simulation of the fight.  Computer picks between a few random attacks for both the player and enemy that do varying amounts of damage.  Higher strength means more damage.  Higher stealth means higher chance to dodge an attack.  Intelligence boosts the chance of a critical hit that does more damage than normal.  Computer can decide to “insult” the enemy.  Insult decreases the damage the enemy does and a higher charisma stat means more reduction in damage that the enemy can do.  Your health at the end of the fight becomes your new health.  If you win, the defeated enemy drops an item.

Think:
When think is selected, a skill check on is ran on intelligence.  If it passes, the player gets a boost or the enemy gets a debuff in either of the other options.  If it fails, the player is forced into a fight and the enemy gets a free hit.

After passing an enemy
After passing an enemy, certain stats are increased based on the choices that the player made.


In-Between Story Choices:
Go to the Gym (increases strength)
Go to a party (increase charisma)
Study at the Library (increases intelligence)
Eat food (increase stamina)
Go to the hospital (Restore health 50-60 pts)

Inventory System:
Stores items that the player can use to help them.  If the player has an item they can use when they encounter an enemy, there is an additional button to use that item and a brief description of what it will do.

 > ## Phase II
 ![CS100 UML diagram](https://user-images.githubusercontent.com/122512856/218392411-2e93ab59-b241-44b7-bb74-5139813f1fd5.png)

Game Logic:
Game Logic contains a list of all scenes in the game and navigates through them based on the player input.  Game logic also initializes the game (enemies, scenes, player stats, etc.) when the game is launched.

Scene:
Scene contains all of the information on a specific scene (type, options, pictures, etc).

Action:
Action contains all of the functions for the decisions the player can make by using the buttons.

Inventory:
Inventory contains a vector with all of the items that the player has picked up.  It also can add or remove items from the player’s inventory.

Item:
Item contains the ID of the specific item in the inventory and it’s name and picture.  

Strengther:
A type of item that can be used in combat. It increases the player’s strength.

Healer:
A type of item that restores the player’s Health

Learner:
A type of item that increases the player’s intelligence

Charismer:
A type of item that increases the player’s charisma.

Display:
Displays images and text to the terminal for the player to interact with the game. It can display characters, backgrounds, text, items, difficulty, and options.

Enemy:
A class that contains the health, damage, strength, and difficulty of an enemy the player might face. An enemy can attack, take damage, or drop items. Its difficulty can also be viewed.

Player:
The player class will contain all of the information of the player. That starts with first choosing the type of player based upon their major. This will initialize the attributes of the player from their health score, strength, intelligence, stamina, and charisma. The functions of the class will be getMajor for user input of desired major choice and getStats/setStat in order to initialize and keep track of the player stats. 


 > ## Phase III
 ![CS100 UML diagram](https://github.com/cs100/final-project-f1-d1-rank-1-team/blob/svo025/workspace1/cs100UMLproject.png)

### Classes and Changes to UML Diagram using Solid Principles ###
 **1.** Character class has been implemented in order to improve and simplify the code. We implemented it using the Liskov’s Substitution Principle, where both the base class and the derived classes behave in the same way. To implement this principle, we made sure that both Character and Enemy class had all the functions of Character so that the base class behaves in the same way as the derived classes. This also satisfies the Interface Segregation Principle because we made sure that both classes don't have functions that are ineffective for that specific class. 
 
 **2.** Action class implemented so classes are more focused on maintaing and executing one task. Classes are now more specific and responsible for more individual tasks. This was implemented using the Single Responsibility Principle, we saw that the original Action/Character class had too many repsonsbilities so we made new classes and split the responbilities up for the classes. We now have classes responsible for maintaing data and classes to output data. 
 
**3** Stats class was implemented with the Single Responsbility Principle so that classes are less cluttered and each class are implemented with the idea of having one responsbility. This change of creating a Stats Class provides less confusion in what each Class is responsbile for.  

**4** Updated the Scene and Display classes to be more representative of the actual ImGui implementation and obey the single responsibility principle of the SOLID principles.  Scene will store all text, pictures, and button text that Display will have to display for a specific scene.  Display now has an Init(), Render(), and Shutdown() function which all use ImGui to display the scenes.  The UpdateXXX() functions will tell ImGui exactly what it needs to display 
 
 
 
 > ## Final deliverable
### Updated UML Diagram
<img width="579" alt="Screenshot 2023-03-17 at 16 43 58" src="https://user-images.githubusercontent.com/108632333/226070368-0f537995-093b-4d40-842c-f9344a92f178.png">

 
 
 ## Screenshots
<img width="650" alt="IntroScene" src="https://user-images.githubusercontent.com/122512856/226069928-5dd7db40-b656-4444-aa0b-b3cfcc52a105.PNG">
<img width="654" alt="SelectMajor" src="https://user-images.githubusercontent.com/122512856/226069949-c9429008-7bd9-4f60-93b6-1cebc313d90f.PNG">
<img width="649" alt="CheckStats" src="https://user-images.githubusercontent.com/122512856/226069968-eb408288-4ead-4b3e-8191-0a423cec2b22.PNG">
<img width="652" alt="HUB" src="https://user-images.githubusercontent.com/122512856/226070059-3b7fc9fe-3e52-4734-b576-5962611ecab2.PNG">
<img width="653" alt="Party" src="https://user-images.githubusercontent.com/122512856/226070091-86cb79fe-9024-490d-a074-f51ad814c073.PNG">
<img width="653" alt="Fight" src="https://user-images.githubusercontent.com/122512856/226070176-ea29759b-3b1e-48db-aa0b-50932035e162.PNG">
<img width="652" alt="Victory" src="https://user-images.githubusercontent.com/122512856/226070219-73d5dada-56da-4976-bf0d-8b33d82a9ac1.PNG">
<img width="656" alt="Reward" src="https://user-images.githubusercontent.com/122512856/226070234-0e36f8bb-0541-46a9-9569-88abe2b12cf2.PNG">

 ## Installation/Usage
After downloading the repository, navigate to the path below and open the .exe file highlighted in the picture.  Follow on screen prompts to play the game.


<img width="845" alt="Filepath" src="https://user-images.githubusercontent.com/122512856/226070525-e447768f-fea9-45d0-b415-d097d0f9e3c8.PNG">

 ## Testing
We have taken a thorough approach to ensure the validity and functionaility of this project by designing unit tests for the classes involved. The majority of functions within each class have undergone testing using the googletest submodule.
