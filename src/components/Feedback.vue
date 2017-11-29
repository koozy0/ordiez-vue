<template>
  <div class="feedback">
    <form class="formLayout">
      <h1>feedback</h1>
      <div class="textarea">
        <div style="width: 100%;">
          <div class="col-left">
            <label style="width: 100%;">How was your delivery?
              <input type="text" style="width: 95%;">
            </label>
          </div>
          <div class="col-right">
            <div>
              <label>Positive:
                <input type="radio" name="feedback" value="1">
              </label>
              <label>Negative:
                <input type="radio" name="feedback" value="-1">
              </label>
            </div>
          </div>
        </div>
        <div v-for="order_items in order.order_items" style="width: 100%;">
          <div class="col-left">
            <label style="width: 100%;">How was your {{ order_items.name }}?
              <input type="text" style="width: 95%;">
            </label>
          </div>
          <div class="col-right">
            <div>
              <label>Positive:
                <input type="radio" value="1" v-model="order_items.rating">
              </label>
              <label>Negative:
                <input type="radio" value="-1" v-model="order_items.rating">
              </label>
            </div>
          </div>
        </div>
      </div>
      <br />
      <input type="submit" value="Submit Feedback" v-on:click="submitForm" @click="$emit('close')">
    </form>
    <div class="back"></div>
  </div>
</template>

<script>
  export default {
    name: 'feedback',
    props: {
      order: {
        type: Object
      }
    },
    data() {
      return {

      }
    },
    methods: {
      submitForm: function (e) {
        e.preventDefault()
        console.log('submiting form')
        this.formActive = false
      }
    },
    created: function () {

    }
  }
</script>

<style scoped>
  h1 {
    margin: 0 0 20px 0;
  }
  .feedback {
    position: absolute;
    display: block;
    height: 100%;
    width: 100%;
    top: 0px;
    left: 0px;
  }

  .formLayout {
    background-color: white;
    position: absolute;
    width: 50%;
    height: 50%;
    left: 25%;
    top: 20vh;
    z-index: 1000;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .back {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0,0,0,0.2) !important;
    z-index: 500;
  }

  .textarea {
    width: 80%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .feedback {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .col-left {
    display: inline-block;
    width: 60%;
    height: 100%;
  }

  .col-right {
    display: inline-block;
    width: 35%;
    height: 100%;
  }
</style>
