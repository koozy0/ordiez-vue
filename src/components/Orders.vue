<template>
  <div class="orders">
    <h1>{{ title }}</h1>
    <h2>user: {{ user.firstName }} {{ user.lastName }}</h2>
    <h2>Orders</h2>
    <ul>
      <deliveryorder v-for="deliveryorder in orders" :order='deliveryorder'></deliveryorder>
    </ul>
  </div>
</template>

<script>
  import DeliveryOrder from '../components/DeliveryOrder.vue'

  export default {
    name: 'orders',
    components: {
      'deliveryorder': DeliveryOrder
    },
    data() {
      return {
        title: 'Ordiez',
        user: {
          firstName: 'John',
          lastName: 'Doe'
        },
        orders: [],
        showModal: false
      }
    },
    methods: {

    },
    created: function () {
      this.$http.get('https://koozy-ordiez.herokuapp.com/orders')
      .then(response => {
        let orders = response.data.orders
        this.orders = orders
      })
    }
  }
</script>

<style scoped>
  h1, h2 {
    text-align: center;
  }
</style>
