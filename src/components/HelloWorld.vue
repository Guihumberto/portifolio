<template>    
<section>
  <div class="container">
    <div class="text-center">
      <v-avatar size="8rem" color="grey">
        <v-icon size="7rem">mdi-account</v-icon>
      </v-avatar>
      <div class="my-2">
        <h1 class="text-h4 font-weight-bold">João Humberto</h1>
        <div class="text-body-2 font-weight-light m-n1">Desenvolvedor Frontend</div>
      </div>
    </div>
    <div class="cardsWrapper">
        <v-card
          class="py-4 card"
          color="surface-variant"
          prepend-icon="mdi-text-box-outline"
          rounded="lg"
          title="Informações Profissionais"
          variant="text"
          max-width="740px"
        >
          <v-overlay
            opacity=".06"
            scrim="primary"
            contained
            model-value
            persistent
          />
          <v-card-text>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt ad, 
              deserunt dolore recusandae nemo voluptatem a consectetur neque porro cupiditate, 
              voluptatibus quidem aspernatur. Vero magnam ipsa minima molestias quaerat eum?
            </p>
          </v-card-text>
        </v-card>
    </div>
    <div class="cardsWrapper">
      <v-card
        v-for="item, i in 6" :key="i"
        class="py-4 card"
        color="surface-variant"
        prepend-icon="mdi-text-box-outline"
        rounded="lg"
        title="Informações Profissionais"
        variant="text"
        width="364px"
      >
        <v-overlay
          opacity=".06"
          scrim="primary"
          contained
          model-value
          persistent
        />
      </v-card>
    </div>
  </div>
</section>
</template>

<script setup>
  //
</script>

<style scoped>
section{
  width: 100vw;
  height: calc(100vh - 40px);
  display: flex;
  align-items: center;
  justify-content: center;
}
.container{
}
.cardsWrapper{
  margin: 0 auto;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  max-width: 760px;
  margin-top: 1em;
  gap: 1rem;
  padding: .5rem;
}
@media (max-width: 760px) {
  .cardsWrapper{
    justify-content: center;
  }
  .card{
    width: 100%;
  }
}
</style>
