<template>
  <div class="star">
    {{ hoverCnt }}
    <span
      v-for="(i, idx) in starCnt"
      :key="idx"
      class="px-1"
      :class="{'active': hoverCnt >= idx}"
      @click="selectHandle(idx)"
      @mouseover="hoverHandle(idx)"
      @mouseleave="leaveHandle"
    >
      <i class="fa-solid fa-star" />
    </span>
  </div>
</template>

<script>
export default {
  data () {
    return {
      starCnt: 10,
      selectedCnt: 0,
      hoverCnt: 0
    }
  },
  methods: {
    selectHandle (idx) {
      this.selectedCnt = idx
      this.$emit('selected', this.selectedCnt)
    },
    hoverHandle (idx) {
      this.hoverCnt = idx
    },
    leaveHandle () {
      this.hoverCnt = this.selectedCnt
    }
  }
}
</script>

<style>
  .star {
    color: #ddd;
  }
  .star .active i{
    color: #ebd72d;
  }
</style>
