<template>
    <h6>Detail User</h6>
    <div class="card">
        <div v-if="!isLoading" class="card-body">
            <h6 class="card-title">
                Nama
            </h6>
            <p class="card-text">{{ user.name }}</p>
            <h6 class="card-title">
                Nama
            </h6>
            <p class="card-text">test</p>
        </div>
        <div v-else class="card-body text-center">
            Loading...
        </div>
    </div>

</template>

<script>
import axios from "axios";
export default {
    props: ["id"],
    data() {
        return {
            user: null,
            isLoading: true,
        };
    },
    methods: {
        getUser() {
            const id = this.$route.params.id;
            axios.get(`/users/${id}`).then(response => {
               this.user = response.data;
               this.isLoading = false;
            });
        },
    },
    mounted(){
        this.getUser()
    },
};
</script>