<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layout>
    <template #header>
      <Header></Header>
    </template>
    <template #resume>
      <Resume
        :total-label="'Ahorro total'"
        :label="label"
        :total-amount="totalAmount"
        :amount="amount"
      >
        <template #graphic>
          <Graphic :amounts="amounts" @select="select" />
        </template>
        <template #action>
          <Action @create="create" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements
        :movements="movements"
        @remove="remove"
      />
    </template>
  </Layout>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';
import Layout from "./Layout.vue";
import Header from "./Header.vue";
import Resume from "./Resume/Index.vue";
import Action from "./Action.vue";
import Movements from "./Movements/index.vue";
import Graphic from "./Resume/Graphic.vue";

const label = ref(null);
const amount = ref(null);
const movements = ref([]);

const amounts = computed(() => {
  const lastDays = movements.value
    .filter(m => {
      const today = new Date();
      const oldDate = today.setDate(today.getDate() - 30);
      return m.time > oldDate;
    })
    .map(m => m.amount);

  return lastDays.map((m, i) => {
    const lastMovements = lastDays.slice(0, i);
    return lastMovements.reduce((suma, movement) => suma + movement, 0);
  });
});

const totalAmount = computed(() => {
  return movements.value.reduce((suma, m) => suma + m.amount, 0);
});

const create = (movement) => {
  movements.value.push(movement);
  save();
};

const remove = (id) => {
  const index = movements.value.findIndex(m => m.id === id);
  movements.value.splice(index, 1);
  save();
};

const save = () => {
  localStorage.setItem("movements", JSON.stringify(movements.value));
};


const select = (el) => {
  console.log(el);
  amount.value = el;
};

onMounted(() => {
  const savedMovements = JSON.parse(localStorage.getItem("movements"));
  if (Array.isArray(savedMovements)) {
    movements.value = savedMovements.map(m => ({
      ...m,
      time: new Date(m.time)
    }));
  }
});
</script>
