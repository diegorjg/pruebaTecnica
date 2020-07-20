<template>

<table>
        <tr v-for="(n,i) in 3 " :key="i">
        <td v-for="(n,j) in 3 " :key="j">
        <casilla : token-actual="tokenActual" :ref="'casilla' +i +j"
        @jugado="jugar"
        :fila="i"
        :col="j">
    </casilla>
     </td>
     </tr>

    </table>
    
</template>
    <script>
        export default {

         name : "tablero",
         components:{casilla},
         data :()=>{
         return{
         tokenActual: "X",
         matriz: [["", "", ""],
         ["", "", ""],
         ["", "", ""],]
         }
         },
         metthods:{
             jugar(e){
             this.matriz[e.fila][e.col]=e.tokenJugado
             if(this.verificar(e.tokenJugado)){
             this.$emit("ganado",this)
             }else{
             this.tokenActual=e.tokenJugado== "X" ? "O":"X"
             this.$emit("cambio de turno ", this)
             }



             }




           

         }
        }


