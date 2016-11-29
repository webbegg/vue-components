<template>
    <div class="form-group">
        <label :for="name">{{label}} <span class="label label-danger" v-if="required"><i class="fa fa-asterisk"></i> requerido</span></label>
        <textarea v-if="type === 'textarea'"
               :name="name"
               @input="update($event.target.value)"
               class="form-control">{{value}}</textarea>
        <input v-if="type !== 'textarea'"
               :type="type"
               :name="name"
               :value="value"
               @input="update($event.target.value)"
               class="form-control">
    </div>
</template>

<script>
export default {
  name: 'input-field',
  props: {
    type: {type: String, default: 'text'},
    label: {type: String, default: '--label--'},
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
  .form-group {
    display: flex;
    flex-direction: column;
  }

  input, textarea {
    flex: 1 1 100%;
    background-color: #fffee5;
    border: .14em solid #cdd0d2;
    border-radius: .2em;
    color: #324E6B;
    display: block;
    font-size: 16px;
    font-weight: bold;
    padding: 6px 10px;
  }
  .label.label-danger {
    font-size: 9px;
  }
</style>
