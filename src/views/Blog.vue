<template>
<Titulo texto="Titulo en mi Blog"/>
<button @click="ConsumirApi">Consumir Api</button>
</template>

<script>
import Titulo from '../components/Titulo'
export default {
            components: {
                Titulo
            },
            data() {
                return{
                    articulo: {}
            }
            },
            methods: {
                async consumirArticulo(){
                 try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const objeto = await data.json()
                console.log(objeto)
                this.articulo = objeto
            } catch (error) {
                console.log(error)
            }

            }
},
created(){
        this.consumirArticulo()
    }
}
</script>

<style>

</style>