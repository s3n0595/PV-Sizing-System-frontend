<template>
  <div class="form-container">
    <h1>CREATE PROJECT</h1>
    <form @submit.prevent="submitForm">
      <!-- 项目名称 -->
      <div class="form-group">
        <label for="projectName">LOCATION</label>
      </div>

      <!-- 位置 -->
      <div class="tab-header">
        <button
          :class="{ active: activeTab === 'address' }"
          @click="activeTab = 'address'"
        >
          Address
        </button>
        <button
          :class="{ active: activeTab === 'coordinates' }"
          @click="activeTab = 'coordinates'"
        >
          Coordinates
        </button>
      </div>

      <!-- 地址  required必填-->
      <div class="form-group" v-if="activeTab === 'address'">
        <label for="address">Address</label>
        <input
          type="text"
          id="address"
          v-model="formData.address"
          placeholder="Enter address"

        />
      </div>

      <!-- 坐标 -->
      <div class="form-group" v-if="activeTab === 'coordinates'">
        <label for="coordinates">Coordinates</label>
        <input
          type="text"
          id="coordinates"
          v-model="formData.coordinates"
          placeholder="Enter coordinates"
        />
      </div>

      <!-- 提交按钮 -->
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTab: 'address', // 默认激活的 Tab
      formData: {
        projectName: '',
        location: '',
        address: '',
        coordinates: '',
      },
    };
  },
  methods: {
    submitForm() {
      // 在这里处理表单提交逻辑
      // console.log('Form submitted:', this.formData);
      // alert('Form submitted successfully!');
    },
  },
};
</script>

<style scoped>
.form-container {
  //max-width: 400px;
  //margin: 0 auto;
  //padding: 20px;
  //border: 1px solid #ccc;
  //border-radius: 8px;
  //background-color: #f9f9f9;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}



.tab-header {
  display: flex;
  background-color: #646464;
  margin-bottom: 15px;
}

.tab-header button {
  flex: 1;
  padding: 10px;
  border: none;
  background-color: transparent;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s;
}

.tab-header button.active {
  background-color: #007bff;
  color: white;
}

.tab-header button:hover {
  background-color: #0056b3;
  color: white;
}



.tab-pane h3 {
  margin-top: 0;
}
</style>
