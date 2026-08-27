# Sharing Yard

A division game for one classroom screen, one game controller and thirty
students. No reading required, no clock, one HTML file that runs offline on an
old machine.

**Playable prototype.** Download `index.html` and double-click it — that's the
whole install. The design notes are in [DESIGN.md](DESIGN.md), and
[concept.html](concept.html) is the illustrated pitch.

## The idea

Division is a picture the child drives — and they drive it with a crane. Cars sit
in a pile, circles sit beside it, the left stick runs the crane along a rail, and
**A** picks a car up and drops it in a circle. When the pile is empty every circle
holds the same number, and the answer is something you can see.

Because placement is free, fair sharing is something you *achieve*: a sharing
question won't accept an answer until every circle holds the same number, and an
uneven split turns the odd circles red until the child levels them up. A grouping
question enforces the opposite rule — a circle takes exactly the divisor and the
claw refuses one more.

## Playing it

| Control | Does |
| --- | --- |
| Left stick (or ← →) | Drive the crane; pick the number on the answer strip |
| **A** | Pick up a car · drop it · confirm |
| **B** | Back to the cars from the answer strip |
| **Y** | Tip every car back into the pile |

Watch out on the way across: **barrels** drift through the carry lane, and if one
touches the car or the rope it falls and rolls back to the pile. The claw's grip
also slips after about six seconds — the meter on the trolley shows how long you
have. Dipping the claw ducks under a barrel. The pile itself is always safe.

Each student picked gets **three problems**, then the reel spins again.

On the first run the game asks you to press the button marked **A**, then the one
marked **B**, and remembers. No controller? Arrow keys and Enter work too.

## What makes it more than an animation

- **Both divisions.** Sharing (`12 cars into 3 circles` → 4 each) and grouping
  (`12 cars, 4 to a circle` → 3 circles) are different pictures wearing the same
  symbols. The game teaches both — and between them, the **divisor** and the
  **quotient** swap jobs, which is exactly why the vocabulary is worth teaching
  against both pictures rather than one.
- **The words are painted on.** Dividend, divisor, quotient and remainder each
  have a colour, and that colour marks the word, the number in the equation, and
  the part of the picture it names. Position carries the meaning; colour
  reinforces it.
- **The picture fades.** Watch it, drive it, predict it, then work in symbols
  with the picture available on request at a cost in points. The model exists to
  stop being needed.

A wrong answer is never a red cross — the game moves the child's answer out and
lets the pile run dry.

## Hardware

One Nintendo Switch-layout controller that Windows reports as an Xbox pad, so
the face buttons need remapping by position rather than by index — **A** (the
right-hand button, and the one children reach for to confirm) arrives as
`buttons[1]`, not `buttons[0]`. Details and the calibration screen are in
DESIGN.md.

A random picker draws a student number from 1 to 30 before each question.
