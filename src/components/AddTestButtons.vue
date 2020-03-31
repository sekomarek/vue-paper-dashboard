<template>
    <div class="row">
        <div class="col-md-4 pt-2 d-flex justify-content-center" v-for="(test, index) in filteredData" :key="index">
            <p-button outline size="xlg">{{test.name}}</p-button>
        </div>
        <div class="col-12 pt-2 pb-2 d-flex justify-content-center">
            <p-button size="lg" type="info" simple round v-on:click.native="moreNrOfButtons()">Load more</p-button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'add-test-buttons',
    props: {
      data: Array,
    },
    computed: {
        filteredData() {
            return this.data.slice(0, this.nrOfButtons)
        }
    },
    data() {
      return {
        nrOfButtons: 3
      };
    },
    methods: {
        moreNrOfButtons() {
            this.nrOfButtons = this.nrOfButtons + 3;
        }
    }
}
</script>

<style>

</style>