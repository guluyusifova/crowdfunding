<template>
  <div class="title">CrowdFunding</div>
  <div class="totalFunding">Total Funding: ${{ totalRaised }}</div>
  <div class="mainpart">
    <box
      @myEvent="totalFunding"
      v-for="bx in boxdata"
      :projectnum="bx.projectnum"
      :projectgoal="bx.projectgoal"
      :amountraised="bx.amountraised"
      :remainingamount="bx.remainingamount"
    />
  </div>
</template>

<script>
import box from "./components/box.vue";
export default {
  components: {
    box,
  },
  methods: {
    totalFunding(newDonation) {
      this.totalRaised += newDonation;
    },
  },
  data() {
    return {
      totalRaised: 0,
      boxdata: [
        {
          projectnum: "1",
          projectgoal: 1000,
        },
        {
          projectnum: "2",
          projectgoal: 500,
        },
        {
          projectnum: "3",
          projectgoal: 2000,
        },
        {
          projectnum: "4",
          projectgoal: 1500,
        },
      ],
    };
  },
};
</script>
<style scoped lang="scss">
.title {
  color: blue;
  background-color: beige;
  border: 2px solid red;
  border-radius: 5px;
  text-align: center;
  font-size: 30px;
  margin: 0 110px;
}

.totalFunding {
  color: black;
  background-color: beige;
  border: 1px solid black;
  border-radius: 5px;
  text-align: center;
  font-size: 20px;
  margin: 10px 500px;
}

.mainpart {
  display: flex;
  justify-content: center;
}
</style>
