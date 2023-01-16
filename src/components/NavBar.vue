<template>
    <div>
        <b-navbar type="dark" variant="dark">
            <b-navbar-nav>
                <img alt="Vue logo" src="../assets/logo.png">
                <b-nav-item><router-link class="nav-link" to="/">Home</router-link></b-nav-item>
                <b-nav-item><router-link class="nav-link" to="/create">Create post</router-link></b-nav-item>
                <b-nav-item><router-link class="nav-link" to="/tricks">Tricks</router-link></b-nav-item>
                <b-nav-item><router-link class="nav-link" to="/beginner">Beginner</router-link></b-nav-item>
            </b-navbar-nav>
        </b-navbar>
    </div>
</template>

<script>
    export default {
        name: 'NavBar',
        components: {
            
        }
    }
</script>

<style>
    img{
     width: 50px;
    }
</style>