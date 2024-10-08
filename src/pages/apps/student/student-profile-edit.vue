<script setup lang="ts">
import { reactive } from "vue";

definePage({
  meta: {
    layout: "master-student",
  },
});

const profile = reactive({
  firstName: "POM",
  lastName: "Mouylang",
  gender: "F",
  dateOfBirth: "2002-04-23",
  id: "e20201008",
  position: "Software Engineering",
  department: "GIC",
  username: "admin",
  password: "12345678",
  telephone: "086 318 261",
  email: "e20201008@itc.edu.kh",
  address: "Phnom Penh",
  pic: "https://p16-va.lemon8cdn.com/tos-alisg-v-a3e477-sg/7b06a6982a31403eacc7c9d5826731fd~tplv-tej9nj120t-origin.webp",
});

const saveProfile = () => {
  console.log("Profile saved:", profile);
};

const handleFileUpload = (event: Event) => {
  const input = event.target as HTMLInputElement;
  if (input.files && input.files[0]) {
    const reader = new FileReader();
    reader.onload = (e) => {
      profile.pic = e.target?.result as string;
    };
    reader.readAsDataURL(input.files[0]);
  }
};
</script>

<template>
  <div class="profile-management">
    <div class="bar-style-top">
      <div class="ml-3">Profile</div>
      <router-link to="/apps/student/student-profile-view">
        <button type="submit" class="add-button" @click="saveProfile">
          Save
        </button>
      </router-link>
    </div>
    <div class="edit-section">
      <div class="body">
        <form @submit.prevent="saveProfile">
          <div class="form-row-body">
            <div class="profile-pic-container">
              <img
                :src="
                  profile.pic ||
                  'https://p16-va.lemon8cdn.com/tos-alisg-v-a3e477-sg/7b06a6982a31403eacc7c9d5826731fd~tplv-tej9nj120t-origin.webp'
                "
                alt="Profile Picture"
              />
              <label for="profilePic" class="upload-button">
                Upload Picture
                <input type="file" id="profilePic" @change="handleFileUpload" />
              </label>
            </div>
            <div class="form-col-body">
              <div class="form-row">
                <div class="form-group">
                  <label for="firstName">First Name</label>
                  <input
                    type="text"
                    id="firstName"
                    v-model="profile.firstName"
                    placeholder="First Name"
                  />
                </div>
                <div class="form-group">
                  <label for="lastName">Last Name</label>
                  <input
                    type="text"
                    id="lastName"
                    v-model="profile.lastName"
                    placeholder="Last Name"
                  />
                </div>
                <div class="form-group">
                  <label for="gender">Gender</label>
                  <input
                    type="text"
                    id="gender"
                    v-model="profile.gender"
                    placeholder="Gender"
                  />
                </div>
                <div class="form-group">
                  <label for="dob">Date of Birth</label>
                  <input type="date" id="dob" v-model="profile.dateOfBirth" />
                </div>
              </div>
              <div class="form-row">
                <div class="form-group">
                  <label for="id">ID</label>
                  <input
                    type="text"
                    id="id"
                    v-model="profile.id"
                    placeholder="ID"
                  />
                </div>
                <div class="form-group">
                  <label for="position">Position</label>
                  <input
                    type="text"
                    id="position"
                    v-model="profile.position"
                    placeholder="Position"
                  />
                </div>
                <div class="form-group">
                  <label for="department">Department</label>
                  <input
                    type="text"
                    id="department"
                    v-model="profile.department"
                    placeholder="Department"
                  />
                </div>
              </div>
              <div class="form-row">
                <div class="form-group">
                  <label for="telephone">Telephone</label>
                  <input
                    type="tel"
                    id="telephone"
                    v-model="profile.telephone"
                    placeholder="Telephone"
                  />
                </div>
                <div class="form-group">
                  <label for="email">Email</label>
                  <input
                    type="email"
                    id="email"
                    v-model="profile.email"
                    placeholder="Email"
                  />
                </div>
              </div>
              <div class="form-row">
                <div class="form-group">
                  <label for="username">Username</label>
                  <input
                    type="text"
                    id="username"
                    v-model="profile.username"
                    placeholder="Username"
                  />
                </div>
                <div class="form-group">
                  <label for="password">Password</label>
                  <input
                    type="password"
                    id="password"
                    v-model="profile.password"
                    placeholder="Password"
                  />
                </div>
              </div>
              <div class="form-row">
                <div class="form-group">
                  <label for="address">Address</label>
                  <input
                    type="text"
                    id="address"
                    v-model="profile.address"
                    placeholder="Address"
                  />
                </div>
              </div>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Battambang:wght@100;300;400;700;900&display=swap");

.profile-management {
  max-width: 100%;
  margin: 0 auto;
  padding: 20px;
  font-family: "Battambang", sans-serif;
}

.edit-section {
  background: white;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
}

.profile-pic-container {
  text-align: center;
  margin-bottom: 0;
  width: 40%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.profile-pic-container img {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
}

.upload-button {
  display: inline-block;
  margin-top: 10px;
  padding: 5px 10px;
  color: #203e61;
  border-radius: 5px;
  cursor: pointer;
  font-size: medium;
  font-weight: bold;
}

.upload-button:hover {
  background-color: #203e61;
  color: white;
}

.profile-pic-container input[type="file"] {
  display: none;
}

.form-row {
  display: flex;
  justify-content: space-between;
  gap: 20px;
}

.form-row-body {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.form-col-body {
  width: 60%;
}

.form-group {
  flex: 1;
}

.form-group label {
  display: block;
  margin-bottom: 0;
  font-weight: normal;
  color: #203e61;
  padding-left: 5px;
  padding-top: 10px;
}

.form-group input,
.form-group select {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-sizing: border-box;
  font-family: "Battambang", sans-serif;
  font-size: 12px;
}

.bar-style-top {
  display: flex;
  background-color: #203e61;
  justify-content: space-between;
  color: white;
  padding: 10px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  font-size: 18px;
  align-items: center; /* Fixed alignment issue */
}

button {
  width: 100px;
  background-color: white;
  border: #203e61;
  border: none;
  cursor: pointer;
  font-weight: bold;
  font-family: "Battambang", sans-serif;
  border-radius: 20px;
  text-align: center;
  height: 30px;
}

button:hover {
  background-color: lightgrey;
  color: #203e61;
}

.body {
  width: 95%;
  margin: 30px auto;
}

input {
  color: #203e61;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-sizing: border-box;
  font-family: "Battambang", sans-serif;
  font-size: 12px;
}

#dob {
  height: 43.2px;
}
</style>
