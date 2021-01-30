# First frame timings

## MacBook Pro, a while ago

### Vanilla (Naive)
- a: render(235) layout(1633) draw(100) frame(1992)
- ab: render(225) layout(292) draw(22) frame(558)
- abo: render(100) layout(98) draw(10) frame(218)
- abou: render(85) layout(85) draw(10) frame(194)
- about: render(85) layout(85) draw(10) frame(191)

### Vanilla (Naive 2)
- a: render(95) layout(1636) draw(100) frame(1845)
- ab: render(114) layout(292) draw(18) frame(444)
- abo: render(21) layout(95) draw(10) frame(137)
- abou: render(11) layout(85) draw(10) frame(117)
- about: render(12) layout(86) draw(10) frame(118)

### Vanilla (Incremental)
- a: render(15) layout(85) draw(<10) frame(126)
- ab: render(93) layout(40) draw(<10) frame(150)
- abo: render(25) layout(15) draw(<10) frame(56)
- abou: same as above
- about: same as above

### React (Naive)
- a: render(95) framework(632) layout(1634) draw(100) frame(2484)
- ab: render(16) framework(570) layout(63) draw(25) frame(687)
- abo: render(5) framework(73) layout(26) draw(10) frame(124)
- abou: render(3) framework(23) layout(20) draw(10) frame(66)
- about: render(3) framework(15) layout(1) draw(<10) frame(33)

### React (Naive, Faster Diffing)
- a: render(96) framework(527) layout(1634) draw(100) frame(2375)
- ab: render(14) framework(106) layout(195) draw(20) frame(543)
- abo: render(5) framework(45) layout(95) draw(10) frame(168)
- abou: render(3) framework(33) layout(85) draw(10) frame(140)
- about: render(3) framework(29) layout(85) draw(10) frame(133)

### React (Naive Incremental)
- a: render(9) framework(89) layout(88) draw(10) frame(200)
- ab: render(4) framework(450) layout(35) draw(<10) frame(500)
- abo: render(1) framework(118) layout(9) draw(<10) frame(139)
- abou: render(<1) framework(68) layout(4) draw(<10) frame(78)
- about: render(<1) framework(63) layout(4) draw(<10) frame(74)

### React (Incremental Portals)
- a: render(100) framework(806) layout(88) draw(10) frame(1023)
- ab: render(16) framework(894) layout(42) draw(<10) frame(974)
- abo: render(6) framework(321) layout(14) draw(<10) frame(358)
- abou: render(4) framework(254) layout(10) draw(<10) frame(280)
- about: render(4) framework(237) layout(10) draw(<10) frame(263)


## Windows PC, Core i7-6700K 4.00GHz (Development Builds)

On all of these tests there is a pre-layout pass that happens before
rendering each frame. This contributes to the overall frame time
but I didn't write it down. This explains why frame times are sometimes
significantly higher than the sum of the other measurements.

### Vanilla (Naive)

| query | render/commit | layout | draw | frame total |
| ----- | ------------- | ------ | ---- | ----------- |
| a     | 1030          | 5514   | 577  | 7164        |
| ab    | 467           | 740    | 47   | 3000        |
| abo   | 39            | 182    | 15   | 378         |
| abou  | 22            | 135    | 14   | 216         |
| about | 23            | 127    | 14   | 205         |

### React (Naive)

| query | render | commit | layout | draw | frame total |
| ----- | ------ | ------ | ------ | ---- | ----------- |
| a     | 3690   | 200    | 5340   | 568  | 9889        |
| ab    | 305    | 1530   | 682    | 60   | 4456        |
| abo   | 63     | 94     | 135    | 16   | 509         |
| abou  | 51     | 13     | 109    | 16   | 250         |
| about | 48     | 7      | 102    | 15   | 225         |

### Vue (Naive)

| query | render/commit | layout | draw | frame total |
| ----- | ------------- | ------ | ---- | ----------- |
| a     | 4380          | 4896   | 537  | 9879        |
| ab    | 3350          | 546    | 51   | 5494        |
| abo   | 169           | 107    | 16   | 440         |
| abou  | 75            | 84     | 14   | 226         |
| about | 60            | 80     | 14   | 198         |
