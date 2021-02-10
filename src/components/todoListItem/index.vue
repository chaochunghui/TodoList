<script>
export default {
    data(){
        return{
            edit:null
        }   
    },
    props:{
        index:{
            type:Number,
            required:true
        }
    },
    computed:{
        todo(){
            return this.$store.state.todos[this.index]
        },
        complete:{
            get(){
                return this.todo.complete
            },
            set(val){
                this.$store.commit('UPDATE_TODO',{
                    index:this.index,
                    data:{
                        content:this.todo.content,
                        complete:val
                    }
                })
            }
        }
    },
    methods:{
        destroyHandler(){
            if(confirm(`是否確認刪除 ${this.todo.content} ?`))
            this.$store.commit('DELETE_TODO',this.index)
        },
        editHandler(){
            this.edit = this.todo.content
           // this.cache =this.todo.content
        },
        submitHandler(){
            if(!this.edit) this.destroyHandler()
            this.$store.commit('UPDATE_TODO',{
                 index:this.index,
                    data:{
                        content:this.edit,
                        complete:this.todo.complete
                    }
            })
            this.cancelHandler()
        },
        cancelHandler(){
            this.edit = null
        }
    }
}
</script>
<template src="./template.html"></template>  