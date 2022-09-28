<template>
<div class="todo-list">
    <h1>Todo List</h1>
  <input placeholder="New Task" class="text-field" type="text" @change="addToList" v-model="text" />
  <ul>
    <li v-for="(item, index) in list" :key="index">
    
      <span @click="toggleCheckbox(item)" class="list-item">
        <input type="checkbox" :checked="item.done" class="item-checkbox">  
        <span :class="{'done': item.done}">{{ item.label }}</span>
      </span>
      <span @click="deleteFromList(index)" class="list-item"> Delete</span>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  data() {
    return {
      list: [],
      text: "",
    };
  },
  created() {
    this.list = JSON.parse(localStorage.getItem("list")) || [];
  },
  methods: {
    addToList() {
      this.list.unshift({label: this.text, done: false});
      this.uptadeLocalStorage();
      this.text = "";
    },
    deleteFromList(index) {
      this.list.splice(index, 1);
      this.uptadeLocalStorage();
    },
    uptadeLocalStorage() {
      localStorage.setItem("list", JSON.stringify(this.list));
    },
    toggleCheckbox(item) {
        item.done = !item.done
        this.uptadeLocalStorage();
    }
  },
  
};
</script>

<style>

.todo-list {
    max-width: 500px;
    margin: auto;
}

h1 {
    text-align: center;
}

.text-field {
    width: 100%;
    height: 35px;
    margin-bottom: 15px;
    text-align: center;
}
.text-field::placeholder{
    color: rgb(95, 30, 43);
}

ul {
    list-style: none;
    padding: 0;
}

li {
    display: flex;
    justify-content: space-between;    
}

li .list-item {
    display: flex;
    align-items: center;
    cursor: pointer;
}

.done {
    text-decoration: line-through;
}

.item-checkbox {
    margin-right: 10px;
    cursor: pointer;
}

</style>