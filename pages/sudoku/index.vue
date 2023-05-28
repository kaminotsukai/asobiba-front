<template>
    <div class="px-2 pt-8 sudoku-font">
        <SudokuBoard/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from '@nuxtjs/composition-api'
import SudokuBoard from '~/components/sudoku/Board.vue'

export default defineComponent({
    name: "SudokuIndex",
    components: {
        SudokuBoard
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
