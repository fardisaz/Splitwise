<template>
  <div class="wrapper">
    <h1>Overview</h1>
    <div class="input-section">
      <input type="text" placeholder="Add the purchase" v-model="title" />
      <input type="text" placeholder="$ 0.00" v-model="price" />
      <input type="text" placeholder="Payer" v-model="payer" />
      <button @click="addPayment">Add</button>
    </div>
    <ul class="payment-list">
      <li v-for="payment in paymentList">
        <span>{{ payment.purchasTitle }}</span>
      </li>
    </ul>
  </div>
</template>
<script setup>
import { ref } from 'vue'
const title = ref('')
const price = ref('')
const payer = ref('')
const paymentList = ref([])
function addPayment() {
  const _title = title.value.trim()
  const _price = price.value.trim()
  const _payer = payer.value.trim()
  if (_title && _price && _payer) {
    paymentList.value.push({
      id: Date.now(),
      purchasTitle: _title,
      price: _price,
      payer: _payer,
    })
    title.value = ''
    price.value = ''
    payer.value = ''
    console.log(paymentList)
  }
}
</script>
<style scoped>
.wrapper {
  font-family: 'Lucida Console', 'Courier New', monospace;
  text-align: center;
  color: #737365;
}
.input-section {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  gap: 12px;
}

.input-section input,
.input-section button {
  width: 100%; /* makes inputs & button full width of the box */
  padding: 10px;
  border-radius: 5px;
  border: 1px solid lightgray;
  box-sizing: border-box; /* important! */
}
.input-section button {
  background-color: #737365;
  color: white;
  cursor: pointer;
  margin-top: 5px;
}
.input-section button:hover {
  background-color: #4d4545;
}
.payment-list {
  list-style-type: none;
}
</style>
