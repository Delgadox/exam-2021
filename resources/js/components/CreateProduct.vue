<template>
    <div>
        <h3 class="text-center">Create item</h3>
        <div class="row">
            <div class="col-md-6">
                <form @submit.prevent="additem">
                    <div class="form-group">
                        <label>Name</label>
                        <input type="text" class="form-control" v-model="item.name">
                    </div>
                    <div class="form-group">
                        <label>Text</label>
                        <input type="text" class="form-control" v-model="item.text">
                    </div>
                    <button type="submit" class="btn btn-primary">Create</button>
                </form>
            </div>
        </div>
    </div>
</template>
 
<script>
    export default {
        data() {
            return {
                item: {}
            }
        },
        methods: {
            additem() {
                this.axios
                    .post('http://localhost:8000/api/items', this.item)
                    .then(response => (
                        this.$router.go('/')
                    ))
                    .catch(err => console.log(err))
                    .finally(() => this.loading = false)
            }
        }
    }
</script>