<script setup>
import {reactive,computed} from 'vue'
import Header from './components/Header.vue';
import Form from './components/Form.vue';
import IncomeList from './components/IncomeList.vue';

const state = reactive({
  income:[],
  sortedIncome: computed(() => {
        let temp = [];
        
        temp = state.income.sort(function (a, b) {
          return b.date - a.date;
        });
        return temp;
      }),
  totalIncome:computed(()=>{
    let temp=0 

    if(state.income.length > 0){
      for(let i = 0; i < state.income.length; i++){
        temp+= state.income[i].value
      }
    }

    return temp
  })
})

const addIncome = (data)=>{
  let d = data.date.split('-')
  let newD = new Date(d[0],d[1],d[2])
  state.income =  [...state.income, {id: Date.now(),...data,date:newD.getTime()}]
}

const removeIncome = (data)=>{
  let res = state.income.filter(inc => inc.id !== data)
  state.income = res
}

</script>

<template>
  <Header :totalIncome="state.totalIncome"/>
  <Form @add-income="addIncome"/>
  <IncomeList :state="state" @onremove="removeIncome"/> 
</template>

<style >
body{
  background-color: #cecece;
}
</style>
