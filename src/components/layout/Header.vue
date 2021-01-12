<template>
    <header>
        <h1>TodoList</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name:"Header"
}
</script>

<style scoped>
    header{
        background: #333;
        color: #fff;
        text-align: center;
        padding:10px;
    }
    header h1{
        color: #f3f3f3;
        padding-right: 5px; 
    }
    header a{
        color: #fff;
        padding-right:5px;
        text-decoration: none;
    }
    nav{
        color: white;
        padding-right:5px;
        text-decoration: none;
    }
    #nav a.router-link-exact-active {
        color: #42b983;
    }
    #nav {
        padding: 30px;
    }

    #nav a {
        font-weight: bold;
        color: #fff;
    }


</style>