<template>
  <h1>Historial de pedidos</h1>
  <p v-for="order in orders" :key="order.id">
    <span>ID: {{ order.id }} -</span>
    <a :href="`https://GranjaFlask.mechell.repl.co/orders/${order.id}`">Detalles</a>
  </p>
</template>

<script>
export default {
  props: ['inventory', 'addToCart'],
  data () {
    return {
      orders: [],
      dataReady: false
    }
  },
  async mounted () {
    const response = await (await fetch('https://GranjaFlask.mechell.repl.co/orders')).json()
    this.orders = response.data
    this.dataReady = true
  }
}
</script>

<style>
</style>
