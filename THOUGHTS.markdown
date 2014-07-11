Thoughts
========

MongoDB model
-----------
```

t = top
b = bottom
r = right
l = left

All from center of board.

{
  _id:    <ObjectId>
  cells:  {
            ttll: 0,
            ttl:  0,
            ttr:  0,
            ttrr: 0,
            tmll: 0,
            tml:  0,
            tmr:  0,
            tmrr: 0,
            bmll: 0,
            bml:  0,
            bmr:  0,
            bmrr: 0,
            bbll: 0,
            bbl:  0,
            bbr:  0,
            bbrr: 0,
          },
  highestNum: 0,
  direction:  {
                up:     <ObjectIdUP>,
                down:   <ObjectIdDOWN>,
                left:   <ObjectIdLEFT>,
                right:  <ObjectIdRIGHT>,
              },
  locked: true
  locked_time: DATETIME
  finished: false
}
```

Process
-------

Program it so multiple programs can run at once to map out all possibilities.

1. Open DB connection
2. If DB is empty, prompt for seeding.
3. Prompt for number of entries to process (5, 10, 20, 100, 500, all)
4. Once DB has been seeded, grab first unlocked and unfinished entry (catch for error, retry)
5. Lock it
6. Check if up has <ObjectIdUP>
7. If so, Process board for going up. If not, go to step 10.
8. Lookup new board in database
9. If board exist, up: <ObjectIdOfBoardFound>. Else, create new board entry using cells. (catch for error, retry creation)
10. Repeat 6-8 for down, left, right.
12. Repeat 4-10 until no more unfinished and unlocked entries can be found.

