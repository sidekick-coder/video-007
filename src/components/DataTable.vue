<script setup>

defineProps({
    columns: {
        type: Array,
        default: () => []
    },
    rows: {
        type: Array,
        default: () => []
    }
})

const tdAttrs = {
    class: 'border px-4 py-2 text-left'
}

</script>
<template>
    <table class="w-full border">
        <thead>
            <tr>
                <th
                    v-for="(c, index) in columns" :key="index"
                    v-bind="tdAttrs"
                >
                    {{  c.label  }}
                </th>
            </tr>
        </thead>

        <tbody>

            <tr v-for="(r, index) in rows" :key="index">
                <slot
                    v-for="(c, index) in columns"
                    :key="index"
                    :name="`row-${c.field}`"
                    :row="r"
                    :attrs="tdAttrs"
                >                
                    <td  v-bind="tdAttrs">
                        {{ r[c.field]  }}
                    </td>
                </slot>
            </tr>
        </tbody>

    </table>
</template>