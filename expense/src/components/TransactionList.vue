<template>
       <h3>History</h3>
      <ul id="list" class="list">
        <li v-for="transaction in transactions" :key="transaction.id" :class="transaction.amount < 0 ? 'minus' : 'plus'">
          {{transaction.text}} <span>${{transaction.amount}}</span><button class="delete-btn" @click="">x</button>

        </li>
        <!-- <li class="minus">
          Cash <span>-$400</span><button class="delete-btn">x</button>
        </li>
        <li class="plus">
          paycheck <span>$400</span><button class="delete-btn">x</button>
        </li> -->
      </ul>
</template>

<script setup>
import {defineProps} from 'vue';

const Props =defineProps({
   transactions:{
     type:Array,
     requird:true,
   }
});
 

</script>
