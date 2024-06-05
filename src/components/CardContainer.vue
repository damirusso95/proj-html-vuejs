<script>
export default {
    data() {
        return {
            // Array di card
            cards: [
                {
                    title: "Bussines english",
                    name: "Preston Marshall",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-1-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Social computing",
                    name: "David Sanders",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-2-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Learn Spanish",
                    name: "Jennie king",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-3-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Basic Marketing",
                    name: "Edward Bowman",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-4-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Android developer",
                    name: "David Sanders",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-5-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Web designing",
                    name: "Jennifer pawell",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-6-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Financial modeling",
                    name: "Edward Bowman",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-12-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Academic english",
                    name: "Dave Robbins",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-8-f-img.jpg', import.meta.url).href
                },
                {
                    title: "Modern psychology",
                    name: "Kathryn Webb",
                    content: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque quod earum possimus. Qui corporis dolores laudantium molestiae maxime.",
                    imgSrc: new URL('../assets/img/course-9-f-img.jpg', import.meta.url).href
                },
            ],
            // Indice di partenza per il gruppo di card da visualizzare
            startIndex: 0,
            // Numero di card da visualizzare per pagina
            cardsPerPage: 3,
            // Timer per il cambio automatico delle card
            timer: null,
        };
    },
    computed: {
        // Card attualmente visibili
        displayedCards() {
            const endIndex = this.startIndex + this.cardsPerPage;
            return this.cards.slice(this.startIndex, endIndex);
        },
        // Calcola il numero totale di gruppi di card per i pallini di navigazione
        totalDots() {
            return Math.ceil(this.cards.length / this.cardsPerPage);
        }
    },
    methods: {
        // Va al gruppo di card precedente
        prevPage() {
            this.startIndex = Math.max(0, this.startIndex - this.cardsPerPage);
        },
        // Va al gruppo di card successivo
        nextPage() {
            const maxIndex = Math.ceil(this.cards.length / this.cardsPerPage) - 1;
            if (this.startIndex + this.cardsPerPage >= this.cards.length) {
                this.startIndex = 0;
            } else {
                this.startIndex = Math.min(maxIndex * this.cardsPerPage, this.startIndex + this.cardsPerPage);
            }
        },
        // Va a un gruppo di card specifico cliccando sul pallino
        goToPage(index) {
            this.startIndex = index * this.cardsPerPage;
        },
        // Inizia il timer per il cambio automatico delle card
        startAutoScroll() {
            this.timer = setInterval(this.nextPage, 4000);
        },
    },
    mounted() {
        // Avvia il cambio automatico delle card quando il componente è montato
        this.startAutoScroll();
    },
};
</script>

<template>
    <div>
        <!-- Contenitore principale del carosello -->
        <div class="container">
            <div class="row">
                <!-- Visualizza le card in blocchi da 3 -->
                <div v-for="(card, index) in displayedCards"  class="card col-4">
                    <!-- Immagine della card -->
                    <img :src="card.imgSrc" alt="">
                    <!-- Titolo della card -->
                    <h2>{{ card.title }}</h2>
                    <!-- nome -->
                    <p>{{ card.name }}</p>
                    <!-- Contenuto della card -->
                    <p>{{ card.content }}</p>
                </div>
            </div>
        </div>

        <!-- Contenitore dei pallini di navigazione -->
        <div class="dots-container">
            <!-- Crea un pallino per ogni gruppo di card -->
            <span v-for="(dot, index) in totalDots"  class="dot"
                :class="{ active: startIndex / cardsPerPage === index }" @click="goToPage(index)"></span>
        </div>
    </div>
</template>

<style scoped>
.card {
    padding: 10px;
    margin-bottom: 10px;
    border: none;
}

/* Stile per il contenitore dei pallini di navigazione */
.dots-container {
    text-align: center;
    margin-top: 10px;
}

/* Stile per i pallini di navigazione */
.dot {
    display: inline-block;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background-color: #2873ff50;
    margin: 0 5px;
    cursor: pointer;
}

/* Stile per il pallino attivo */
.dot.active {
    background-color: #2873ff;
}
</style>
