<template>
  <div class="column">
  <h2>{{customTitle}}</h2>
  <!-- <h2>{{title || "Counter"}}</h2> -->
  <!-- <h3>{{count}} <sup>2</sup> = {{getSquareValue()}}</h3> -->
  <h3>{{count}} <sup>2</sup> = {{squareCounter}}</h3>
  <!-- <h3>{{count}} <sup>2</sup> = {{squareCounter}}</h3> -->
  <!-- <h3>{{count}} <sup>2</sup> = {{squareCounter}}</h3> -->
  <!-- <h3>{{count}} <sup>2</sup> = {{squareCounter}}</h3> -->
  <div>
      <!-- <button v-on:click="increase">+1</button> -->
    <!-- ! v-on:click === @click -->
      <button @click="increase">+1</button>
      <button @click="decrease">-1</button>
  </div>
  </div>
</template>

<script>
export default {
    // props: ['title'],
    // props: ['title','start'],
    // props: {
    //     title: String,
    //     start: Number,
    // },
    props: {
        title: String,
        start: {
            type: Number,
            // required: true
            default: 100,
            validator (value){
                return value > 100 //this won't work
                // return value >= 100 //This will work
            }
        }
    },
    name: 'probando',
    data(){
        return {
            // count: 1,
            count: this.start,
            
        }
    },
    methods: {
        getSquareValue() {
            console.log('getSquareValue')
            return this.count * this.count
        },

        increase() {
            // this.count = this.count + 1
            this.count++
        },
        decrease() {
            // this.count = this.count - 1
            this.count--
        },
    },
    computed: {
        // ! Estas propiedades computadas se guardan en el caché, lo que hará más eficiente el proceso
        // ! Solo se llama una vez, y ejecuta solo cuando la variable "count" cambia
        // 
        // https://vuejs.org/guide/essentials/computed.html#basic-example
        squareCounter() {
            console.log('squareCounter')
            return this.count * this.count
        },
        customTitle() {
            console.log('funciona!')
            return this.title || "Counter"
        }
    }

}
</script>

<style>
h3 {
  font-size: 1.2rem;
}

sup {
   color: hsla(160, 100%, 37%, 1);
}

/* I can use the shortcut "Ctrl + Shift + P" to open the Command Palete and write "Sort Lines Ascending" */
/* To sort the properties alphabetically as below */
button {
    background-color: hsla(160, 100%, 37%, 1);
    border-radius: 5px;
    border: none;
    color: #fff;
    cursor: pointer;
    font-size: 1rem;
    font-weight: 500;
    margin: 10px 5px;
    padding: 5px 15px;
    transition: 0.3s ease-in-out;
}

button:hover {
    background-color: #5aa67b;
    transition: 0.3s ease-in-out;
}

.column{
    display: flex;
    flex-direction: column;
}
</style>
