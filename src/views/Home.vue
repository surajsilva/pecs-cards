<!-- <template>
      <VCard cardImg="/public/cars.jpg" cardTxt="CAR1"/>
      <VCard cardImg="/public/cars.jpg" cardTxt="CAR2"/>
      <VCard cardImg="/public/cars.jpg" cardTxt="CAR3"/>
</template>

<script setup>
  import VCard from '@/components/Card.vue'
</script> -->
<template>
  <EditPanel @close="showPanel = false" />
  <v-app>
    <v-toolbar app color="primary">
      <v-btn @click="addCard">Add</v-btn>
      <v-btn @click="deleteCard">Delete</v-btn>
      <v-btn @click="clearCards">Clear</v-btn>
      <v-btn @click="printCards">Print</v-btn>
    </v-toolbar>

    <v-main id="print">  
      <v-container fluid>
        <v-row dense>
          <v-col v-for="card in cards" :key="card.id" cols="4">
            <VCard :cardImg="card.img" :cardTxt="card.txt" :trf="card.trf" class="mx-2 my-5"/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
  import VCard from '@/components/Card.vue'
  import EditPanel from '@/components/EditPanel.vue'
</script>

<script>
export default {
  data() {
    return {
      showPanel: false,
      cards: [
        {
          id: 1,
          img: "/public/img/computer.jpg",
          txt: "computer"
        },
        {
          id: 2,
          img: "/public/img/pen-skills.jpg",
          txt: "pen skills",
          trf: 270
        },
        {
          id: 3,
          img: "/public/img/reading.jpg",
          txt: "reading"
        },
        {
          id: 4,
          img: "/public/img/ducks.jpg",
          txt: "ducks"
        },
        {
          id: 5,
          img: "/public/img/puzzle.jpg",
          txt: "puzzle"
        },
        {
          id: 6,
          img: "/public/img/red-park.jpg",
          txt: "red park"
        },
        {
          id: 7,
          img: "/public/img/catch-ball.jpg",
          txt: "catch ball",
          trf: 90
        },
        {
          id: 8,
          img: "/public/img/ipad.jpg",
          txt: "ipad",
          trf: 90
        },
        {
          id: 9,
          img: "/public/img/crafts.jpg",
          txt: "crafts",
          trf: 0
        }
      ]
    }
  },
  methods: {
    addCard() {
      this.cards.push({
        id: Math.random().toString(36).substr(2, 9)
      });
    },
    deleteCard() {
      this.cards.pop();
    },
    clearCards() {
      this.cards = [];
    },
    printCards(){
      
      // Get HTML to print from element
      const prtHtml = document.getElementById('print').innerHTML;

      // Get all stylesheets HTML
      let stylesHtml = '';
      for (const node of [...document.querySelectorAll('link[rel="stylesheet"], style')]) {
        stylesHtml += node.outerHTML;
      }

      // Open the print window
      const WinPrint = window.open('', '', 'left=0,top=0,toolbar=0,scrollbars=1,status=0');

      WinPrint.document.write(`<!DOCTYPE html>
      <html>
        <head>
          ${stylesHtml}
        </head>
        <body>
          ${prtHtml}
        </body>
      </html>`);

      WinPrint.document.close();
      WinPrint.focus();
      //WinPrint.print();
      //WinPrint.close();
      
      //this.showPanel = true;
    }
  }
}
</script>
