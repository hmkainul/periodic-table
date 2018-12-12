<template>
  <div class="home">
    <ChemicalElement number="1" symbol="H" name="Hydrogen" weight="1.008"/>
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import ChemicalElement from '@/components/ChemicalElement.vue';

@Component({
  components: {
    HelloWorld,
    ChemicalElement,
  },
})
export default class Home extends Vue {}
</script>
