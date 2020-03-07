<template>
  <v-container fluid>
        <v-card>
            <v-form @submit.prevent="update">
            <v-text-field
                label = "Title"
                v-model="form.title"
                type="text"
                required
            ></v-text-field>

            <vue-simplemde v-model="form.body" ref="markdownEditor" />

            <v-card-actions>
                <v-btn class="ma-2" color="green" dark type="submit">Save
                    <v-icon dark right>mdi-checkbox-marked-circle</v-icon>
                </v-btn>
                <v-btn class="ma-2" color="red" dark @click="cancel">Decline
                    <v-icon dark right>mdi-cancel</v-icon>
                </v-btn>
            </v-card-actions>
            </v-form>
        </v-card>
</v-container>
</template>

<script>
export default {
    data(){
        return {
            form:{
                title:null,
                body:null
            }
        }
    },
    props:['data'],
    mounted(){
        this.form = this.data
    },
    methods:{
        cancel(){
            EventBus.$emit('cancelEditing')
        },
        update() {
            axios.patch(`/api/question/${this.data.slug}`, this.form)
            .then(res => this.cancel())
            .catch(error => console.log(error.response.data))
        },
    }
}
</script>


<style>
    
</style>