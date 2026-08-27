# Sharing Yard — design notes

Working title. A division game for one classroom screen, one game controller,
and thirty students. No reading required, no clock, one HTML file that runs
offline on an old machine.

The whole game is one sentence: **every division question is a picture of
objects being moved into groups, one press at a time, and the child either
watches that picture, drives it, or predicts it.**

Its own thing — it does not need to look or sound like Times Table Dungeon.
Some of the Dungeon's code is worth lifting (question generation, scoring, the
end-of-lesson summary of missed facts), but none of its theme.

---

## 1. The screen

Straight from the sketch, and it does not get more complicated than this:

```
       dividend  divisor          quotient
           3   ÷   3      =           1

    ( o o o )    (     )    (     )    (     )
       pile       group      group      group
```

- The **equation** across the top, big.
- A **row of circles** underneath — the groups.
- The **answer** on the right, blank until it is earned.

Nothing else is on screen during a question. No HUD to read, no menu, nothing
that requires knowing letters.

### One thing to settle from the sketch

The sketch draws three circles for `3 ÷ 3` with all three cars in the first one.
That reads two ways, and they behave differently once numbers grow:

- **The first circle is the pile** — cars start there and move out to the
  others. At `12 ÷ 3` that means twelve cars crammed into one circle at the
  start.
- **The pile is separate** — drawn to the left as a larger dashed circle, with
  the solid group circles beside it.

These notes assume the second, because it looks identical at `3 ÷ 3` and at
`12 ÷ 3`, and because an empty pile is a clear finish line. Say the word and it
flips back.

## 2. The move

One press of **A** moves one car. That is the core verb of the game.

1. The cars sit in the pile. The circles are empty.
2. **A** — a car leaves the pile and drives into the first circle. Clack.
3. **A** — the next goes to the second circle. **A** — the third.
4. Round and round until the pile is empty. Every circle holds the same number.
5. The answer strip lights up. The child picks the number and confirms.

**R** fast-forwards the rest for a child who has already seen enough.

There is no timer anywhere in the game. A child can sit on a question and move
cars back and forth for as long as they want, and nothing on screen hurries
them.

## 3. The fork worth getting right

`3 ÷ 3 = 1` is two different pictures, not one:

| Reading | The picture | What the answer *is* |
| --- | --- | --- |
| **Sharing** (partitive) | 3 cars, **3 circles**, one to each until the pile is empty | 1 = **cars per circle** |
| **Grouping** (quotative) | 3 cars, **3 to a circle**, fill one and open another | 1 = **number of circles** |

"Three cars in one group" is the grouping reading. Both are correct, both are on
the curriculum, and they are different animations wearing the same symbols. Most
apps only ever show sharing, which is why a child stalls on *"eighteen sweets,
three each, how many children?"* — that question hands you the group size and
asks for the count, and the picture in their head answers the other question.

Sharing moves one car to each circle in rotation. Grouping fills one circle
completely, then opens a new one. Same cars, same end state, different order —
and the order is the entire distinction.

## 4. The parts have names

The vocabulary is not a label pinned next to the game — it is painted onto the
game. Every question is colour-coded into its parts, and the word, the number,
and the part of the picture it names all wear the same colour.

| Part | What it is on screen | Sharing | Grouping |
| --- | --- | --- | --- |
| **Dividend** | How many cars are in the pile at the start | the total | the total |
| **Divisor** | The number you divide by | how many **circles** | how many **per circle** |
| **Quotient** | The answer | how many **per circle** | how many **circles** |
| **Remainder** | What is left in the pile | leftovers | leftovers |

Notice that the divisor and the quotient **swap jobs** between the two pictures.
That is exactly why the words are worth teaching against both — a child taught
only sharing has quietly learned "quotient = how many each", which is wrong half
the time. The words are what survive when the circles are gone.

### How it is encoded

- **Position first, colour second.** The dividend is always left of the `÷`, the
  divisor always right of it, the quotient always right of the `=`. Colour
  reinforces; it never carries the meaning alone, so a colour-blind child loses
  nothing.
- The **pile** glows in dividend colour. The **circle outlines** take divisor
  colour when the divisor is the number of circles, and the **counts inside**
  take quotient colour as the answer resolves. Leftovers take remainder colour.
- The same three colours are used nowhere else in the game.

### Where it appears

- **Stage 1** — no words at all. Colours only, quietly establishing which part
  is which before anything is named.
- **Stage 2 onward** — the three words sit under the equation permanently, in
  their colours, in fixed positions. A child learns them by location long before
  reading them.
- **Now and then** — a "which part is this?" check: the game lights one part of
  the picture and offers the three words on a strip. D-pad to choose, **A** to
  confirm. Same input as everything else, and worth points like any question.
- **Teacher menu toggle** — words off entirely for a class that cannot read yet.
  The colour coding stays and does its work regardless.

The payoff comes at the top of the ladder: once the circles are gone and only
`56 ÷ 8` is on screen, "what is the divisor here?" is still a question the child
can answer, because the divisor has been sitting in the same place wearing the
same colour for six stages.

## 5. The controller — Switch pad, Xbox mapping

The pad is a Nintendo Switch layout that Windows reports as an Xbox pad. That
swaps the two pairs of face buttons, and getting it wrong makes the game feel
broken in a way nobody can describe.

**The physical positions do not move. The letters printed on them do.**

| Printed on the pad | Position | Browser reports it as | Bind to |
| --- | --- | --- | --- |
| **A** | right | `buttons[1]` (Xbox B) | **Move a car · confirm** |
| **B** | bottom | `buttons[0]` (Xbox A) | Take a car back · go back |
| **X** | top | `buttons[3]` (Xbox Y) | Peek at the picture |
| **Y** | left | `buttons[2]` (Xbox X) | Replay the move from the start |

The trap: the obvious binding is `buttons[0]` for "confirm", because that is A on
an Xbox pad. On this hardware `buttons[0]` is the button printed **B**, which is
*cancel* on every Nintendo console the class has ever touched. Confirm must be
`buttons[1]`.

Everything else maps by position and only needs relabelling:

| Printed | Index | Does |
| --- | --- | --- |
| **L** / **R** | 4 / 5 | Fast-forward the moving |
| **ZL** / **ZR** | 6 / 7 | unused |
| **−** | 8 | unused |
| **+** | 9 | Teacher menu |
| **D-pad** ← → | 14 / 15 | Choose the number on the answer strip |
| **D-pad** ↑ ↓ | 12 / 13 | unused |
| Left stick | axes 0/1 | Same as d-pad, deadzone 0.5 |

**There is no typing.** Answers come from a horizontal strip of numbers chosen
with the d-pad. Answers are small — 0 to 12 — so a strip beats a keypad, and it
removes the whole class of "pressed 4 then 2, meant 4" errors.

### Calibration, because Bluetooth lies

A Switch Pro pad reports the standard Xbox mapping over USB in Chrome, but over
Bluetooth, or through a third-party adapter, the indices move around. Rather
than guess, the first run shows one screen: **"press the button that says A"**,
then **"press the button that says B"**. Store the result in `localStorage` and
never ask again. Two presses, and the hardware question is closed permanently.

Also needed, because a controller is the only input: a "no pad found — press any
button" screen that polls until one appears, handling for a pad going to sleep
mid-lesson, and a keyboard fallback so the game is still usable when the pad is
flat.

## 6. The random student picker

Before the game, and between questions, a picker chooses who takes the
controller. Thirty students, one pad, so it is a **random draw** — not a queue,
not a rota.

- Numbers **1 to 30** on a reel. Press **A**, the reel spins and slows, and
  lands on a number that fills the screen.
- Big enough to read from the back of the room.
- Press **A** again to start the question.

Optional toggle: **no repeats until all thirty have gone**, so the draw stays
random but nobody gets missed across a lesson. Off by default — the plain random
draw is the simpler thing and it is what the picker is for.

Names are optional; the number is the identity, which is what makes it work with
a class that cannot read yet.

## 7. The ladder — the picture has to fade

The point of the pictures is to stop needing them. Four rungs, per stage:

1. **Watch** — the moving runs on its own; the child reads the finished circles
   and picks the number. Teaches what the picture means.
2. **Move** — the child drives it with **A**, then answers.
3. **Predict** — the answer is picked *first*, then the moving runs and either
   confirms or contradicts it. This rung is where the learning happens.
4. **Know** — symbols only. **X** peeks at the picture and costs points. Fluency,
   with the model still within reach.

A fluent child spends most turns on rung 4, dropping back when a new divisor
appears.

## 8. Wrong answers are shown, not marked

No red cross, no buzzer. If a child picks `12 ÷ 3 = 5`, the game moves *their*
answer: five into the first circle, five into the second, and the pile runs dry
with the third holding two. *Not enough to go round* is something you can watch
happen, and it corrects better than any marking.

Too small fails the other way — cars left in the pile when everyone could have
had one more.

## 9. Remainders

The strongest argument for doing division with objects at all. `13 ÷ 3`: the
circles fill to four each and one car sits in the pile, outlined and blinking,
unable to join a full group.

Answer entry: pick `4`, press **A**, a second strip appears for the remainder,
pick `1`, press **A**.

Remainders are stage 5, but the pile never lies about them — a leftover shows
from the first lesson if the numbers make one.

## 10. Two rules about the pictures themselves

- **Countable at a glance.** Cars inside a circle lay out in rows, never a heap.
  Six is two rows of three. If a child has to count one by one, the picture has
  stopped teaching division and started teaching careful counting.
- **Bundle above twenty.** Twenty loose objects is about the most anyone can
  read across a classroom. `60 ÷ 10` uses crates of ten, not sixty cars — which
  is also the honest on-ramp to place value, so it earns its place rather than
  being a compromise.

## 11. The array

After a correct answer the circles slide together into a rectangle — 3 rows of
4 — and both facts appear across it:

```
3 × 4 = 12        12 ÷ 3 = 4
```

Read across for one, down for the other. Division stops being a fresh set of
facts to memorise and becomes the times tables turned around.

## 12. Stage progression

| Stage | Facts | Why here |
| --- | --- | --- |
| 1 | `÷1` and `n ÷ n`, totals to 6 | The two cases every child mis-states. One enormous circle; or every circle holding exactly one. The `3 ÷ 3` from the sketch lives here. |
| 2 | `÷2`, `÷5`, `÷10` to 20 | Halving and the easy tables. Two circles is visibly "half". |
| 3 | `÷3`, `÷4` within known tables | First real sharing — enough rounds that the rotation is felt. |
| 4 | Any table fact to `100 ÷ 10` | Crates of ten appear. |
| 5 | Remainders | Only once a full group is a solid idea. |
| 6 | Symbols only | Fluency. **X** peeks, at a price in points, never in time. |

## 13. Object sets

Cars, apples, coins, ducks, socks, pizza slices. One set per round so the
picture stays fresh, all drawn to the same silhouette size so circles stay
comparable at a glance. Socks earn their place because a pair makes `÷2` obvious
before anything has moved.

## 14. Technical notes

One HTML file, 2D canvas, flat high-contrast art, no build step, nothing from
the network. Everything must read from the back of a classroom, so type and
objects are sized for a projector rather than a desk.

The moving animation caps at about 2.5 seconds however many objects there are:
roughly 120 ms each up to a dozen, then it accelerates. **R** skips the rest.

Gamepad input is polled per frame rather than evented — the game loop already
runs, so it costs nothing, but presses need edge detection (compare this frame's
`pressed` against last frame's) rather than a keydown handler, and every
repeatable action needs a repeat delay or one press moves three cars.

## 15. First prototype

The move, one object set, sharing *and* grouping, rungs 1–3, stage 2 numbers,
the controller layer with its two-press calibration, and the random picker.
