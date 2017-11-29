<template>
  <li class="delivery-orders">
    <div class="left">
      <ul style="padding: 0;">
        <li class="list-items"><h3 style="margin: 0;">order_id: {{ order.order_id }}</h3></li>
        <li class="list-items">delivery_date: {{ order.delivery_date }}</li>
        <li class="list-items">delivery_time: {{ order.delivery_time }}</li>
        <li class="list-items">feedback_submitted: {{ order.feedback_submitted }}</li>
      </ul>
    </div>
    <div class="right">
      <h4 style="margin: 0;">order_items</h4>
      <ul style="padding: 0;">
        <li v-for="order_items in order.order_items" class="list-items">
          {{ order_items.order_item_id }}: {{ order_items.name }}
        </li>
      </ul>
    </div>
    <button v-if="order.feedback_submitted === false" @click="showModal=true">Submit Feedback</button>
    <transition name="fade">
      <feedback v-if="showModal" @close="showModal=false" :order='order'></feedback>
    </transition>
  </li>
</template>

<script>
  import Feedback from './feedback'

  export default {
    name: 'deliveryorder',
    components: {
      'feedback': Feedback
    },
    props: {
      order: {
        type: Object
      }
    },
    data() {
      return {
        showModal: false
      }
    },
    methods: {

    }
  }
</script>

<style scoped>
  h1, h2 {
    text-align: center;
  }

  .delivery-orders {
    margin-bottom: 50px;
    display: block;
  }

  .left, .right {
    display: inline-block;
    vertical-align: top;
    margin: 0 10px;
  }

  .list-items {
    display: block;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s
  }

  .fade-enter, .fade-leave-to {
    opacity: 0
  }
</style>
