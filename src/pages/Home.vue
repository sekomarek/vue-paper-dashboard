<template>
  <div>

    <!-- Buttons -->
    <div class="row">
      <div class="col-md-6 col-xl-3">
        <p-button size="xlg" color="green" block withIcon iconClass="ti-plus">Create a new profile</p-button>
      </div>
      <div class="col-md-6 col-xl-3">
        <p-button size="xlg" color="blue" block withIcon iconClass="ti-list">Load a profile</p-button>
      </div>
      <div class="col-md-6 col-xl-3">
        <p-button size="xlg" block withIcon iconClass="ti-write">Add new test</p-button>
      </div>
      <div class="col-md-6 col-xl-3">
        <p-button size="xlg" block withIcon iconClass="ti-pencil">Edit existing test</p-button>
      </div>
    </div>

    <!-- Robots Table -->
    <div class="row">
      <div class="col-12">
        <card :title="table1.title" :subTitle="table1.subTitle">
          <div slot="raw-content" class="table-responsive">
            <robots-table :data="table1.data" :columns="table1.columns">

            </robots-table>
          </div>
        </card>
      </div>

    </div>
  </div>
</template>
<script>
  import {
    RobotsTable
  } from "@/components";
  const tableColumns = ["Robot name", "Databearer", "Actual profile", "Nr of tests", "Location"];
  const tableData = [{
      id: 1,
      robot_name: "JORDAN-22",
      databearer: "FTTH",
      actual_profile: "FTTH Measurement profile",
      nr_of_tests: 33,
      location: "TLA-RBT-02"
    },
    {
      id: 2,
      robot_name: "JORDAN-24",
      databearer: "FTTH",
      actual_profile: "FTTH Measurement profile",
      nr_of_tests: 18,
      location: "TLA-RBT-01"
    },
    {
      id: 3,
      robot_name: "JORDAN-25",
      databearer: "FTTH",
      actual_profile: "FTTH Measurement profile",
      nr_of_tests: 32,
      location: "ADB-RBT-02"
    },
    {
      id: 4,
      robot_name: "JORDAN-09",
      databearer: "4G",
      actual_profile: "4G Measurement profile",
      nr_of_tests: 28,
      location: "ADB-RBT-01"
    },
    {
      id: 5,
      robot_name: "JORDAN-3G-03",
      databearer: "4G",
      actual_profile: "JORDAN-3G-03",
      nr_of_tests: 26,
      location: "JORDAN"
    },
    {
      id: 6,
      robot_name: "JORDAN-07",
      databearer: "4G",
      actual_profile: "Umniah SIM Comparison",
      nr_of_tests: 20,
      location: "ADB-RBT-03"
    }
  ];
  export default {
    components: {
      RobotsTable
    },
    data() {
      return {
        table1: {
          title: "List of running robots and their measurement profiles",
          subTitle: "Select robot from list below to edit measurement profile",
          columns: [...tableColumns],
          data: [...tableData]
        }
      };
    }
  };

</script>
<style>
</style>
