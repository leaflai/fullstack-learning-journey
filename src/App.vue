<script setup>
  import { ref } from 'vue';

  const inputValue = ref('')
  const list = ref([{
    isComplete:false,
    text:"学习"
  }])

  function add(){
    list.value.push({
      isComplete:false,
      text:inputValue.value      
    });
    inputValue.value = "";
  }

  function del(index){
    list.value.splice(index,1)
  }
</script>

<template>
    <div class="todo-app">
        <div class="title">to do</div>
        <div class="todo-form">
            <div class="input-container">
                <input v-model="inputValue" class="input-todo" type="text" placeholder="todo list">
                <button @click = "add" class="input-button">add to do</button>
            </div>
        </div>
        <div v-for="(item,index) in list":class="[item.isComplete?'item completed':'item']">
            <div>
                <input v-model="item.isComplete" type="checkbox">
                <span class="name">{{ item.text }}</span>
            </div>

            <div @click ="del(index)" class="del">del</div>
        </div>
    </div>
</template>

<style scoped>
    .todo-app {
            width: 98%;
            height: 500px;
            background-color: #fff;
            border-radius: 20px;
            margin-top: 40px;
            margin-left: 1%;
            padding-top: 40px;
            box-sizing: border-box;
        }

        .title {
            font-size: 30px;
            font-weight: 700;
            text-align: center;
        }

        .input-container {
            display: flex;
            /* 使用弹性布局排列输入框和按钮 */
            margin-top: 50px;
            /* 距离页面顶部的距离 */
            justify-content: center;
            /* 水平居中 */
        }

        .input-todo {
            border: 1px solid #dfe1e5;
            outline: none;
            padding: 10px;
            /* 输入框的内边距 */
            border: 2px solid #ccc;
            /* 输入框的边框 */
            border-radius: 20px 0 0 20px;
            /* 输入框的圆角 */
            width: 60%;
            /* 输入框的宽度 */
            height: 35px;
        }

        .input-button {
            padding: 10px 20px;
            /* 按钮的内边距 */
            background-color: #007BFF;
            /* 按钮的背景颜色 */
            color: white;
            /* 按钮的文字颜色 */
            border: none;
            /* 按钮没有边框 */
            border-radius: 0 20px 20px 0;
            /* 按钮的圆角 */
            cursor: pointer;
            /* 鼠标悬停时显示手指图标 */
            user-select: none;
        }

        button:hover {
            background-color: #0056b3;
            /* 按钮悬停时的颜色变化 */
        }

        .item {
            display: flex;
            box-sizing: border-box;
            justify-content: space-between;
            width: 75%;
            height: 50px;
            margin: 8px auto;
            padding: 16px;
            border-radius: 20px;
            box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
        }
        .del{
            color: red;
        }
        .completed{
            text-decoration: line-through;
            opacity: 0.4;
        }
</style>
