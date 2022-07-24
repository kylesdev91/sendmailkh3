<template>
  <div>
    <button @click="sendEmail">Email</button>
  </div>
  <h2>{{ product.id }}</h2>
  <h2>{{ product.name }}</h2>
</template>

<script>
import items from '../data/items';
import axios from 'axios';
export default {
  data() {
    return {
      items: items,
    };
  },
  props: ['product'],
  methods: {
    sendEmail() {
      var content = this.items.reduce(function (a, b) {
        return a + '<tr><td>' + b.id + '</a></td><td>' + b.name + '</td></tr>';
      }, '');
      var formData = {
        emailSubject: 'Online Order',
        emailBody: content,
        orderTotal: 10,
      };
      axios.post('/api/sendmail3', formData).then((response) => {
        console.log(response);
      });
    },
  },
};
</script>
