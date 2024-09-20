<template>
     <div class="inc-exp-container">
        <div>
          <h4>Income</h4>
          <p id="money-plus" class="money plus">+${{Income}}</p>
        </div>
        <div>
          <h4>Expense</h4>
          <p id="money-minus" class="money minus">-${{Expenses}}</p>
        </div>
      </div>
</template>

<script setup>
import {defineProps} from 'vue';

const Props = defineProps({
  Income:{
    type:Number,
    requied:true,

  },
  Expenses:{
    type:Number,
    requied:true,
    
  }
})
</script>
