# snake
loosley based on chris deleon's 

13/8/19
Joe's changes

it's changing direction twice before moving once

EXAMPLE SITUATION: SNAKE MOVING EAST
tap DOWN & LEFT keys at same time (DOWN a fraction of a second before LEFT)
SNAKE tries to turn SOUTH, THEN  INSTANTLY turn WEST (this works because at the moment of LEFT-tap, snake's direction(i.e. speed) was southward)
BUT SNAKE hasn't yet moved from the position it was in when it was heading EAST
THEREFORE SNAKE has turned from EAST to WEST before moving, tries to move back onto itself, hits its own neck, game over & resets

SOLUTION(S):
- force snake to step one square after every keypress

FIXED:
- changed snake from block var (w/ "let") to global var (w/ "window.") so I could access it within the keypress event handler function
- added call to (now global) snake.move() to force move, one call per switch case block for each direction key
- now when you try to reproduce the bug by tapping two directions together, the snake always steps one step in the first direction before acting on the second direction
	- e.g. snake moving RIGHT, tap DOWN & LEFT together, snake now steps 1 square DOWN then turns LEFT, thus not turning into itself

OTHER STUFF:
- commented out an unnecessary line per each case of the keypress function 
	- still unnecessarily convoluted, could get by with e.g.
		case 37:
			if(!xv === 1){
				xv = -1
				yv = 0
				snake.move()
				break
			}
	although I think this would let you go superspeed by tapping the direction you're already going repeatedly, so you decide if that's a bug or a feature
	
