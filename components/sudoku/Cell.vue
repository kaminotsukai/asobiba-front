<template>
    <div
        class="w-10 h-10 text-2xl border border-[0.5px] border-gray-400"
        :class="[getCellClassList(), getSelectedClassList()]"
    >
        <div
            class="flex items-center justify-center w-full h-full"
            :class="[getReadonlyClassList()]"
            @click="selectCell"
        >
            {{ value === 0 ? '' : value }}
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from '@nuxtjs/composition-api'

export default defineComponent({
    props: {
        value: {
            type: Number,
            required: true,
        },
        row: {
            type: Number,
            required: true,
        },
        col: {
            type: Number,
            required: true,
        },
        readonly: {
            type: Boolean,
            required: true,
        },
        selectedCell: {
            type: Array
        }
    },
    emits: ['select'],
    setup(props, { emit }) {
        const selectCell = () => {
            if (props.readonly) {
                return
            }
            emit('select', props.row, props.col)
        }

        const getCellClassList = () => {
            const classes = []
            if (props.row === 0) {
                classes.push('border-t-2', 'border-t-gray-500')
            }
            if (props.row === 8) {
                classes.push('border-b-2', 'border-b-gray-500')
            }
            if (props.col === 0) {
                classes.push('border-l-2', 'border-l-gray-500')
            }
            if (props.col === 8) {
                classes.push('border-r-2', 'border-r-gray-500')
            }
            if ((props.row + 1) % 3 === 0) {
                classes.push('border-b-2', 'border-b-gray-500')
            }
            if ((props.col + 1) % 3 === 0) {
                classes.push('border-r-2', 'border-r-gray-500')
            }
            return classes
        }

        const getSelectedClassList = () => {
            if (props.selectedCell === undefined) {
                return []
            }
            if (props.row === props.selectedCell[0] && props.col === props.selectedCell[1]) {
                return [
                    'scale-110',
                    'ring-2',
                    'ring-blue-500',
                    'bg-white',
                    'border-none',
                    'text-blue-500'
                ]
            }
        }

        const getReadonlyClassList = () => {
            if (props.readonly) {
                return [
                    'bg-gray-50'
                ]
            }
        }

        return {
            selectCell,
            getCellClassList,
            getSelectedClassList,
            getReadonlyClassList,
        }
    },
})
</script>
