<template>
<Header />
<div class="container">
<Balance :total="+total" />
<incomeExpenses :Income="+Income" :Expenses="+Expenses"/>
<TransactionList :transactions="transactions" />
<AddTransaction  @transationSubmitted="handleTransationSubmitted"/>
</div>
</template>


<script setup>

import Header  from './components/Header.vue'
import Balance  from './components/Balance.vue'
import incomeExpenses  from './components/incomeExpenses.vue'
import TransactionList  from './components/TransactionList.vue'
import AddTransaction  from './components/AddTransaction.vue'

import {useToast} from 'vue-toastification'

import {ref , computed} from 'vue';

const toast = useToast()

const  transactions= ref([
        {id:1, text:"book" , amount:-19.99},
        {id:2, text:"laptop" , amount:30.99},
        {id:3, text:"Mouse" , amount:50000},
        {id:4, text:"mobile" , amount:59000},
      ]);
         
      //Get Total
      const total = computed (()=>{
        return transactions.value.reduce((acc , transactions)=>{
            return acc + transactions.amount
        },0)
      });

      //Get Income
      const Income = computed (()=>{
        return transactions.value
        .filter((transaction)=> transaction.amount > 0 )
        .reduce((acc , transactions)=>{
            return acc + transactions.amount
        },0).toFixed(2)
      });

      //Get Expenses
      const Expenses = computed (()=>{
        return transactions.value
        .filter((transaction)=> transaction.amount < 0 )
        .reduce((acc , transactions)=>{
            return acc + transactions.amount
        },0).toFixed(2)
      });

      // Add Transaction

      const handleTransationSubmitted = (transactionData) =>{
          transactions.value.push({
            id:generatedUniqueId(),
            text : transactionData.text,
            amount : transactionData.amount
          })

          toast.success("Transaction Add")
        //   console.log(generatedUniqueId())
      }

      // generated Unique Id
 const generatedUniqueId = () =>{
    return Math.floor(Math.random() * 100000)
 }

    
</script>