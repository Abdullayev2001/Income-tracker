<script setup>
import IncomeItem from './IncomeItem.vue';

const props = defineProps({
    state:Object
})

const emit = defineEmits('onremove')

</script>

<template>
    <div class="income-list">
        <IncomeItem
         v-for="data in state.income"
         :key="data.id"
         :income="data"
         @remove-income="emit('onremove',data.id)"
         />
    </div>
</template>

<style scoped>
    .income-list{
        margin-top: 30px;
        padding: 15px;
    }
</style>