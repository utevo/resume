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

      <div class="txt-multiline">{{ person.knowledge }}</div>
    </div>

    <div class="contact-container">
      <a v-if="person.contact.email"
        :href="contactLinks.email"
        class="external-link">
        <i class="contact-icon material-icons">mail</i>
        <span class="block-marged txt-full-white">
          {{ person.contact.email }}
        </span>
      </a>

      <a v-if="person.contact.phone"
        :href="contactLinks.phone"
        class="external-link">
        <i class="contact-icon material-icon">mail</i>
        <span class="block-marged txt-full-white">
          {{ person.contact.phone }}
        </span>
      </a>

      <a v-if="person.contact.github"
        :href="contactLinks.github"
        class="external-link">
        <i class="contact-icon fa fa-github"></i>
        <span class="block-marged txt-full-white">
          {{ person.contact.github }}
        </span>
      </a>
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
