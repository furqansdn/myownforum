<template>
  <v-card>
    <v-card-title primary-title>
        <div>
            <h3 class="headline mb-0">
                <router-link :to="data.path">
                {{ data.title }}
                </router-link>
            </h3>
        </div>
    </v-card-title>
    <v-card-subtitle class="pb-0">{{ data.user }} Post {{ data.created_at }}</v-card-subtitle>

    <v-card-text class="text--primary">
        <div>{{ data.body }}</div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
    props:['data']
}
</script>