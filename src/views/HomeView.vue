<script setup>
import { ref } from 'vue'
import Modal from '../components/CardDialog.vue'

const isModalVisible = ref(false)

function save() {
  isModalVisible.value = true
}

</script>

<template>
  <main class="page">
    <img src="../assets/bg2.webp" class="bg-top" /><img src="../assets/bg3.webp" class="bg-bottom" />
    <div class="save-btn" @click="save">立即领取</div>
  </main>
  <Modal
    :title="'自定义卡片标题'"
    :content="'自定义卡片内容'"
    :visible="isModalVisible"
    @close="isModalVisible = false"
  />
</template>

<style>
.page {
  height: 100vh;
  /* background: url('../assets/bg2.webp') no-repeat; */
  background-size: 100%;
  font-size: 0;
  overflow: hidden;
}

.bg-top, .bg-bottom {
  width: 100%;
}

.save-btn {
  width: 200px;
  height: 50px;
  line-height: 50px;
  background-color: #ff6700;
  text-align: center;
  font-size: 24px;
  color: white;
  border-radius: 4px;
  margin: 30px auto;
  position: fixed;
  bottom: 25vh;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 10px;
  border: 1px solid #ccc;
}
</style>
