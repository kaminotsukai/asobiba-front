<template>
    <div class="px-2 pt-8">
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
