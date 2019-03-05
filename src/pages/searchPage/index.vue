<template>
    <div>
        <searchBar canuse="true" @handleInput="handleInput"></searchBar>
    </div>
</template>
<script>
import searchBar from "@/components/searchBar";
export default {
  components: {
    searchBar
  },
  methods: {
    handleInput(val){
      console.log(val)
    }
  }
};
</script>
<style lang="scss" scoped>
</style>
