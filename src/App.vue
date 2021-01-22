<template>
  <div id="app">
    <div id="nav">
      <router-link to="/all">全部</router-link> |
      <router-link to="/active">未完成</router-link> |
       <router-link to="/complete">已完成</router-link>
    </div>
    <TodoInput />
    <div class="list">
      <TodoListItem v-for="index in todoIndex" :key="index" :index="index"/>
    </div>
  </div>
</template>
<script>
import TodoInput from '@/components/todoinput/index.vue'
import TodoListItem from '@/components/todoListItem/index.vue'
export default {
  components:{
    TodoInput,
    TodoListItem
  },
  computed:{
    todoIndex(){
      return this.$store.getters['todoIndex']
    }
  },
  mounted(){
    this.$store.dispatch('INIT_TODOS')
  }
}
</script>

<style src="@/assets/reset.css"></style>
<style src="@/assets/style.css"></style>
