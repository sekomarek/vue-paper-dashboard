<template>
  <div>
    <table class="table" :class="tableClass">
      <thead>
        <slot name="columns">
          <th v-for="column in columns" :key="column">{{column}}</th>
          <th>Action</th>
        </slot>
      </thead>
      <tbody>
        <tr v-for="(item, index) in filteredData" :key="index">
          <slot :row="item">
            <td v-for="(column, index) in columns" :key="index" v-if="hasValue(item, column)">
              {{itemValue(item, column)}}
            </td>
            <td>
              <p-button size="sm" type="info" round>Edit profile</p-button>
            </td>
          </slot>
        </tr>
      </tbody>

    </table>
    <div class="pb-4 d-flex justify-content-center">
      <p-button size="lg" type="info" simple round v-on:click.native="moreNrOfRows()">Load more</p-button>
    </div>
  </div>

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
      },
      filteredData() {
        return this.data.slice(0, this.nrOfRows)
      }
    },
    data() {
      return {
        nrOfRows: 6
      };
    },
    methods: {
      hasValue(item, column) {
        return item[column.toLowerCase().replace(/ /g, "_")] !== "undefined";
      },
      itemValue(item, column) {
        return item[column.toLowerCase().replace(/ /g, "_")];
      },
      moreNrOfRows() {
        this.nrOfRows = this.nrOfRows + 6;
      }
    }
  };

</script>
<style>
</style>
