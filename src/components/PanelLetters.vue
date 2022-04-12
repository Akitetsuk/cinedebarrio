

<script>
export default {
    props: ["text", "guessedLetters"],
    data() {
        return {
            title: this.text.toUpperCase().split(" "),
            guessedLettersMayus: this.guessedLetters.map(x => x.toUpperCase())
        }
    }
}
</script>

<template>
    <div class="main">
        <span class="world--panel" v-for="(word, index) in title" :key="index">
            <span class="letter--panel" :class="{ 'empty': letter === ' ' }" v-for="(letter, index) in word"
                :key="index">
                <span class="letter" :class="guessedLettersMayus.includes(letter) ? 'animation':''" v-if="guessedLettersMayus.includes(letter)"> {{ letter }}
                </span>
                <span class="letter" v-else>
                </span>
            </span>
        </span>
    </div>

</template>

<style scoped>
.empty {
    background-color: transparent;
    border: none;
}

.world--panel {
    display: flex;
    text-transform: uppercase;
    flex-wrap: wrap;
}

span.letter {
    display: flex;
    justify-content: center;
    align-items: center;
    text-transform: uppercase;
    font-size: 1.2rem;
    border: black solid 1px;
    background-color: white;
    width: 80px;
    height: 80px;
    text-align: center;
    font-weight: 700;
    transition: 1s all;
   
}

.letter--panel {
    display: flex;
    justify-content: center;
    align-items: center;
    background-image: url("../../public/panel-1letters.png");
    background-size: 100%;
    width: 145px;
    height: 171px;

}

.animation {
  animation-name: animation;
  animation-duration: 1s;
    
}

@keyframes animation {
  from { transform: rotateY(-90deg);}
  to { transform: rotateY(0deg);}
}

</style>