<template>
  <form class="add-form" @submit="onSubmit">
    <div class="form-control">
        <label>Task</label>
        <input type="text" name="text" placeholder="Tambah Task" v-model="text">
    </div>
    <div class="form-control">
        <label>Tanggal dan Waktu</label>
        <input type="text" name="day" placeholder="Tambah Waktu dan Tanggal" v-model="day">
    </div>
    <div class="form-control-check">
        <label>Pengingat</label>
        <input type="checkbox" name="reminder" v-model="reminder">
    </div>
        <input type="submit" name="Simpan Task" class="btn btn-block">
  </form>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e) {
            // Preventing Reload
            e.preventDefault() 

            // Simple Validation
            if(!this.text) {
                alert('Tolong Tambahkan Task')
                return
            }

            const newTask = {
                // id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask)

            // Clearing Form
            this.text = ''
            this.day = ''
            this.reminder = false
        }
    }
}
</script>

<style scope>

.add-form{
    margin-bottom: 40px;
}

.form-control{
    margin: 20px 0;
}

.form-control label {
    display: block;
}

.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check{
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>