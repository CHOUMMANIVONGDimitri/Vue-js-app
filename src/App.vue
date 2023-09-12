<script setup>
import HelloWorld from './components/HelloWorld.vue';
import FormTest from './components/FormTest.vue';
import SlotComp from './components/SlotComp.vue';

import { ref, reactive } from 'vue';

const title = "Hello World!";
const subTitle = ref("Lorem ipsum dolor sit amet.");
const user = reactive({
  name: "your name",
  age: 20
})

const displayValue = () => {
  console.log(user.name, user.age)
};

displayValue();
</script>

<template>
  <HelloWorld  :title="title" :sub-title="subTitle" />
  <input :class="{'text-red': subTitle.length <= 10}" type="text" v-model="subTitle">

  <FormTest :user="user" />
  <input type="text" v-model="user.name" v-on:input="displayValue">
  <input type="number" v-model="user.age" @input="displayValue" :class="[user.age > 30 ? 'text-green' : 'text-red']">
  <div v-if="user.age > 30" class="text-green">
    Your age is above 30
  </div>

  <SlotComp slot-title="Test slot">
    <template v-slot:pargraphe1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Corrupti, praesentium aperiam. Molestiae ex accusamus ad cumque sapiente cupiditate in nobis voluptatibus placeat, incidunt corporis odio necessitatibus praesentium culpa. In, laborum?
        Quidem voluptas hic quasi excepturi et eveniet adipisci amet veritatis accusantium tempora aut assumenda fugiat, nam ad, quam explicabo porro, tenetur culpa dolorum magnam enim. Deserunt quo autem voluptatum laborum.
        Iure laborum illo saepe ex odio pariatur, sit explicabo aliquam numquam maxime omnis dicta sint praesentium cupiditate soluta, ipsa asperiores eum velit suscipit reiciendis, libero vitae recusandae! Natus, quos facere.
      </p>
    </template>
    <template v-slot:pargraphe2>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Corrupti, praesentium aperiam. Molestiae ex accusamus ad cumque sapiente cupiditate in nobis voluptatibus placeat, incidunt corporis odio necessitatibus praesentium culpa. In, laborum?
        Quidem voluptas hic quasi excepturi et eveniet adipisci amet veritatis accusantium tempora aut assumenda fugiat, nam ad, quam explicabo porro, tenetur culpa dolorum magnam enim. Deserunt quo autem voluptatum laborum.
        Iure laborum illo saepe ex odio pariatur, sit explicabo aliquam numquam maxime omnis dicta sint praesentium cupiditate soluta, ipsa asperiores eum velit suscipit reiciendis, libero vitae recusandae! Natus, quos facere.
      </p>
    </template>
  </SlotComp>
</template>

<style scoped>

.text-red {
  color: #b81b1b;
}
.text-green {
  color: #1bb86f;
}

</style>
