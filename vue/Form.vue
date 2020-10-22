<template>
  <form class="creditcard">
      <div class="form_cc">
        <label for="name">Name</label><br>
        <input class="input" type="text" name="cc_name"><br>
        <label for="cc_number">Number</label><br>
        <input class="input" @input="event => number=event.target.value" v-bind:value="number | cardNumberFormat" type="text" name="cc_number"><br>
        
        <div class="key_cc">
        <label for="name">CCV2</label><br>
        <input class="input" type="text" name="cc_cvv">
        <label for="name">Expiration Date</label><br>
        <input class="input" type="text" name="cc_expiration"><br>
        </div>
        
        <input type="submit" value="Pay">
      </div>
  </form>
</template>

<script>
const creditcards = require('creditcards');

export default {
  name: 'Form',
  filters: {
    cardNumberFormat: function(value) {
      return creditcards.card.format(creditcards.card.parse(value));
    },
  },
  data() {
    return {
      type: '',
      name: '',
      number: '',
      expiration: '',
      cvv: '',
    };
  },
};
</script>