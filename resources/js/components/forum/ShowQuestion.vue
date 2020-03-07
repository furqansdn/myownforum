<template>
    <v-card>
        <v-container fluid>
        <v-card-title>
            <div>
                <div class="headline">{{ data.title }}</div>
                <span class="grey--text">{{ data.user }} posted {{ data.created_at }}</span>

            </div>
            <v-spacer></v-spacer>
            <v-btn color="green"> 5 Replies </v-btn>
        </v-card-title>

        <v-card-text v-html="body"></v-card-text>
        <v-card-actions v-if="own">
            <v-btn @click="edit">
                <v-icon color="primary">mdi-wrench</v-icon>
            </v-btn>
            <v-btn @click="destroy">
                <v-icon color="red">mdi-cancel</v-icon>
            </v-btn>
        </v-card-actions>
        </v-container>
    </v-card>
</template>

<script>
export default {
    data(){
        return {
            own: User.own(this.data.user_id)
        }
    },
    props:['data'],
    computed:{
        body(){
           return md.parse(this.data.body)
        }
    },
    methods:{
        destroy(){
            axios.delete(`/api/question/${this.data.slug}`)
            .then(res => this.$router.push('/forum'))
            .catch(error => console.log(error.response.data))
        },
        edit(){
            EventBus.$emit('startEditing')
        }
    }
}
</script>