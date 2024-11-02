<template>
  <div v-if="isVisible" class="modal" @click.self="closeModal">
    <div class="modal-content" :class="{ 'show': isVisible }">
        <img class="card" src="../assets/333.png" alt="">
        <div class="btn" @click.self="closeModal">确定</div>
        <div class="btn" @click.self="goList">查看</div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  title: { type: String, default: '卡片标题' },
  content: { type: String, default: '这是卡片的内容。可以在这里添加更多信息。' },
  visible: { type: Boolean, default: false },
})

const emit = defineEmits(['close'])

const isVisible = ref(props.visible)

watch(() => props.visible, (newVal) => {
  isVisible.value = newVal
})

function closeModal() {
  isVisible.value = false
  emit('close')
}

function action() {
  alert('操作按钮被点击！')
}

function goList() {
    window.location.href = 'https://laddertest03.lkcoffee.com/preview?page_id=263&scenarioName=unknown&random=0.31635779886807747'
}
</script>

<style scoped>
.btn {
    width: 100px;
    height: 28px;
    line-height: 28px;
    margin: 10px;
    text-align: center;
    background-color: #000B58;
    color: #fff;
    border: 1px solid #ccc;
    display: inline-block;
}
.modal {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
}

.modal-content {
  position: relative;
  padding: 20px;
  border-radius: 10px;
  width: 80%;
  max-width: 400px;
  text-align: center;
  opacity: 0;
  transform: perspective(600px) rotateX(-20deg) scale(0.5);
  transition: all 0.4s ease;
  animation: zoomIn 0.5s forwards ease-in-out;
}

.modal-content.show {
  animation: zoomIn 0.6s forwards ease-in-out;
}

/* 光效层 */
.glow {
  position: absolute;
  top: -20px;
  left: -20px;
  right: -20px;
  bottom: -20px;
  border-radius: 20px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.4), transparent 70%);
  filter: blur(20px);
  animation: glowEffect 1.5s ease-in-out infinite alternate;
}

/* 氛围光效动画 */
@keyframes glowEffect {
  0% {
    opacity: 0.5;
  }
  100% {
    opacity: 1;
  }
}

/* 3D 弹出特效 */
@keyframes zoomIn {
  0% {
    opacity: 0;
    transform: perspective(600px) rotateX(-20deg) scale(0.5);
  }
  60% {
    opacity: 1;
    transform: perspective(600px) rotateX(10deg) scale(1.05);
  }
  100% {
    opacity: 1;
    transform: perspective(600px) rotateX(0deg) scale(1);
  }
}

.close {
  position: absolute;
  top: 10px;
  right: 15px;
  font-size: 24px;
  cursor: pointer;
}

.card {
    width: 70vw;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  background-color: #ffffff;
}

.card h2 {
  margin: 0 0 10px;
}

.card p {
  margin: 10px 0 20px;
}

.action-button {
  padding: 10px 20px;
  font-size: 14px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  background-color: #4CAF50;
  color: white;
}
</style>
