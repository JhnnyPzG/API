<template >
  <div>
    <div id="lignes" class="container-col">
      <div id="image" @click="characterData = true" 
      v-bind:style="{ backgroundImage: 
      'url(' + character.thumbnail.path + '.' + character.thumbnail.extension + ')' }">
      </div>
      <div id="nom" class="container-row">
        <h1 @click="characterData = false">{{character.name}}</h1>
      </div>
    </div>

    <div class="modal-body" v-if="characterData" id="modal">
      <div style="margin: 4px">

        <div>{{character.description}}</div>

        <div style="height: 8px;"></div>

        <div style="color:brown">
          <div> Comics: {{character.comics.available}}, Series: {{character.series.available}}</div>
          <div> Historias: {{character.stories.available}}, Eventos: {{character.events.available}}</div>
        </div>

        <div style="height: 8px;"></div>

        <div >Nombres de algunos eventos:</div>

        <div v-for="serie in character.series.items.slice(0, 3)" :key="serie.name">{{serie.name}} </div>

        <div style="height: 10px;"></div>

        <div>
          <button @click="characterData=false" type="button" class="btn btn-secondary" data-dismiss="modal">Cerrar</button>
        </div>      
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name : "Personaje",
  props: {
    character: {
      type: Object,
    }
  },
  data() {
    return {
      characterData: false
    }
  }
}
</script>

<style>
.container-row {
  display : flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.container-col {
  display : flex;
  flex-direction: column;
  margin: 6px;
}

#lignes{
  width:250px;
  height:300px; 
  border-radius: 10px;
}

#lignes:hover{
    border: 2px solid #e92227;
}

#image {
  width: 100%;
  height: 100%;
  background-size: cover;
  border-radius: 10px 10px 0px 0px;
  border: 1px solid rgba(180, 180, 180, 0.781);
}

#nom {
  background-color:white;
  border: 1px solid rgba(180, 180, 180, 0.781);
  width: 100%;
  height: 80px;
  border-radius: 0px 0px 10px 10px;
}


h1{
  font-size: 20px;
  height: auto;
  text-align: center;
  color:black;
}

h1:hover{
  font-size: 25px;
  color:#e92227;
}

#modalName{
  font-size: 25px;
  text-align: center;
  color:black;
  height: 80px;
}

#modal{
  width: 250px;
  height: auto;
  font-size: 15px;
  background-color: #f1f2f0;
  text-align: center;
  margin-bottom: 20px;
  margin-left: 6px;
  border-radius: 10px 10px 10px 10px;
}

button {
  height: auto;
  width: 100px;
  background-color: #e92227;
  margin-bottom: 5px;
  align-content: center;
  text-decoration-color: rgb(255, 255, 255);
  border-radius: 8px;
}

</style>
