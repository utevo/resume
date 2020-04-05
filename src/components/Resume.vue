<template>
  <div class="resume">
    <div class="left-column">

      <div class="headline">
        <div class="headline-name">
          <span>{{ person.name.first }} {{ person.name.middle }}</span>
          <span class="uppercase">{{ person.name.last }}</span>
        </div>

        <p>
          <span class="txt-full-white">{{ person.position }}</span>
          <br />
          <span class="uppercase">{{ person.contact.city }}, {{ person.contact.country }}</span>
        </p>
      </div>

      <div class="txt-multiline">{{ person.about }}</div>

      <div class="txt-multiline">{{ person.about }}</div>
    </div>

  </div>
</template>

<script>
import Vue from "vue";
import { importData } from "../data/data.js";

const name = "Resume";
export default Vue.component(name, importData());
</script>


<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
