<script setup>
import {onMounted} from "vue";
import axios from "axios";

let container = null

onMounted(() => {
  Ext.onReady(function() {
    container = Ext.create('Ext.Panel', {
      renderTo: 'helloWorldPanel',
      height: 900,
      width: 1200,
      title: 'Hello world',
      html: 'First Ext JS Hello World Program'
    });
  });
});
// 重点在你怎么获取之前项目的ext页面元素
axios.get('/existingExtPage.js').then(res=>{
  const newPanel = eval(res.data)
  container.add(newPanel)
  container.doLayout()
})
</script>

<template>
<div class="ctn" id="helloWorldPanel">
  everything is ok!
</div>
</template>

<style scoped>

</style>