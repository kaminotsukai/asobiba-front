<template>
    <div>
        <div class="w-full">
            <div class="flex justify-center w-full items-center">
                <div class="grid grid-cols-9 grid-flow-col">
                    <div v-for="col, i1 in data.board" :key="i1">
                        <div v-for="cell, i2 in col" :key="i2">
                            <SudokuCell
                                :value="cell.value"
                                :col="i1"
                                :row="i2"
                                :readonly="cell.readonly"
                                :selectedCell="data.selectedCell"
                                @select="selectCell"
                            ></SudokuCell>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="grid grid-cols-9 gap-1 mt-1">
            <div
                v-for="value in 9"
                :key="value"
                class="h-16 border  rounded border-slate-200 font-display w-full bg-white items-center justify-center text-2xl cursor-pointer flex"
                @click="inputNumber(value)"
            >{{ value }}</div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from "@nuxtjs/composition-api";
import SudokuCell from "./Cell.vue"

export default defineComponent({
    name: "SudokuBoard",
    components: {
        SudokuCell,
    },
    setup() {
        let data = reactive({
            selectedCell: [-1, -1],
            board: [
                [
                    { value: 1, readonly: true },
                    { value: 2, readonly: true },
                    { value: 3, readonly: true },
                    { value: 4, readonly: true },
                    { value: 5, readonly: true },
                    { value: 6, readonly: true },
                    { value: 7, readonly: true },
                    { value: 8, readonly: true },
                    { value: 9, readonly: true },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
                [
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                    { value: 0, readonly: false },
                ],
            ],
            message: "aaaaaaaa"
        })

        const selectCell = (row: number, col: number) => {
            data.selectedCell = [row, col]
        }

        const inputNumber = (value: number) => {
            if (data.selectedCell == undefined || data.selectedCell[0] == -1 || data.selectedCell[1] == -1) {
                return
            }
            const cell = data.board[data.selectedCell[1]][data.selectedCell[0]]
            if (cell.readonly) {
                return
            }
            data.board[data.selectedCell[1]][data.selectedCell[0]].value = value
        }

        return {
            data,
            selectCell,
            inputNumber
        }
    },

})
</script>
