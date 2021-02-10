<template>
  <div>
    <span :class="state === 'active' ? '' : 'complete'">{{content}}</span>
    <button @click="remove">x</button>
    <!-- <button @click="complete">complete</button> -->
    <input type="checkbox" name="" id="" @click="complete" >
  </div>
</template>

<script>
  export default {
    props: {
      content: String,
      id:Number,
      state: {
        type: String,
        default: 'active'
      }
    },
    methods: {
      remove() {
        // console.log(this.id)
        this.$emit('remove',this.id)
      },
      complete(e){
        console.log(e.target.checked)
        if (this.state === 'complete') {
          e.target.checked = false
        }
        if (this.state === 'active') {
          this.$emit('update:state',"complete")
        }else if (this.state === 'complete') {
          this.$emit('update:state',"active")
        }
      }
    },

  }
</script>

<style >
  .complete{
      text-decoration: line-through;
    }

</style>