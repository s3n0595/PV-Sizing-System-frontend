<template>
  <div class="form-container">
    <div class="form-content">
      <el-form ref="elForm" :model="formData" :rules="rules" size="medium" label-width="100px">
        <h1>CREATE PROJECT</h1>
        <!-- 位置 -->
        <div class="tab-header">
          <button type="button"
                  :class="{ active: activeTab === 'address' }"
                  @click="activeTab = 'address'"
          >
            Address
          </button>
          <button type="button"
                  :class="{ active: activeTab === 'coordinates' }"
                  @click="activeTab = 'coordinates'"
          >
            Coordinates
          </button>
        </div>
        <!-- 地址  required必填-->
        <div class="form-group" v-if="activeTab === 'address'">
          <label for="address" class="no-bold">Address</label>
          <el-input v-model="formData.address" placeholder="Enter address" clearable :style="{width: '100%'}">
          </el-input>
        </div>
        <!-- 坐标 -->
        <div class="form-group" v-if="activeTab === 'coordinates'">
          <label for="coordinates" class="no-bold">Coordinates</label>
          <el-input v-model="formData.coordinates" placeholder="Enter coordinates" clearable :style="{width: '100%'}">
          </el-input>
        </div>
        <!--        项目名字-->
        <div class="form-group">
          <label for="coordinates">PROJECT</label>
          <label for="coordinates" class="no-bold">NAME</label>
          <el-input v-model="formData.projectName" placeholder="Enter projectName" clearable :style="{width: '100%'}">
          </el-input>
        </div>
        <div class="form-group">
          <label for="coordinates" class="no-bold">Planned date of installation</label>
          <el-date-picker v-model="formData.installation" format="yyyy-MM-dd" value-format="yyyy-MM-dd"
                          :style="{width: '100%'}" placeholder="Enter installation" clearable></el-date-picker>
        </div>
        <!--        设计方法-->
        <div class="form-group">
          <label for="coordinates" class="no-bold">Design method</label>
          <el-select v-model="formData.method" placeholder="Enter method" clearable :style="{width: '100%'}">
            <el-option v-for="(item, index) in field101Options" :key="index" :label="item.label"
                       :value="item.value" :disabled="item.disabled"></el-option>
          </el-select>
        </div>
        <!--        作者-->
        <div class="form-group">
          <label for="coordinates" class="no-bold">Author</label>
          <el-input v-model="formData.Author" placeholder="Enter Author" clearable :style="{width: '100%'}">
          </el-input>
        </div>

        <!--        顾客-->
        <div class="form-group">
          <label for="coordinates">Customer</label>
          <label for="coordinates" class="no-bold">NAME</label>
          <el-input v-model="formData.customerName" placeholder="" clearable :style="{width: '100%'}">
          </el-input>
        </div>
        <!--        联络人-->
        <div class="form-group">
          <label for="coordinates" class="no-bold">Contact person</label>
          <el-input v-model="formData.contactPerson" placeholder="" clearable :style="{width: '100%'}">
          </el-input>
        </div>
        <!--        项目说明-->
        <div class="form-group">
          <label for="coordinates" class="no-bold">Project notes</label>
          <el-input v-model="formData.projectNotes" placeholder="" clearable :style="{width: '100%'}">
          </el-input>
        </div>
        <!--        标签-->
        <div class="form-group">
          <label for="coordinates" class="no-bold">Tags</label>
          <el-input v-model="formData.Tags" placeholder="Search or add tag" clearable :style="{width: '100%'}">
          </el-input>
        </div>
      </el-form>
    </div>
    <div class="submit-button-container">
      <el-button type="submit" @click="submitForm">Add</el-button>
    </div>

    <!--    <div class="form-content">-->


    <!--      <h1>CREATE PROJECT</h1>-->
    <!--      <form @submit.prevent="submitForm">-->
    <!--        &lt;!&ndash; 项目名称 &ndash;&gt;-->
    <!--        <div class="form-group">-->
    <!--          <label for="projectName">LOCATION</label>-->
    <!--        </div>-->


    <!--        &lt;!&ndash;        项目名字&ndash;&gt;-->
    <!--        <div class="form-group">-->
    <!--          <label for="coordinates">PROJECT</label>-->
    <!--          <label for="coordinates" class="no-bold">NAME</label>-->
    <!--          <input-->
    <!--            type="text"-->
    <!--            id="coordinates"-->
    <!--            v-model="formData.projectName"-->
    <!--            placeholder="projectName"-->
    <!--          />-->
    <!--        </div>-->


    <!--        &lt;!&ndash;        作者&ndash;&gt;-->
    <!--        <div class="form-group">-->
    <!--          <label for="coordinates" class="no-bold">Author</label>-->
    <!--          <input-->
    <!--            type="text"-->
    <!--            id="coordinates"-->
    <!--            v-model="formData.Author"-->
    <!--            placeholder="Author"-->
    <!--          />-->
    <!--        </div>-->
    <!--      </form>-->
    <!--    </div>-->
    <!--    &lt;!&ndash; 提交按钮 &ndash;&gt;-->
    <!--    <div class="submit-button-container">-->
    <!--      <button type="submit" @click="submitForm">Add</button>-->
    <!--    </div>-->
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTab: 'address', // 默认激活的 Tab
      formData: {
        projectName: 'New project',
        customerName: '',
        location: '',
        address: '',
        coordinates: '',
        Author: '',
        method: '',
        contactPerson: '',
        projectNotes: '',
        Tags: '',
        installation: null,
      },
      field101Options: [{
        "label": "1",
        "value": 1
      }, {
        "label": "2",
        "value": 2
      }],
      rules: {
        address: [{
          required: true,
          message: 'Enter address',
          trigger: 'blur'
        }],
        Author: [{
          required: true,
          message: 'Enter Author',
          trigger: 'change'
        }],
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
  display: flex;
  flex-direction: column;
  height: 100vh; /* 占满整个视口高度 */
  //padding: 20px;
  box-sizing: border-box;
}

.form-content {
  flex: 1; /* 占据剩余空间 */
  overflow-y: auto; /* 允许内容滚动 */
  padding-bottom: 20px; /* 为底部按钮留出空间 */
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

.form-content {
  flex: 1; /* 占据剩余空间 */
  overflow: hidden;
  overflow-y: auto; /* 允许内容滚动 */
  padding-bottom: 60px; /* 为底部按钮留出空间 */
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

.submit-button-container {
  flex-shrink: 0; /* 防止按钮区域被压缩 */
  padding: 20px;
  text-align: center;
  margin-bottom: 15%;
}

.submit-button-container button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.submit-button-container button:hover {
  background-color: #0056b3;
}

/* 不加粗的样式 */
label.no-bold {
  font-weight: normal; /* 不加粗 */
}

.tab-pane h3 {
  margin-top: 0;
}
</style>
