<template>
  <main>
    <!--Contenedor del formulario y la figura modificable -->
    <form class="form">
      <div>
        <label for="colorDeFondo">Color de fondo</label>
        <input
          v-model="colorDeFondo"
          type="text"
          id="colorDeFondo"
          placeholder="orange"
        />
      </div>
      <div>
        <label for="colorDeTexto">Color de texto</label>
        <input
          v-model="colorDeTexto"
          type="text"
          id="colorDeTexto"
          placeholder="white"
        />
      </div>
      <div>
        <label for="mostrarTexto">Mostrar texto</label>
        <input type="checkbox" id="mostrarTexto" v-model="mostrarTexto" />
      </div>
      <div>
        <label for="RadioBorde">Borde</label>
        <input
          v-model="RadioBorde"
          type="range"
          id="RadioBorde"
          min="0"
          max="100"
        />
      </div>
      <div>
        <label for="contenidoTextual">Contenido texto</label>
        <textarea
          v-model="contenidoTextual"
          id="contenidoTextual"
          rows="4"
        ></textarea>
      </div>
      <div>
        <div><label for="tipografia">Tipografía</label></div>
        <select v-model="tipografia" id="tipografia">
          <option value="cursive">Cursive</option>
          <option value="serif">Serif</option>
          <option value="sans-serif">Sans-serif</option>
          <option value="fantasy">Fantasy</option>
          <option value="monospace">Monospace</option>
        </select>
      </div>
      <div>
        <label for="opacidad">Mostrar Figura</label>
        <input type="checkbox" id="opacidad" v-model="opacidad" />
      </div>
      <div>
        <label>Tamaño de letra</label>
        <div class="radioInput">
          <div
            class="radioItems"
            v-for="fontSize in tamanoDeLetra"
            :key="fontSize"
          >
            <input
              type="radio"
              name="tamanoDeLetra"
              :value="fontSize"
              v-model="tamanoDeLetraSeleccionado"
            />
            <label>{{ fontSize }}</label>
          </div>
        </div>
      </div>
    </form>

    <!-- Figura modificable  -->
    <div
      class="container"
      :style="{
        backgroundColor: colorDeFondo,
        color: colorDeTexto,
        borderRadius: RadioBorde + '%',
        opacity: opacidad ? 0 : 1,
        fontFamily: tipografia,
      }"
      :class="{
        'text-small': tamanoDeLetraSeleccionado === 'small',
        'text-medium': tamanoDeLetraSeleccionado === 'medium',
        'text-large': tamanoDeLetraSeleccionado === 'large',
      }"
    >
      <p v-show="mostrarTexto">{{ contenidoTextual }}</p> <!--muestra y oculta el texto del a figura-->
    </div>
  </main>
</template>

<script>
//style binding
export default {
  name: "App",
  data() {
    return {
      colorDeFondo: "orange",
      colorDeTexto: "black",
      mostrarTexto: false,
      RadioBorde: 5,
      tipografia: "roboto",
      opacidad: false,
      contenidoTextual: "",
      tamanoDeLetra: ["small", "medium", "large"],
      tamanoDeLetraSeleccionado: "small",
    };
  },
};
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  gap: 20px;
}

.form {
  display: flex;
  flex-direction: column;
  border-radius: 10px;
  color: white;
  padding: 2rem;
  width: 400px;
  background-color: #01703e;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.2);
  margin-right: 5rem;
}

.container {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  text-align: center;
  justify-content: center;
  margin-top: 3rem;
  width: 300px;
  height: 300px;
}

.text-small {
  font-size: 1rem;
}

.text-medium {
  font-size: 2rem;
}

.text-large {
  font-size: 4rem;
}

input[type="text"],
input[type="range"],
textarea {
  width: 100%;
  margin-bottom: 0.5rem;
}

textarea {
  resize: vertical;
}

.radioInput {
  display: flex;
  align-items: center;
}

.radioItems {
  margin-right: 1rem;
}

div {
  margin-bottom: 0.5rem;
}
</style>
