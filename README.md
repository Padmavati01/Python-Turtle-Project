## Python Clock Code

Here is the Python code for Clock using the Turtle module:

```python
# Import turtle and time modules
import turtle
import time

# Create a turtle object named krishna
krishna = turtle.Turtle()

# Variables to store x and y coordinates
x = 0
y = 0

# Move the turtle to the home position (center)
krishna.home()

# Set turtle drawing speed to the maximum (0 means fastest)
krishna.speed(0)

# Draw the outer circle for the clock (circle with radius 100)
y = -100
krishna.penup()          # Lift the pen to move without drawing
krishna.goto(x, y)       # Move to position where outer circle starts
krishna.pendown()        # Put the pen down to start drawing
krishna.begin_fill()     # Start filling the color
krishna.fillcolor("gold")# Fill the circle with gold color
krishna.circle(100)      # Draw the outer circle
krishna.penup()          # Lift the pen again
krishna.home()           # Return to the center of the clock

# Draw the inner circle for the clock (circle with radius 60)
y = -60
krishna.goto(x, y)       # Move to the position for the inner circle
krishna.pendown()        # Put the pen down to start drawing
krishna.circle(60)       # Draw the inner circle
krishna.end_fill()       # End filling the color
krishna.penup()          # Lift the pen
krishna.home()           # Move back to the center

# Rotate turtle to face upwards (90 degrees left)
krishna.left(90)

# Draw the clock numbers at 12 positions around the circle
for i in range(12):
    krishna.right(360 / 12)  # Rotate by 30 degrees to the next number position
    krishna.forward(85)      # Move forward to the edge where numbers should be placed
    krishna.write((i + 1))   # Write the clock number (1-12)
    krishna.goto(0, 0)       # Return to the center of the clock

# Function to draw the hour hand (short arm)
def draw_hour_arm():
    krishna.penup()          # Lift the pen
    krishna.home()           # Return to the center
    krishna.right(180)       # Rotate to point downward (6 o'clock)
    krishna.pendown()        # Put the pen down to draw
    krishna.pensize(5)       # Set the pen size for hour hand
    krishna.forward(40)      # Draw the hour hand

# Function to draw the minute hand (longer arm)
def draw_minute_arm():
    krishna.penup()          # Lift the pen
    krishna.home()           # Return to the center
    krishna.right(270)       # Rotate to point to the 9 o'clock position
    krishna.pendown()        # Put the pen down to draw
    krishna.pensize(3)       # Set the pen size for minute hand
    krishna.forward(70)      # Draw the minute hand

# Call functions to draw hour and minute hands
draw_hour_arm()
draw_minute_arm()

# Set pen size for second hand
krishna.pensize(2)

# Initialize angle for the second hand
angle = 0

# Infinite loop to move the second hand continuously
while True:
    start = time.time()        # Capture the current time for timing the second-hand movement
    first_start = 1            # A flag variable to track the initial setup for the second hand
    if first_start == 1:       # Check if this is the first time moving the second hand
        krishna.penup()        # Lift the pen
        krishna.home()         # Move to the center of the clock
        krishna.left(90)       # Rotate to face upward
        first_start = 2        # Set flag to prevent resetting the second hand direction

    krishna.right(angle)       # Rotate the second hand by the current angle
    krishna.pendown()          # Put the pen down to draw the second hand
    krishna.forward(60)        # Draw the second hand
    time.sleep(1 - (time.time() - start))  # Sleep for 1 second minus any time taken by the operations
    krishna.undo()             # Undo the last second hand drawing
    krishna.penup()            # Lift the pen to reposition
    krishna.goto(0, 0)         # Return to the center
    angle += 360 / 60          # Increment the angle for the next second (6 degrees)

# Keep the turtle window open
turtle.done()
