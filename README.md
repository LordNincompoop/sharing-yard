# Sharing Yard

A division game for one classroom screen, one game controller and thirty
students. No reading required, no clock, one HTML file that runs offline on an
old machine.

**Status: concept.** Nothing is built yet. The design is in
[DESIGN.md](DESIGN.md); [concept.html](concept.html) is the same thing as an
illustrated pitch.

## The idea

Division is a picture the child drives. Cars sit in a pile, circles sit beside
it, and each press of **A** moves one car into a circle. When the pile is empty
every circle holds the same number, and the answer is something you can see.

Three things make it more than an animation:

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
