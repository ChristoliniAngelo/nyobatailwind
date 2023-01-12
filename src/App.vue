<script>
import HelloWorld from './components/HelloWorld.vue'
export default {
  data() {
    return {
      listsuhu: [],
    };
  },
  methods: {
     async ambildata(){
      const response = await fetch("http://localhost:80/getlist ");
      const data = await response.json();
      this.listsuhu = data.sensor_suhu
      console.log(this.listsuhu); 
    },
  },
};
</script>

<template>
    <table class="p-10">
      <tr>
        <td>Waktu</td>
        <td>Suhu</td>
      </tr>
      <tr v-for="item in listsuhu"> 
        <td>{{ item.waktu }}</td>
        <td>{{ item.suhu }}</td>
      </tr>
    </table>
    <div>
    <button class="rounded-3xl p-2 bg-orange-600 text-white" @click="ambildata()">Ambil Data</button>
    <button class="rounded-3xl p-2 bg-orange-900 text-white" @click="ambildata()">Ambil Data</button>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
