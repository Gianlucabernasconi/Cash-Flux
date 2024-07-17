<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <button @click="showModal = true">Agregar movimiento</button>
  <teleport to="#app">
    <Modal v-show="showModal" @close="showModal = false">
      <form @submit.prevent="submit">
        <div class="field">
          <label>Titulo</label>
          <input type="text" v-model="title" />
        </div>
        <div class="field">
          <label>Monto</label>
          <input type="number" v-model="amount" />
        </div>
        <div class="field">
          <label>Descripcion</label>
          <textarea rows="4" v-model="description" />
        </div>
        <div class="field">
          <label class="radio-label">
            <input type="radio" v-model="movementType" value="Ingreso" />
            <span>Ingreso</span>
          </label>
          <label class="radio-label">
            <input type="radio" v-model="movementType" value="Gasto" />
            <span>Gasto</span>
          </label>
        </div>
        <div class="action">
          <button>Agregar movimiento</button>
        </div>
      </form>
    </Modal>
  </teleport>
</template>

<script setup>
import { ref } from 'vue'
import Modal from './Modal.vue'

const showModal = ref(false)
const title = ref('')
const amount = ref(0)
const description = ref('')
const movementType = ref('Ingreso')

const emit = defineEmits(['Create'])

const submit = () => {
  showModal.value = !showModal.value
  emit('create', {
    title: title.value,
    description: description.value,
    amount: movementType.value === 'Ingreso' ? amount.value : -amount.value,
    time: new Date(),
    id: new Date()
  })
  title.value = ''
  description.value = ''
  amount.value = 0
  movementType.value = 'Ingreso'
}
</script>

<style scoped>
button {
  font-family: 'Genos', sans-serif;
  color: white;
  font-size: 1.25rem;
  background-color: #8a3dc5;
  border: none;
  width: 100%;
  padding: 24px 60px;
  border-radius: 60px;
  box-sizing: border-box;
  box-shadow:
    0 8px 16px 0 rgba(0, 0, 0, 0.2),
    0 6px 20px 0 rgba(0, 0, 0, 0.19);
}

form {
  font-family: 'Genos', sans-serif;
  font-size: 1.24rem;
  width: 100%;
}

form .action {
  padding: 0 24px;
}

.field {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  padding: 16px 24px;
}

label {
  margin-bottom: 8px;
}

input,
textarea {
  font-family: 'Genos', sans-serif;
  font-size: 1.24rem;
  border: 2px solid #8e43c8;
  border-radius: 8px;
  padding: 8px;
}

input[type='number'] {
  text-align: right;
}

.radio-label {
  display: flex;
  align-items: center;
  margin-top: 8px;
}

.radio-label span {
  margin-top: 4px;
  margin-left: 8px;
}

input[type='radio'] {
  appearance: none;
  width: 1.24rem;
  height: 1.24rem;
  color: #8e43c8;
  border: 2px #8e43c8;
  border-radius: 50%;
}

input[type='radio']:checked {
  background-color: #17b169;
}
</style>
