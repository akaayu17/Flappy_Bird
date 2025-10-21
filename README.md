Flappy Bird (Java Swing)
A simple, classic clone of the Flappy Bird game built entirely in Java using the Swing library for the GUI.

(It's highly recommended you add a screenshot or GIF of your game here!) ![Flappy Bird Gameplay](gameplay.png)

🎮 Features
Classic Gameplay: Press a key to make the bird "jump" upwards.

Physics: Simple gravity implementation pulls the bird down.

Pipe Generation: Pipes are randomly generated at a set interval.

Collision Detection: The game ends if the bird hits a pipe or the ground.

Scoring: The score increases for each set of pipes the bird successfully passes.

Restart: Easily restart the game from the "Game Over" screen.

🕹️ How to Play
Start Game: The game starts automatically.

Jump: Press the Spacebar to make the bird flap its wings and gain upward velocity.

Goal: Navigate the bird through the gaps between the top and bottom pipes.

Game Over: The game ends if you collide with a pipe or fall to the ground.

Restart: When the "Game Over" message appears, press the Spacebar to restart.

🚀 How to Run
Your FlappyBird.java file is a JPanel, which is the content of the game. It needs a JFrame (a window) to be placed into.

1. Required Files
First, ensure you have all the necessary files in the same directory:

FlappyBird.java (Your game code)

flappybirdbg.png (Background image)

flappybird.png (Bird sprite)

toppipe.png (Top pipe image)

bottompipe.png (Bottom pipe image)

2. Create the Main Application File
Create a new file named App.java in the same directory and paste the following code into it. This code creates the main window for your game.

Java

import javax.swing.*;

public class App {
    public static void main(String[] args) throws Exception {
        int boardWidth = 360;
        int boardHeight = 640;

        JFrame frame = new JFrame("Flappy Bird");
        // frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // Optionally set this
        frame.setSize(boardWidth, boardHeight);
        frame.setLocationRelativeTo(null);
        frame.setResizable(false);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        FlappyBird flappyBird = new FlappyBird();
        frame.add(flappyBird);
        frame.pack(); // Sizes the frame to fit the preferred size of the panel
        flappyBird.requestFocus(); // Makes the panel listen for key presses
        frame.setVisible(true);
    }
}
3. Compile and Run
Open a terminal or command prompt in the directory containing all your files.

Compile all the Java files:

Bash

javac App.java FlappyBird.java
Run the main application:

Bash

java App
The game window should now appear and you can start playing!

🛠️ Code Overview
Your FlappyBird.java file handles all the core game logic.

Main Class (FlappyBird): Extends JPanel to act as the game screen. It also implements ActionListener to respond to the game loop timer and KeyListener to respond to user input.

Inner Classes (Bird, Pipe): Simple classes to store the properties (position, size, image) of the game objects.

Timers:

gameLoop: A Timer that fires approximately 60 times per second (every 1000/60 ms). It calls the actionPerformed method.

placePipeTimer: A Timer that fires every 1.5 seconds (1500 ms) to call the placePipes() method.

Game Loop (actionPerformed): This is the main engine of the game. On each tick, it:

Calls move() to update all game object positions and check for game-over conditions.

Calls repaint() to redraw the screen with the new positions.

Stops the timers if gameOver is true.

Drawing (paintComponent, draw): Uses Graphics g to draw the background, bird, pipes, and score onto the panel.

Game Logic (move):

Applies gravity to the bird's velocityY.

Moves all pipes to the left (velocityX).

Checks for collisions using the collision() method.

Increments the score when a pipe is passed.

Sets gameOver if the bird hits a pipe or the ground.

Input (keyPressed):

Listens for the Spacebar.

If the game is running, it sets the velocityY to -9 to make the bird jump.

If the game is over, it resets all game variables (bird position, score, etc.) and restarts the timers.