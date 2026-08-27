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
| Left stick ← → | Drive the crane along the rail; pick the number on the answer strip |
| Left stick ↑ ↓ | Raise and lower the hoist — this is how you dodge |
| **A** | Pick up a car · drop it · confirm |
| **B** | Back to the cars from the answer strip |
| **Y** | Tip every car back into the pile |
| **−** (select) | Change how many problems each student gets — any time |

Watch out on the way across: **gulls** fly through the yard, each at its own
height, and clipping one drops the car — it falls to the floor and rolls back to
the pile. Fly over them, or under them. The claw's grip also slips after about
six seconds; the meter on the trolley shows how long you have. Only the car can
be clipped, never the cable, and the pile itself is always safe.

Each student gets a set number of problems, then the reel spins again. A setup
screen picks that number at the start (1–10, default 3), and **−** changes it
mid-lesson — useful when time is short and half the class hasn't had a go.

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
