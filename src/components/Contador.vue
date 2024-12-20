<template>
    <h2>{{encabezado}} :{{ valor2 }}</h2>
    <p>{{numero}} <sup>{{exponente}}</sup>={{ calcularCuadradoComputado}}</p>
    <p>{{numero}} <sup>{{exponente}}</sup>={{ calcularCuadradoComputado}}</p>
   
    <div>
        <button @click="incrementar">+1</button>
        <button @click="decrementar">-1</button>
    </div>
    <div v-if="esVerdad">
        <h1>Feliz Navidad</h1>
    </div>
</template>
 
<script>
export default {
 
    data() {
        return {
            numero: this.valor,
            exponente:2,
            titulo:'Contador'
        }
    },
    methods: {
        calcularCuadrado(){
            console.log('entro a calcular');
            return this.numero*this.numero;
        },
        incrementar(){
            this.numero++;
        },
        decrementar(){
            this.numero--;
        },
        aumentarExponente(){
            this.exponente++;
        }
    },
    computed: {
        calcularCuadradoComputado(){
            console.log('entro a calcular computado');
            return this.numero*this.numero;}
       
        },
        //primera forma de hacerlo props
        // props: ['encabezado', 'valor']
        //segunda forma de hacerlo props
    props: {
        encabezado: {
            type: String,
            required: true,
             validator(value) {
        return value.length > 5 && value.includes('a');
    }
        },
        valor: Number,
        valor2:{
            type:Number,
            required:false,
            default:77,
            validator(value){
              //programo mi validacion bajo mi criterio  y retorno true
              //si es valido para mi 
              // retorno false si no es valido para mi 
                return value <=78;
            }
        },
        esVerdad:{
            type:Boolean,
            required:true
        },
        arreglo:Array,
        fecha:Date,
        objetoPersona:Object
    }
}
</script>
 
<style>
button{
    background-color: #4CAF50;
    border-radius: 5px;
    border: 1px solid white;
    color: white;
    cursor: pointer;
    margin: 0px 5px;
    padding: 5px 15px;
}
button:hover{
    background-color: #c7f3da;
}
 
</style>
 