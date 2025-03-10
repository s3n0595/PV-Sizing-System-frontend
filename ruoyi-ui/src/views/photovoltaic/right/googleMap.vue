<template>
  <div class="map-container">
    <div ref="map" class="map"></div>
    <button class="screenshot-btn" @click="captureScreenshot">截图</button>
    <canvas ref="canvas" class="hidden-canvas"></canvas>
  </div>
</template>

<script>
export default {
  name: "GoogleMap",
  data() {
    return {
      map: null,
      mapOptions: {
        center: { lat: 51.5074, lng: -0.1278 }, // 伦敦坐标
        zoom: 12,
        disableDefaultUI: true, // 禁用默认 UI
        gestureHandling: "greedy", // 允许滚动缩放
        mapTypeId: "satellite", // 设置为卫星地图
      },
    };
  },
  mounted() {
    this.loadGoogleMaps();
  },
  methods: {
    loadGoogleMaps() {
      if (window.google && window.google.maps) {
        this.initMap();
      } else {
        const script = document.createElement("script");
        script.src = `https://maps.googleapis.com/maps/api/js?key=AIzaSyDGIMePJUFBn7mamyLdWlCO5Od9wm1g54I`;
        script.async = true;
        script.defer = true;
        script.onload = () => this.initMap();
        document.head.appendChild(script);
      }
    },
    initMap() {
      this.map = new google.maps.Map(this.$refs.map, this.mapOptions);
      this.map.addListener("dblclick", this.captureScreenshot);
    },
    captureScreenshot() {
      const mapElement = this.$refs.map;
      html2canvas(mapElement).then((canvas) => {
        const link = document.createElement("a");
        link.href = canvas.toDataURL("image/png");
        link.download = "map_screenshot.png";
        link.click();
      });
    },
  },
};
</script>

<style scoped>
.map-container {
  position: relative;
  width: 100%;
  height: 100vh;
}
.map {
  width: 100%;
  height: 100%;
}
.screenshot-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  padding: 8px 16px;
  cursor: pointer;
  border-radius: 5px;
  font-size: 14px;
}
.screenshot-btn:hover {
  background-color: #0056b3;
}
.hidden-canvas {
  display: none;
}
</style>
