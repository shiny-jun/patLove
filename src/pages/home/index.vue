<template>
    <div>
        <searchBar :canuse="false"></searchBar>
        <current :types="types">
          <div v-for="(type,index) in types" :key="index" :slot="type.value">
            <div>
              1{{type.name}}
           </div>
          </div>
        </current>
    </div>
</template>
<script>
import searchBar from "@/components/searchBar";
import current from "@/components/current";
export default {
  components: {
    searchBar,current
  },
  data() {
    return {
      types: [
        { name: "推荐", value: "recommend" },
        { name: "关注", value: "follow" },
        { name: "狗", value: "dog" },
        { name: "猫", value: "cat" },
        { name: "兔", value: "rabbit" },
        { name: "鼠", value: "rat" },
        { name: "鼠", value: "rat" },
        { name: "鼠", value: "rat" },
      ]
    }
  },
};
</script>
<style lang="scss" scoped>
</style>
