### tooling

build using no-build-tools approach, but strip out wp-specific stuff


### process

before writing any code...
- [ ] learn the rules
- [ ] read about the game
- [ ] think through the whole thing, write it all down in comments, and go back and refine it until you're confident it's right
- [ ] break it down into small, easy to build chunks

only then should you start writing any code
- [ ] start w/ the UI and do that entirely (ala "thinking in react"). just a single html and css file. use htm instead of jsx
- [ ] break into component files
- [ ] stop and think through the rest of the process. write down tasks here,
	break them into small chunks that are easy to understand and do in small amount of time, don't combine multiple things into a single step
	don't do a waterfall, just break into high level conceptual chunks.
		then for each chunk take an agile approach, but write it all out on paper first like have done w/ high level concepts



### rules

( from wikipedia, may be worth checking out a more academic source too )

The universe of the Game of Life is an infinite, two-dimensional orthogonal grid of square cells,
each of which is in one of two possible states, live or dead, (or populated and unpopulated, respectively).

Every cell interacts with its eight neighbours, which are the cells that are horizontally, vertically, or diagonally adjacent.
At each step in time (what exactly does that mean? how does time work in this simulation?), the following transitions occur:

* Any live cell with fewer than two live neighbours dies, as if by underpopulation (loneliness).
* Any live cell with two or three live neighbours lives on to the next generation.
* Any live cell with more than three live neighbours dies, as if by overpopulation (crowding,draining)
* Any dead cell with exactly three live neighbours becomes a live cell, as if by reproduction.

These rules, which compare the behavior of the automaton to real life, can be condensed into the following:

* Any live cell with two or three live neighbours survives.
* Any dead cell with three live neighbours becomes a live cell.
* All other live cells die in the next generation. Similarly, all other dead cells stay dead.

The initial pattern constitutes the seed of the system. The first generation is created by applying the above rules ___simultaneously___ to
 every cell in the seed, live or dead; births and deaths occur simultaneously, and the discrete moment at which this happens is sometimes called a "tick".
  ___Each generation is a ***pure function*** of the preceding one___. The rules continue to be applied repeatedly to create further generations.




### rough thoughts (turn this into pseudocode?)

look at other implementations to get ideas, UI but not code
after write initial version, then look at other code and compare


start w/ 9x9 grid, get working, then expand?
for every cell, look at every cell around them (in what order?)
if {condition} then {live/die}

does the game specify what order to do things in, b/c that will affect how it runs
	or is that just left as an implementation detail?
	maybe it's part of the academic paper on the rules, but not part of the common description
	or maybe it doesn't have to be a for() loop? maybe could choose select a random order each round, and access them directly?
	or maybe there's some other way? maybe each one acts independently like an object, rather than a top-down approach?
		if you do that, then it may be dependent on how react/javascript/firefox process events/etc, which might distort but might be fine
	or maybe have a "shadow" grid of something where the state of or real grid is examined, and then saved to the shadow grid
		at end of round, shadow grid becomes real grid. that way none of the changes in the shadow grid are taken into account when processing the real grid?
			{but maybe that'd mess it up?
			could call it a "generation" instead of "shadow".
			in general, when naming things, using terms that are analagous to real life
				also be consistent w/ the terms used in other implementations
		yeah, this approach is probably what the "pure function" in the rules is talking about


### v2 also want buttons to:
 * control how fast if runs (and be able to change it in real time)
 * pause and restart (maybe be able to make adjustments while paused?)
 * make adjustments while running?
 * button to generate random seed state
