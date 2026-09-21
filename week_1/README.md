QUESTION1
The code moves the ball in instant jumps each frame rather than along a smooth path:
Δx=v⋅Δt
If the ball moves too fast, its next position jumps completely outside the bowl in a single frame. Because the code only checks where the ball ends up,not the path it took,it misses the wall boundary entirely, causing the ball to clip or pass straight through (tunneling).
•  Δt (Time Step): A larger time step means bigger position jumps per frame, making it easier to skip past the wall.
•  |v| (Velocity): Faster speeds mean the ball travels further in one frame (Δx=|v|Δt), increasing the chance of overshooting.
•  ρ (Ball Radius) & R (Bowl Radius): The gap R-ρ gives the collision margin. A smaller ball radius (ρ) leaves a thinner boundary, making tunneling easier.
•  g (Gravity): Gravity speeds up the ball as it falls, which increases |v| and causes larger jumps into the wall.

QUESTION2
Peak Height Behavior
Instead of holding steady, the peak height actually decays and stops over time.
Where the Energy Goes
Even though e_w=1 keeps ideal physics energy constant, energy is lost due to numerical errors and boundary snapping:
	Discrete Time-Stepping: When the ball hits the curved wall, it overshoots the boundary before the code detects it. Snapping the ball back onto the bowl wall and reflecting its velocity angle strips away small amounts of speed on every bounce.
	Micro-Bounces at the Bottom: Near the bottom of the bowl, gravity repeatedly pulls the ball slightly into the floor, and the wall code immediately pushes it back up. These rapid, frame-by-frame position corrections act like artificial friction, quickly draining the remaining speed until the ball settles.


MAX NO OF BALLS
The max number I cud reach while the simulation still ran smoothly was around 250. The code checks every ball against every other ball to detect collisions. As i add more balls, the required checks grow exponentially, Processing hundreds of thousands of checks 60 times every second overwhelms the CPU, causing the frame rate to drop and the simulation to freeze.


ASSIGMENT BRIEF
Overall, the simulation works nicely as a simple demo, but it clearly shows the limits of basic physics coding. The visuals are cool when running a small number of balls, but things break down quickly once you try pushing it. The CPU gets overloaded when there are too many objects on screen, and the simple bounce logic creates weird quirks where fast balls clip through walls or lose energy when they shouldn't. It was a good project for learning how real-time physics loops work, but it definitely needs more advanced math and performance tweaks to be truly accurate or smooth.
