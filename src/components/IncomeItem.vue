<script setup>


   const props = defineProps({
    income: Object
   })

    const emit = defineEmits(['remove-income'])

    const removeIncome = (income) =>{
        emit('remove-income',income)
    }
   let date = new Date(props.income.date)
   let day = date.getDate()
   let month = date.getMonth()
   let year = date.getFullYear()
   let fullDate = `${day}/${month}/${year}`
   let id = props.income.id
</script>

<template>
    <div class="income-item">
        <div class="removeItem" @click="removeIncome(income)">X</div>
        <div class="desc">{{ income.desc }}</div>
        <div class="price">{{ income.value }}$</div>
        <div class="date">{{fullDate }}</div>
    </div>
</template> 

<style scoped> 
    .income-item {
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0px;
    background-color: #FFF;
    border-radius: 8px;
    max-width: 600px;
    margin: 0 auto 30px;
  }
  .removeItem {
    color: #EF2D2D;
    font-weight: 600;
    font-size: 20px;
    line-height: 1;
    text-align: center;
    margin: 0 15px;
  }
  .desc {
    color: #666;
    flex: 1 1 100%;
    font-size: 20px;
  }
  .price {
    color: #666;
    min-width: 100px;
    font-size: 20px;
  }
  .date {
    color: #666;
    text-align: right;
    font-size: 20px;
  }
</style>