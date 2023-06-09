<template>
    <div>
        <div class="w-full">
            <div class="flex justify-center w-full items-center">
                <div class="grid grid-cols-9 grid-flow-col">
                    <div v-for="col, i1 in board" :key="i1">
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
        <div class="grid grid-cols-9 gap-1 mt-5">
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
import { PropType } from "vue/types/v3-component-props";
import SudokuCell from "./Cell.vue"

type Cell = {
    value: number;
    readonly: boolean;
};

export default defineComponent({
    name: "SudokuBoard",
    components: {
        SudokuCell,
    },
    props: {
        board: {
            type: Array as PropType<Cell[][]>,
            required: true
        }
    },
    setup(props) {
        let data = reactive({
            selectedCell: [-1, -1],
        })

        const selectCell = (row: number, col: number) => {
            data.selectedCell = [row, col]
        }

        const inputNumber = (value: number) => {
            if (data.selectedCell == undefined || data.selectedCell[0] == -1 || data.selectedCell[1] == -1) {
                return
            }
            const cell = props.board[data.selectedCell[1]][data.selectedCell[0]]
            if (cell.readonly) {
                return
            }
            props.board[data.selectedCell[1]][data.selectedCell[0]].value = value
        }

        return {
            data,
            selectCell,
            inputNumber
        }
    },

})
</script>
