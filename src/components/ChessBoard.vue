<template>
  <img alt="Vue logo" src="@/assets/board.png" />

  <button @click="logger">log</button>


<section class="boardSection">
  <div v-for="(file, i) in board" :key="i">

    <div v-for="(rank, j) in board[i]" :key="j" :id="board[i][j].file+board[i][j].rank" class="square" :class="classes(i, j)">
        {{board[i][j].file}}{{board[i][j].rank}}
        <br>
        {{board[i][j].piece}}
        <!-- <img class="figureImg" :src="imageUrl(board[i][j].piece)" /> -->
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
      "piece": {name: "wRook", history: null}
    },
    {
      "file": "a",
      "rank": 2,
      "piece": "wPawn",
      "function": movePawn
    },
    {
      "file": "a",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "a",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "a",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "a",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "a",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "a",
      "rank": 8,
      "piece": "bRook"
    }
  ],
  [
    {
      "file": "b",
      "rank": 1,
      "piece": "wKnight"
    },
    {
      "file": "b",
      "rank": 2,
      "piece": "wPawn"
    },
    {
      "file": "b",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "b",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "b",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "b",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "b",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "b",
      "rank": 8,
      "piece": "bKnight"
    }
  ],
  [
    {
      "file": "c",
      "rank": 1,
      "piece": "wBishop"
    },
    {
      "file": "c",
      "rank": 2,
      "piece": "wPawn"
    },
    {
      "file": "c",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "c",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "c",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "c",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "c",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "c",
      "rank": 8,
      "piece": "bBishop"
    }
  ],
  [
    {
      "file": "d",
      "rank": 1,
      "piece": "wQueen"
    },
    {
      "file": "d",
      "rank": 2,
      "piece": "wPawn"
    },
    {
      "file": "d",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "d",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "d",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "d",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "d",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "d",
      "rank": 8,
      "piece": "bQueen"
    }
  ],
  [
    {
      "file": "e",
      "rank": 1,
      "piece": "wKing"
    },
    {
      "file": "e",
      "rank": 2,
      "piece": "wPawn"
    },
    {
      "file": "e",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "e",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "e",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "e",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "e",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "e",
      "rank": 8,
      "piece": "bKing"
    }
  ],
  [
    {
      "file": "f",
      "rank": 1,
      "piece": "wBishop"
    },
    {
      "file": "f",
      "rank": 2,
      "piece": "wPawn"
    },
    {
      "file": "f",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "f",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "f",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "f",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "f",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "f",
      "rank": 8,
      "piece": "bBishop"
    }
  ],
  [
    {
      "file": "g",
      "rank": 1,
      "piece": "wKnight"
    },
    {
      "file": "g",
      "rank": 2,
      "piece": "wPawn"
    },
    {
      "file": "g",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "g",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "g",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "g",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "g",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "g",
      "rank": 8,
      "piece": "bKnight"
    }
  ],
  [
    {
      "file": "h",
      "rank": 1,
      "piece": "wRook"
    },
    {
      "file": "h",
      "rank": 2,
      "piece": "wPawn"
    },
    {
      "file": "h",
      "rank": 3,
      "piece": ""
    },
    {
      "file": "h",
      "rank": 4,
      "piece": ""
    },
    {
      "file": "h",
      "rank": 5,
      "piece": ""
    },
    {
      "file": "h",
      "rank": 6,
      "piece": ""
    },
    {
      "file": "h",
      "rank": 7,
      "piece": "bPawn"
    },
    {
      "file": "h",
      "rank": 8,
      "piece": "bRook"
    }
  ]
]

function movePawn(n) {
  // Contstraints:
  // 1. handle 1st click
  // 2. show options
  // 3. handling 2nd click
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
  return `@/assets/${piece}.png`
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
}


.light {
  background-color: white;
}

.dark {
  background-color: rgb(126, 126, 126);
  color: white;
}

.figureImg {
  width: 50px;
  height: 50px;
  margin-inline: auto;
}
</style>
