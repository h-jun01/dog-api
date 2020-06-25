<template>
  <div class="label">
    <label v-for="(item, i) in list" :key="i" @change="searchapi()" id="labelWrap">
      <input v-model="dogname" :value="i" type="radio" />
      <div class="wrap">{{ i }}</div>
    </label>
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  data() {
    return {
      dogname: ""
    };
  },
  mounted() {
    this.$store.dispatch("getlist");
  },
  methods: {
    searchapi: function() {
      this.$store.dispatch("searchapi", this.dogname);
    }
  },
  computed: {
    ...mapGetters(["list"])
  }
};
</script>

<style lang="scss" scoped>
input[type="radio"] {
  display: none;
}
.wrap {
  display: block;
  float: left;
  margin: 5px;
  width: 150px;
  height: 45px;
  padding-left: 5px;
  padding-right: 5px;
  color: #b20000;
  text-align: center;
  line-height: 45px;
  cursor: pointer;
  border: 2px solid #006dd9;
  border-radius: 5px;
}
input[type="radio"]:checked + .wrap {
  background: #31a9ee;
  color: #ffffff;
}
.clickClass {
  background: #006dd9;
  color: #fff;
}
</style>
