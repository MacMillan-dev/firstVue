<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" name="text" v-model="text" placeholder="Add Task" autocomplete="off">
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input type="text" name="day" v-model="day" placeholder="Add Day & Time" autocomplete="off">
        </div>
        <div class="form-control form-control-check">
            <label>Set reminder</label>
            <input type="checkbox" name="reminder" v-model="reminder">
        </div>
        <input type="submit" value="Save Task" class="btn btn-block">
    </form>
</template>
<script>
    export default{
        name: 'AddTask',
        data(){
            return{
                text:'',
                day:'',
                reminder: false
            }
        },
        methods: {
            onSubmit(e){
                e.preventDefault()

                if(!this.text){
                    alert('Please add task')
                    return
                }

                const newTask = {
                    id: Math.floor(Math.random() * 10000),
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder
                }
                this.$emit('add-task', newTask);
            }
        }
    }
</script>
<style scoped>
.add-form{
    margin-bottom: 40px;
}
.form-control{
    margin: 20px 0;
}
.form-control label{
    display:block;
}
.form-control input{
    width: 100%;
    height:40px;
    margin:5px;
    padding:3px 7px;
    font-size:17px;
}
.form-control-check{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.form-control-check label{
    flex: 1;
}
.form-control-check input{
    flex:2;
    height:20px;
}
</style>