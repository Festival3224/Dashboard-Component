<script setup lang="ts">
interface Column {
    key: string;
    [key: string]: any;
}

defineProps<{
    rows: Array<{ [key: string]: any}>
    columns: Array<Column>
}>()
</script>

<template>
    <div class="w-full overflow-x-auto">
        <table class="min-w-full">
            <tbody>
                <tr
                  v-for="row in rows"
                  class="hover:bg-gray-100 border-b last-of-type:border-none cursor-pointer"
                >
                 <td v-for="column in columns"
                     class="font-light whitespace-nowrap px-8 py-6"
                 >
                    <slot :name="column.key" :row="row">
                        {{ row[column.key] }}
                    </slot>   
                </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>