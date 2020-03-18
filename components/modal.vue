<template>
   <div>
      <div v-if="loading">Loading</div>
      <div class="container" v-else>
         <div class="header">
            <img :src="superhero[id].images.lg" :alt="superhero[id].name" />
         </div>
         <div class="body">
            <h3 class="title">{{ superhero[id].name }}</h3>
            <div class="info">
               <div class="bio">
                  <h4 class="subtitle">Biography</h4>
                  <p>
                     Full Name:
                     {{
                        superhero[id].biography.fullName
                           ? superhero[id].biography.fullName
                           : '-'
                     }}
                  </p>
                  <p>Alignment: {{ superhero[id].biography.alignment }}</p>
                  <p>Alter Egos: {{ superhero[id].biography.alterEgos }}</p>
                  <p>Birthplace: {{ superhero[id].biography.placeOfBirth }}</p>
                  <p>
                     First Appearance:
                     {{ superhero[id].biography.firstAppearance }}
                  </p>
                  <p>Publisher: {{ superhero[id].biography.publisher }}</p>
               </div>

               <div class="stats">
                  <h4 class="subtitle">Powerstats:</h4>
                  <p>
                     Intelligence: {{ superhero[id].powerstats.intelligence }}
                  </p>
                  <p>Strength: {{ superhero[id].powerstats.strength }}</p>
                  <p>Speed: {{ superhero[id].powerstats.speed }}</p>
                  <p>Durability: {{ superhero[id].powerstats.durability }}</p>
                  <p>Power: {{ superhero[id].powerstats.power }}</p>
                  <p>Combat: {{ superhero[id].powerstats.combat }}</p>
               </div>
            </div>
            <button
               @click="refresh()"
               class="button is-medium is-danger is-outlined"
            >
               Refresh
            </button>
         </div>
      </div>
   </div>
</template>

<script>
export default {
   data() {
      return {
         superhero: null,
         loading: true,
         targetUrl:
            'https://cdn.rawgit.com/akabab/superhero-api/0.2.0/api/all.json',
         id: Math.floor(Math.random() * 600),
      }
   },
   computed: {
      console: () => console,
   },
   mounted: function() {
      return this.$axios.$get(this.targetUrl).then(response => {
         this.superhero = response
         this.loading = false
      })
   },
   methods: {
      refresh: function() {
         window.location.reload()
      },
   },
}
</script>

<style lang="scss">
.title {
   font-weight: bold;
   height: max-content;
   margin: 0;
}

.subtitle {
   font-weight: bold;
   margin: 2vw 0;
}

.container {
   display: flex;
   margin: 0;
}

.header {
   width: max-content;
   margin: 0 2vw;
}

p {
   margin: 5px 1vh;
}

.button {
   transition: 0.5s;
   margin: 5vh 0;
}

.info {
   display: inline-flex;
}

img {
   max-height: 80vh;
}

.body {
   display: flex;
   flex-direction: column;
}
</style>
