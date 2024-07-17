<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { defineProps, computed } from 'vue'

// eslint-disable-next-line no-unused-vars
const props = defineProps({
  label: String,
  amount: Number,
  default: null,
  totalAmount: Number
})

const amountCurrency = computed(() => {
  const amount = props.amount !== null ? props.amount : props.totalAmount
  return new Intl.NumberFormat('es-CL', {
    style: 'currency',
    currency: 'CLP',
    minimumFractionDigits: 0
  }).format(amount)
})
</script>

<template>
  <main>
    <p>{{ label }}</p>
    <h1>{{ amountCurrency }}</h1>
    <div class="graphic">
      <slot name="graphic"> </slot>
    </div>
    <div class="action">
      <slot name="action"> </slot>
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

h1,
p {
  margin: 0;
  text-align: center;
}

h1 {
  margin-top: 14px;
  color: #4cbb17;
}

.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>
