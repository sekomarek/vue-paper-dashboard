<template>
  <table class="table" :class="tableClass">
    <thead>
    <slot name="columns">
      <th v-for="column in columns" :key="column">{{column}}</th>
      <th>Action</th>
    </slot>
    </thead>
    <tbody>
    <tr v-for="(item, index) in data" :key="index">
      <slot :row="item">
        <td v-for="(column, index) in columns"
            :key="index"
            v-if="hasValue(item, column)"z>
          {{itemValue(item, column)}}
        </td>
        <td><p-button size="sm" type="info" round>Edit profile</p-button></td>
      </slot>
    </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  name: 'robots-table',
  props: {
    columns: Array,
    data: Array,
    type: {
      type: String, // striped | hover
      default: "striped"
    },
    title: {
      type: String,
      default: ""
    },
    subTitle: {
      type: String,
      default: ""
    }
  },
  computed: {
    tableClass() {
      return `table-${this.type}`;
    }
  },
  methods: {
    hasValue(item, column) {
      return item[column.toLowerCase().replace(/ /g,"_")] !== "undefined";
    },
    itemValue(item, column) {
      return item[column.toLowerCase().replace(/ /g,"_")];
    }
  }
};
</script>
<style>
</style>
