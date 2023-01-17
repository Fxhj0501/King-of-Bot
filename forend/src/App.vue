<template>
  <div>
    <div>Bot昵称：{{ bot_name }}</div>
    <div>Bot评分：{{ bot_rating }}</div>
  </div>
  <router-view> </router-view>
</template>
<script>
import $ from "jquery";
import { ref } from "vue";
export default {
  name: "App",
  setup: () => {
    let bot_name = ref("");
    let bot_rating = ref("");
    $.ajax({
      url: "http://localhost:3000/pk/getBotInfo/",
      type: "get",
      success: (resp) => {
        bot_name.value = resp.name;
        bot_rating.value = resp.rating;
      },
    });
    return {
      bot_name,
      bot_rating,
    };
  },
};
</script>

<style>
</style>
