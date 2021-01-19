<template>
  <div class="home">
    <input type="text" maxlength="7" v-model="zipcode">
    <button @click="search()">住所自動入力</button>
    <p>Address：{{ address }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zipcode: "",
      address: ""
    };
  },
  methods: {
    async search() {
      const address = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.zipcode}?apikey=ggw9X7s8Q6v6Au8ceYhhapmW3ZcnhTUbRhPbHmA`);

      const addressData = address.data;
      this.address = addressData[0].allAddress;
    }
  }
}
</script>
