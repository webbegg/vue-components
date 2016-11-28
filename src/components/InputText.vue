<template>
  <div class="form-group">
    <label :for="name">{{label}} <span class="label label-danger" v-if="required">* requerido</span></label>
    <input :type="type"
           :name="name"
           :value="value"
           @input="update($event.target.value)"
           class="form-control">
  </div>
</template>

<script>
export default {
  props: {
    type: {type: String, default: 'text'},
    label: {type: String},
    name: {type: String},
    value: {},
    required: {type: Boolean, default: false}
  },
  methods: {
   update (value) {
     var val = ""
     switch(this.type) {
       /** email */
       case 'email':
         val = String(value)
         break;
       /** number */
       case 'number':
         val = Number(value)
         break;
       /** default */
       default:
         val = String(value)
         break;
     }
     this.$emit('input', val)
   }
 }
}
</script>

<style scoped>
  input {
    background-color: #F4EACA;
    border: .14em solid grey;
    border-radius: .2em;
    color: #324E6B;
    display: block;
    font-size: 16px;
    font-weight: bold;
    padding: 6px 10px;
  }
</style>
