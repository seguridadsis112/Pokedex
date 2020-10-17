<template>
  <div class="container"><div class="card-container"></div></div>
</template>

<script>
export default {
  mounted() {
    this.generateIDs();
  },
  methods: {
    async generateIDs() {
      for (let i = 1; i <= 160; i++) {
        await this.fetchingInfo(i);
      }
    },
    async fetchingInfo(id) {
      const types = `https://pokeapi.co/api/v2/pokemon/${id}`;
      const poke_types = await fetch(types);
      const data = await poke_types.json();
      this.getInfo(data);
    },
    getInfo(data) {
      //variables
      const body = document.querySelector(".card-container");
      const newCard = document.createElement("div");
      const images = document.createElement("img");
      const insertName = document.createElement("h1");
      const type = document.createElement("p");
      const id = document.createElement("p");
      const pokeType = data.types[0].type.name;
      //data
      images.setAttribute(
        "src",
        `https://pokeres.bastionbot.org/images/pokemon/${data.id}.png`
      );
      insertName.textContent = data.name;
      id.textContent = `ID: ${data.id}`;
      type.textContent = pokeType;
      //injecting classes
      newCard.classList.add("card");
      newCard.classList.add(`${pokeType}`);
      insertName.classList.add("card-title");
      type.classList.add("card-type");
      //making them appear
      newCard.appendChild(images);
      newCard.appendChild(insertName);
      newCard.appendChild(type);
      newCard.appendChild(id);
      body.appendChild(newCard);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>