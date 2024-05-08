<template>
    <div class="box">
        <h1> Project  {{ projectnum}}</h1>
        <div> Project goal: ${{projectgoal}} </div>
        <br>
        <div> Amount raised: ${{amountraised}}</div>
        <br>
        <input type="number" placeholder="Enter Amount Here"  v-model="inputValue">  </input>
        <Button @click="calculateAmount"> Donate </Button>
        <br>
        <br>
        <div> Remaining amount needed: ${{remainingamount}}</div>
        <br>
    </div>
</template>

<script>
export default {
    props:["projectnum", "projectgoal"],
    data(){
     return {
        amountraised:0,
        remainingamount: this.projectgoal,
     }
    },
    methods: {
        calculateAmount() {
            this.$emit('myEvent', this.inputValue);
            this.amountraised += this.inputValue
            this.remainingamount = this.projectgoal - this.amountraised
            this.inputValue= ""
        }
    },
 }
</script>

<style scoped lang="scss">
.box {
    border: 1px solid blue;
    border-radius: 5px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.7);
    width: 300px;
    margin: 10px;
    text-align: center;
    
};
</style>