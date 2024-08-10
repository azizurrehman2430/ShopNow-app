<template>
  <div class="image-swapper">
    <div class="big-image-container">
      <img :src="currentImage.src" alt="Big Image" class="big-image"/>
      <div class="overlay">
        <div class="text-container">
          <div class="image-text">{{ currentImage.description }}</div>
          <button class="buy-now-btn">Buy Now</button>
        </div>
        <div class="thumbnails-container">
          <div
            v-for="(image, index) in images"
            :key="index"
            class="thumbnail"
            @click="swapImages(index)"
          >
            <img :src="image.src" alt="Thumbnail Image" class="small-image"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        { src: '1.jpg', description: 'There you brought every branded mobile' },
        { src: '2.jpg', description: 'Description for image 2' },
        { src: '3.jpg', description: 'Description for image 3' }
      ],
      currentIndex: 0
    }
  },
  computed: {
    currentImage() {
      return this.images[this.currentIndex];
    }
  },
  methods: {
    swapImages(index) {
      this.currentIndex = index;
    }
  }
}
</script>

<style scoped>
.image-swapper {
  width: 100%;
  height: 100vh;
  position: relative;
}

.big-image-container {
  width: 100%;
  height: 90%;
  position: relative;
}

.big-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 20px;
  box-sizing: border-box;
}

.text-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  height: 50%;
  max-width: 50%;
}

.image-text {
  color: white;
  /* background-color: rgba(0, 0, 0, 0.3); Transparent background */
  padding: 15px;
  border-radius: 5px;
  margin-left: 1rem;
  text-align: center;
  margin-top: 170px;
  width: 100%;
}

.buy-now-btn {
  align-items: center;
  margin-top: 15px;
  padding: 10px 20px;
  background-color: #ff6600;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-left: 10rem;
  transition: background-color 0.3s;
}

.buy-now-btn:hover {
  background-color: #ff4500;
}

.thumbnails-container {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
}

.thumbnail {
  cursor: pointer;
}

.small-image {
  width: 70px;
  height: 100px;
  border: 2px solid white;
  border-radius: 5px;
  transition: transform 0.2s;
}

.small-image:hover {
  transform: scale(1.1);
}

/* Responsive styling */
@media (max-width: 600px) {
  .big-image-container {
    height: 50%;
    margin-bottom: 5px;
  }

  .text-container {
    
    max-width: 90%;
    height: auto;
    align-items: center;
    padding: 10px;
  }

  .image-text {
    margin-top: 6rem;
    margin-right: 5rem;
    font-size: 14px;
  }

  .buy-now-btn {
    /* font-size: 12px; */
    margin-left:0rem;
    padding: 6px 16px;
    font-size: 14px;
    display: flex;
    margin-top: 1px;
  }

  .small-image {
    width: 70px;
    height: 75px;
  }
}
</style>
