<template>
    <div>
        <div class="card">
            <div class="card-header">
                <h4>User List
                    <RouterLink to="/form" class="btn btn-primary">Add User</RouterLink>
                </h4>
            </div>
            <div class="card-body">
                <table class="table table-bordered">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Fullname</th>
                            <th>Email</th>
                            <th>Password</th>
                            <th>Action</th>
                        </tr>
                    </thead>
                    <tbody>

                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'userslist',
    data(){
        return{
            users: []
        };
    },
    mounted(){
        this.getUsers();
    },
    methods: {
        getUsers(){
            axios.get('http://localhost:3000/user').then((res) => {
                this.users = res.data.
                console.log(res)
            }).catch((err) => {
                console.log(err)
            });
        }
    },
}

</script>

<style>

</style>