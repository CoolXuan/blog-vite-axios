<script setup>
import SinglePost from "./SinglePost.vue";
import { onMounted, onUnmounted, onUpdated } from "vue";

onMounted(() => {
  //   alert("页面渲染之前执行,执行完,页面就出来了");
  /** 数据请求 */

});
function delPost(id) {
  let arr = posts.filter(function(posts,post ) {
    //返回符合条件的数组
    console.log("============>",posts,post,id);
    // return post.id !== id
  })
  const data = axios.post("http://localhost:3003/posts", arr);
  if (data.status === 201) {
    router.push("/");
  }
}
// watchEffect()

onUnmounted(() => {
  //   alert("组件注销之前执行,执行完组件就不在页面显示了");
  // better-scroll 销毁掉三方插件实例的一些对象
});

onUpdated(() => {
  // alert("当组件内的内容发生变化, 就会执行这个更新钩子函数");
});

defineProps({
  posts: Array,
});
</script>

<template>
  <div class="post-list">
    <div v-for="post in posts" :key="post.id">
      <SinglePost :post="post" @delPost="delPost(id)" />
    </div>
  </div>
</template>

<style>

</style>
