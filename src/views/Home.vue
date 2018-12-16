<template>
  <PeriodicTable/>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import PeriodicTable from '@/components/PeriodicTable.vue';

@Component({
  components: {
    PeriodicTable,
  },
})
export default class Home extends Vue {
}
</script>
