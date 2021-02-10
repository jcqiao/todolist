<template>
  <div>
    <input type="text" @keyup.enter="addList" v-model="newList">
    <ul>
      <li v-for="item in listItem" :key="item.id">
        <ToDoListItem :content="item.content" :id="item.id" :state="item.state" @remove="remove" :state.sync="item.state"></ToDoListItem>
      </li>
    </ul>
  </div>
</template>

<script>
  import ToDoListItem from "./ToDoListItem";
  export default {
    components: {
      ToDoListItem
    },
    data() {
      return {
        newList:'',
        listItem: [
          {
            id:1,
            content:'list1',
            state: 'active'
          },
           {
            id:2,
            content:'list2',
            state: 'active'
          },
           {
            id:3,
            content:'list3',
            state: 'active'
          }
        ]
      }
    },
    methods: {
      addList() {
        let id = Date.now()
        console.log(this.newList)
        this.listItem.push({
          id,
          content: this.newList
        })
        this.newList = ''
      },
      remove(id) {
        // console.log(id)
        this.listItem = this.listItem.filter(v => {
          return v.id !== id
        })
      }
    },

  }
</script>

<style lang="scss" scoped>

</style>