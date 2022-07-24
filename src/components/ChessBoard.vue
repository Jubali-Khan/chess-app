<template>
  <img alt="Vue logo" src="@/assets/board.png" />

  <button @click="logger">log</button>


<section class="boardSection" id="board">
  <div v-for="(file, i) in board" :key="i">

    <div
    v-for="(rank, j) in board[i]" :key="j"
    :id="board[i][j].file+board[i][j].rank"
    class="square"
    :class="classes(i, j)"
    @click="squareClickHandler(board[i][j])"
    >
        <img
        v-if="board[i][j].piece"
        class="figureImg"
        :class="(/^(w|b)[Pawn]{1}/).test(board[i][j].piece) ? 'pawnSqueezer':''"
        :src="require('../assets/'+board[i][j].imagePath)"
        @click.stop="pieceClickHandler(board[i][j], i, j)"
        />
    </div>

  </div>
  
</section>


</template>
<script setup>
import {ref} from "vue"
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
            "piece": "wKing",
            "imagePath": "wKing.png"
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
            "piece": "bKing",
            "imagePath": "bKing.png"
        }
    ],
    [
        {
            "file": "e",
            "rank": 1,
            "piece": "wQueen",
            "imagePath": "wQueen.png"
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
            "piece": "bQueen",
            "imagePath": "bQueen.png"
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


/* function clickHandler(info) {
    console.log("info:", info)
}
 */

/*
Moving pieces:
1. click and then select next position
2. drag and drop (later on)

- click and move:
1. 2 different click handlers on img element (piece) and on div element (square)
*/


const pieceAndSquare = ref();

function pieceClickHandler(currentSquare, i, j) {
   
    pieceAndSquare.value = [currentSquare.piece, currentSquare.imagePath, i, j]
 console.log(pieceAndSquare.value)
    /*
    1. store current square's info in squareToClean (index in board array)
    2. update pieceToMove from currentSquare's info
    */
}
function squareClickHandler(targetSquare) {
    console.log('sCK fired')
    /*
    1. update targetSquare's info ({..})
    2. delete info from squareToClean
    */

   targetSquare.piece = pieceAndSquare.value[0];
   targetSquare.imagePath = pieceAndSquare.value[1];
    const i = pieceAndSquare.value[2];
    const j = pieceAndSquare.value[3];
   board[i][j].piece = '';
   board[i][j].imagePath = '';
   console.log('targetSquare', targetSquare.piece)  
}




function classes(file, rank) {
  /* return file%2 === 0 ? (rank%2 === 0 ? 'light' : 'dark') : (rank%2 === 0 ? 'light' : 'dark') */
  const square= file + rank; // this works was thinking of adding +2 because when we loop we start from 0
  return square%2===0?'light' : 'dark'    
}

const imageUrl = (piece) => {
  return `${piece}.png`
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
