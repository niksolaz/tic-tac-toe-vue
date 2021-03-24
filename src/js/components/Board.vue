<template>
    <div class="board">
        <div v-for="(n, i) in 3" :key="i">
            <div v-for="(n, j) in 3" :key="j">
                <Square :id="i + '-' + j" :value="squares[i][j]" @click="performMove(i, j)"/>
            </div>
        </div>
        <div class="board-info">
            <h3>Player: {{player}}</h3>
            <h3 v-if="winner !== ''">Winner is: {{winner}}</h3>
            <button @click="startNewGame()">Start new game!</button>
        </div>
    </div>
</template>

<script>
    import Vue from "vue";
    import Square from "./Square";

    export default Vue.extend({
        name: "Board",
        components: {
            Square
        },
        data() {
            return {
                squares: [
                    ["","", ""],
                    ["","", ""],
                    ["","", ""]
                ],
                isNextX: true,
                winner: "",
                player: "",
            }
        },
        methods: {
            performMove(x, y) {
                if(this.squares[x][y] !== "" ) {
                    return;
                }
                if(this.winner !== "") {
                    return;
                }
                console.log(x,y);
                this.player = this.isNextX ? "X" : "O";
                this.isNextX = !this.isNextX;
                this.squares[x][y] = this.player;
                this.$forceUpdate();
                this.getWinner(this.player)
            },
            getWinner(player) {
                for(let i=0;  i<3; i++) {
                    // Orizontal
                    if(this.squares[0][i] === player && this.squares[1][i] === player && this.squares[2][i] === player) {
                        this.winner = player;
                        return;
                    }

                    // Vertical
                    if(this.squares[i][0] === player && this.squares[i][1] === player && this.squares[i][2] === player) {
                        this.winner = player;
                        return;
                    }

                    // Diagonal
                    if(this.squares[0][0] === player && this.squares[1][1] === player && this.squares[2][2] === player || this.squares[2][0] === player && this.squares[1][1] === player && this.squares[0][2] === player) {
                        this.winner = player;
                        return;
                    }
                }
            },
            startNewGame() {
                this.squares = [
                    ["","", ""],
                    ["","", ""],
                    ["","", ""]
                ];
                this.isNextX = true;
                this.winner = "";
                this.player = "";
            }
        }
    });
</script>

<style lang="scss">
.board {
    display: flex;
    flex-direction: row;
    width: 500px;
    height: 400px;
    .board-info {
        margin-left: 30px;
        button {
            margin-top: 10px;
            border: 1px solid rgb(99, 192, 131);
            border-radius: 15px;
            box-shadow: 1px 2px 5px rgb(77, 108, 77);
            background-color: rgb(99, 192, 131);
            color: #FFF;
            text-shadow: 0px 2px 2px rgb(77, 108, 77);
            padding: 10px;
            font-size: 15px;
            font-weight: bold;
            font-family:Arial, Helvetica, sans-serif;
            cursor: pointer;

            &:active {
                box-shadow: 1px 1px 1px rgb(77, 108, 77);
            }
            &:focus {
                border: hidden;
                outline: none;
            }
        }
        h3 {
            font-size: 20px;
            font-weight: bold;
            font-family:Arial, Helvetica, sans-serif;
            color: rgb(99, 192, 131);
            background-color: #FFF;
            text-shadow: 0px 2px 2px rgb(77, 108, 77);
        }
    }
}
</style>