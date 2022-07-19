<template>
  <img alt="Vue logo" src="@/assets/board.png" />

  <button @click="logger">log</button>


<section class="boardSection">
  <div v-for="(file, i) in board" :key="i">

    <div
    v-for="(rank, j) in board[i]" :key="j"
    :id="board[i][j].file+board[i][j].rank"
    class="square"
    :class="classes(i, j)"
    >
        <!-- {{board[i][j].file}}{{board[i][j].rank}}
        <br>
        {{board[i][j].piece}} -->
        <img v-if="board[i][j].piece" class="figureImg" :class="(/^(w|b)[Pawn]{1}/).test(board[i][j].piece) ? 'pawnSqueezer':''" :src="require('../assets/'+board[i][j].imagePath)" />
        <!-- <img  class="figureImg" src="../assets/wKing.png" /> -->
    </div>

  </div>
</section>

</template>
<script setup>
const board = [
    [
        {
            "file": "a",
            "rank": 1,
            "piece": "wRook",
            "imagePath": "wRook.png"
        },
        {
            "file": "a",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "a",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "a",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "a",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "a",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "a",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "a",
            "rank": 8,
            "piece": "bRook",
            "imagePath": "bRook.png"
        }
    ],
    [
        {
            "file": "b",
            "rank": 1,
            "piece": "wKnight",
            "imagePath": "wKnight.png"
        },
        {
            "file": "b",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "b",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "b",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "b",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "b",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "b",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "b",
            "rank": 8,
            "piece": "bKnight",
            "imagePath": "bKnight.png"
        }
    ],
    [
        {
            "file": "c",
            "rank": 1,
            "piece": "wBishop",
            "imagePath": "wBishop.png"
        },
        {
            "file": "c",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "c",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "c",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "c",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "c",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "c",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "c",
            "rank": 8,
            "piece": "bBishop",
            "imagePath": "bBishop.png"
        }
    ],
    [
        {
            "file": "d",
            "rank": 1,
            "piece": "wQueen",
            "imagePath": "wQueen.png"
        },
        {
            "file": "d",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "d",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "d",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "d",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "d",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "d",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "d",
            "rank": 8,
            "piece": "bQueen",
            "imagePath": "bQueen.png"
        }
    ],
    [
        {
            "file": "e",
            "rank": 1,
            "piece": "wKing",
            "imagePath": "wKing.png"
        },
        {
            "file": "e",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "e",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "e",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "e",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "e",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "e",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "e",
            "rank": 8,
            "piece": "bKing",
            "imagePath": "bKing.png"
        }
    ],
    [
        {
            "file": "f",
            "rank": 1,
            "piece": "wBishop",
            "imagePath": "wBishop.png"
        },
        {
            "file": "f",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "f",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "f",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "f",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "f",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "f",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "f",
            "rank": 8,
            "piece": "bBishop",
            "imagePath": "bBishop.png"
        }
    ],
    [
        {
            "file": "g",
            "rank": 1,
            "piece": "wKnight",
            "imagePath": "wKnight.png"
        },
        {
            "file": "g",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "g",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "g",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "g",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "g",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "g",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "g",
            "rank": 8,
            "piece": "bKnight",
            "imagePath": "bKnight.png"
        }
    ],
    [
        {
            "file": "h",
            "rank": 1,
            "piece": "wRook",
            "imagePath": "wRook.png"
        },
        {
            "file": "h",
            "rank": 2,
            "piece": "wPawn",
            "imagePath": "wPawn.png"
        },
        {
            "file": "h",
            "rank": 3,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "h",
            "rank": 4,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "h",
            "rank": 5,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "h",
            "rank": 6,
            "piece": "",
            "imagePath": ".png"
        },
        {
            "file": "h",
            "rank": 7,
            "piece": "bPawn",
            "imagePath": "bPawn.png"
        },
        {
            "file": "h",
            "rank": 8,
            "piece": "bRook",
            "imagePath": "bRook.png"
        }
    ]
]

function movePawn(n) {
  // Contstraints:
  // 1. handle 1st click (from which square)
  // 2. show options
  // 3. handling 2nd click (to which square)
  // 3.1 on a square where you can move the piece
  // 3.2 on a different square/piece
}


/*
-> data types and data structures for each piece according to its needs
  - e.g. type Pawn = {
    piece: string,

  }
-> clickHandler
  1. show options
    - based on:
      1. piece location show (legal)
        1. capture possibilites
        2. move possibilities
      2.
-> afterMove Handler
  - check for:
    - checks
    - checkmates
    - niche moves:
      - en passant
      - promotions
*/




function classes(file, rank) {
  return file%2 === 0 ? (rank%2 === 0 ? 'light' : 'dark') : (rank%2 === 0 ? 'dark' : 'light')
}

const imageUrl = (piece) => {
  return `${piece}.png`
}

  function logger() {
      console.log("board", board);
      console.log("colorClass", colorClass.value)
  }

</script>

<style>
img {
  width: 500px;
  height: 500px;
}

.boardSection {
    margin: 0 auto;
  width: 800px;
  height: 800px;
  border: 1px solid black;
  display: flex;
}

.square {
  width: 100px;
  height: 100px;
  border: 1px solid black;
  color: black;
  display: grid;
  place-content: center;
}


.light {
  background-color: white;
}

.dark {
  background-color: rgb(126, 126, 126);
  color: white;
}

.figureImg {
  width: 90px;
  height: 90px;
  
}
.figureImg:hover{   
    cursor: pointer;
}
.figureImg:active{
    cursor: grabbing;
}


</style>
