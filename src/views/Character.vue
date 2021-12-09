<template>
    <div>
        <p>Nom: {{this.character.name}},<br>
          Poids: {{this.character.mass}}, <br>
          Couleur des yeux: {{this.character.eye_color}}
        </p>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Character',
  
    data() {
        return {
            character: {},
        }
    },
    created() {
        if (this.$route.params.id) {
            axios.get("https://swapi.dev/api/people/" + this.$route.params.id + "/")
            .then(res => {
                this.character = res.data
            })
        }
    }
}
</script>