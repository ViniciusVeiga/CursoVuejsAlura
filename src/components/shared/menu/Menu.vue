<template>
    <nav>
        <ul>
            <li v-for="item in rotas" :key="item.id">
                <router-link :to="item.path">{{item.titulo}}</router-link>
            </li>
        </ul>
    </nav> 
</template>

<script>
export default {
    
    props: {        
        rotas: {
            type: Array, 
            required: true
        }
    }
}
</script>

<style>

</style>


