<template>
  <div class="block" v-if="showBlock" @click="setClickTime">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      startTime: null,
      clickTime: null,
    };
  },
  computed: {
    reactionTime() {
      return this.clickTime - this.startTime;
    },
  },
  methods: {
    setClickTime() {
      this.clickTime = new Date();
      console.log(this.clickTime);
      console.log(this.reactionTime);
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
  },
  updated() {
    this.startTime = new Date();
    console.log(this.startTime);
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: orangered;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>