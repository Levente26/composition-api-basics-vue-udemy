<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">Change Age</button>
    <div>
      <!-- <input type="text" placeholder="First name" @input="setFirstName" /> -->
      <!-- <input type="text" placeholder="Last name" @input="setLastName" /> -->
      <input type="text" placeholder="First name" v-model="firstName" />
      <input type="text" placeholder="Last name" v-model="lastName" />
    </div>
  </section>
</template>

<script>
import { ref, computed, watch } from 'vue';
// import { reactive } from 'vue';

export default {
  setup() {
    // const uName = ref('Levi');
    const uAge = ref(21);
    const firstName = ref('');
    const lastName = ref('');

    const uName = computed(() => {
      return firstName.value + ' ' + lastName.value;
    });

    watch([uAge, uName], (newVals, oldVals) => {
      console.log('Old age: ' + oldVals[0]);
      console.log('New age: ' + newVals[0]);
      console.log('Old name: ' + oldVals[1]);
      console.log('New name: ' + newVals[1]);
    });

    // const user = reactive({
    //   name: 'Levi',
    //   age: '21',
    // });

    // setTimeout(() => {
    //   uAge.value = '20';
    //   uName.value = 'Demi';
    //   user.name = 'Demi';
    //   user.age = 20;
    // }, 2000);

    const setNewData = () => {
      uAge.value = 22;
    };

    // const setFirstName = (e) => {
    //   firstName.value = e.target.value;
    // };

    // const setLastName = (e) => {
    //   lastName.value = e.target.value;
    // };

    return {
      // user: user,
      // setFirstName: setFirstName,
      // setLastName: setLastName,
      userName: uName,
      age: uAge,
      setAge: setNewData,
      firstName,
      lastName,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
