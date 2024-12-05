<template>
  <div class="image-container">
    <img :src="image" alt="Image interactive" height="700" />

    <div
      v-for="(arrow, index) in arrows"
      :key="index"
      class="arrow"
      :class="arrow.direction"
      :style="{ top: arrow.top, left: arrow.startX }"
    >
      <div class="line" :style="{ width: arrow.size + 'px' }"></div>

      <div class="tooltip">{{ arrow.label }}</div>
    </div>
  </div>
</template>

<script setup>
import image from '../assets/image-removebg-preview.png';

// Liste des flèches avec position X configurable
const arrows = [
  { label: 'Muscle', top: '20%', startX: '-70px', direction: 'left', size: 60 },
  { label: 'Cœur', top: '27%', startX: 'calc(45% + 20px)', direction: 'right', size: 100 },
  { label: 'Intestins', top: '45%', startX: '-100px', direction: 'left', size: 135 },
  { label: "Poumon", top: '30%', startX: '-50px', direction: 'left', size: 130 },
  { label: 'Artères', top: '75%', startX: 'calc(70% - 20px)', direction: 'right', size: 35  },
  { label: 'Cerveau', top: '7%', startX: '0', direction: 'left', size: 35  },
  { label: 'Squelette', top: '10%', startX: 'calc(70% - 40px)', direction: 'right', size: 35 }
];
</script>

<style scoped>
/* Conteneur principal */
.image-container {
  position: relative;
  display: inline-block;
}

/* L'image */
.image-container img {
  display: block;
}

/* Flèches */
.arrow {
  position: absolute;
  display: flex;
  align-items: center;
  transform: translateY(-50%);
}

/* Flèches à gauche */
.arrow.left {
  flex-direction: row-reverse; /* Inverser l'ordre des éléments */
}

/* Flèches à droite */
.arrow.right {
  flex-direction: row; /* Flèche et texte dans l'ordre normal */
}

/* Ligne de la flèche */
.line {
  height: 2px;
  background-color: red;
  position: relative;
  margin: 0 10px;
}

/* Bulles d'information */
.tooltip {
  background-color: #333;
  color: #fff;
  padding: 5px 10px;
  border-radius: 5px;
  white-space: nowrap;
  font-size: 14px;
  position: relative;
}

/* Triangle sous la bulle */
.tooltip::after {
  content: '';
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border-width: 5px;
  border-style: solid;
}

/* Triangle pour les flèches à gauche */
.arrow.left .tooltip::after {
  left: 100%;
  border-color: transparent transparent transparent #333;
}

/* Triangle pour les flèches à droite */
.arrow.right .tooltip::after {
  right: 100%;
  border-color: transparent #333 transparent transparent;
}
</style>
