<template>
    <h6 class="mb-3">Data User</h6>
    <div class="table-responsive">
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th class="">No</th>
                    <th class="">Name</th>
                    <th class="">Email</th>
                    <th class="">Address</th>
                    <th class="">Company</th>
                    <th class="">Action</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(user, index) in users" :key="user">
                    <td>{{ index + 1 }}</td>
                    <td>{{ user.name }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.address.street }}</td>
                    <td>{{ user.company.name }}</td>
                    <td>
                        <router-link :to="{ 
                            name:'users.show',
                            params: {
                                id: user.id,
                            },
                        }" 
                        class="btn btn-primary btn-sm">
                            detail
                        </router-link>
                    </td>

                </tr>
                <tr>
                    <td colspan="6" class="text-center">-no data-</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from "axios";
export default {
    data() {
        return {
            users: [],
        };
    },
    methods: {
        getUsers() {
            axios.get("/users").then(response => {
                this.isLoading = true;
                this.users = response.data;
            });
        }
    },
    mounted(){
        this.getUsers()
    }
};
</script>