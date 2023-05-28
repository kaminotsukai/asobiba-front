<template>
    <div class="px-2 pt-8 sudoku-font">
        <SudokuBoard
            :board="data.board"
        ></SudokuBoard>
        <div class="grid grid-cols-4 gap-1 mt-10">
            <div
                class="h-16 border rounded border-slate-200 font-display w-full bg-white items-center justify-center text-2xl cursor-pointer flex"
                v-for="value in 10" :key="value"
                @click="selectQuestion(value)"
            >
                問題{{ value }}
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from '@nuxtjs/composition-api'
import SudokuBoard from '~/components/sudoku/Board.vue'
import q1 from '~/assets/contents/questions/1.json'
import q2 from '~/assets/contents/questions/2.json'
import q3 from '~/assets/contents/questions/3.json'
import q4 from '~/assets/contents/questions/4.json'
import q5 from '~/assets/contents/questions/5.json'
import q6 from '~/assets/contents/questions/6.json'
import q7 from '~/assets/contents/questions/7.json'
import q8 from '~/assets/contents/questions/8.json'
import q9 from '~/assets/contents/questions/9.json'
import q10 from '~/assets/contents/questions/10.json'

type Cell = {
    value: number;
    readonly: boolean;
};

type Board = Cell[][];


export default defineComponent({
    name: "SudokuIndex",
    components: {
        SudokuBoard
    },
    setup() {
        const initBoard = () => {
            let board: Board = []
            for (let i = 0; i < 9; i++) {
                board[i] = [];
                for (let j = 0; j < 9; j++) {
                    board[i][j] = { "value": 0, "readonly": true }
                }
            }
            return board
        }

        const data = reactive({
            board: initBoard(),
        });

        const selectQuestion = async (value: number) => {
            if (value == 1) {
                data.board = [...q1]
            }
            if (value == 2) {
                data.board = [...q2]
            }
            if (value == 3) {
                data.board = [...q3]
            }
            if (value == 4) {
                data.board = [...q4]
            }
            if (value == 5) {
                data.board = [...q5]
            }
            if (value == 6) {
                data.board = [...q6]
            }
            if (value == 7) {
                data.board = [...q7]
            }
            if (value == 8) {
                data.board = [...q8]
            }
            if (value == 9) {
                data.board = [...q9]
            }
            if (value == 10) {
                data.board = [...q10]
            }
        }

        return {
            data,
            selectQuestion
        }
    }
})
</script>

<style scoped>
.sudoku-font {
    font-family: Arial,"ヒラギノ角ゴ Pro W3","Hiragino Kaku Gothic Pro",Osaka,"メイリオ",Meiryo,"ＭＳ Ｐゴシック","MS PGothic",sans-serif;
    font-weight: bold;
    color: #767d88;
}
</style>
