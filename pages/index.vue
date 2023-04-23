<template>
  <div>
    <div>
      <span>{{ onePerson.name }}</span>
      <span>{{ onePerson.salary }}</span>
      <span>{{ onePerson.age }}</span>
    </div>
    <div>
      <span>{{ secondPerson.name }}</span>
      <span>{{ secondPerson.salary }}</span>
      <span>{{ secondPerson.age }}</span>
    </div>
  </div>
</template>

<script>
import Customer from "../components/models/customer";
export default {
  name: "IndexPage",
  data() {
    return {
      onePerson: Customer,
      secondPerson: Customer,
    };
  },
  created() {
    this.person();
  },
  methods: {
    person() {
      this.onePerson = new Customer("Janusz", 20000, 33);
      this.secondPerson = {
        name: "Marian",
        salary: 323232,
        age: 102,
      };
    },
  },
};
</script>

<style scoped></style>