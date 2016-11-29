<template>
    <div class="form-group">
        <label :for="name">{{label}} <span class="label label-danger" v-if="required"><i class="fa fa-asterisk"></i> requerido</span></label>
        <div class="control">
            <select :name="name"
                    class="form-control"
                    @change="update($event.target.value)"
                    :required="required"
            >
                <option v-for="item in items"
                        :value="item.id"
                        :selected="value === item.id"
                >
                    {{ item.description }}
                </option>
            </select>

            <button v-if="onNewClick !== undefined"
                    class="btn btn-default"
                    @click="onNewClick">
                <i class="fa fa-plus"></i> añadir
            </button>
        </div>
    </div>
</template>

<script>
export default {
  name: 'input-field',
  props: {
    label: {type: String, default: '--label--'},
    name: {type: String},
    items: {type: Array, required: true},
    value: {},
    required: {type: Boolean, default: false},
    onNewClick: {type: Function, default: undefined}
  },
  methods: {
   update (value) {
     this.$emit('input', Number(value))
   }
 }
}
</script>

<style scoped>
  .btn {
    margin-left: 6px;
  }
  .form-group {
    display: flex;
    flex-direction: column;
  }
  .control {
    display: flex;
  }
  .label.label-danger {
    font-size: 10px;
  }
  select {
    background-color: #fffee5;
    border: .14em solid #cdd0d2;
    border-radius: .2em;
    color: #324E6B;
    font-size: 16px;
    font-weight: bold;
    padding: 6px 10px;
  }
</style>
