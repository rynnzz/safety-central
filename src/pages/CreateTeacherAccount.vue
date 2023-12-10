<template>
    <q-layout>
        <q-page-container>
            <q-header elevated class="header">
              <q-toolbar>
          <img src="~/src/assets/unnamed.png" alt="Logo">
          <h2 style="color: #ea4335; margin-right: 10px;">CPC</h2>
          <h2 style="color: #4285f4;">SAFETY CENTRAL</h2>
          <div class="row" style="margin-left: 500px;">
            <q-btn type="button" color="purple" icon="person"
              style="width: 170px; border-radius: 10px; margin-right: 15px;" label="Admin" />
            <q-btn type="button" class="btn btn-danger" @click="logout" style="width: 155px; border-radius: 30px;"> <svg
                xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-person-walking"
                viewBox="0 0 16 16">
                <path
                  d="M9.5 1.5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0M6.44 3.752A.75.75 0 0 1 7 3.5h1.445c.742 0 1.32.643 1.243 1.38l-.43 4.083a1.75 1.75 0 0 1-.088.395l-.318.906.213.242a.75.75 0 0 1 .114.175l2 4.25a.75.75 0 1 1-1.357.638l-1.956-4.154-1.68-1.921A.75.75 0 0 1 6 8.96l.138-2.613-.435.489-.464 2.786a.75.75 0 1 1-1.48-.246l.5-3a.75.75 0 0 1 .18-.375l2-2.25Z" />
                <path
                  d="M6.25 11.745v-1.418l1.204 1.375.261.524a.75.75 0 0 1-.12.231l-2.5 3.25a.75.75 0 1 1-1.19-.914zm4.22-4.215-.494-.494.205-1.843a1.93 1.93 0 0 0 .006-.067l1.124 1.124h1.44a.75.75 0 0 1 0 1.5H11a.75.75 0 0 1-.531-.22Z" />
              </svg>Sign Out</q-btn>
          </div>
          <div class="nav-bar" style="margin-left: 70px;">
            <q-tabs>
              <li class="nav-item list-unstyled" style="margin-right: 50px;">
                <router-link to="/HomeComponent" class="nav-link text-white" @click="setActiveTab('HomeComponent')"
                  :class="{ active: activeTab === 'HomeComponent' }"><i class="mx-1"><svg
                      xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-house-fill3" viewBox="0 0 16 16">
                      <path
                        d="M8.707 1.5a1 1 0 0 0-1.414 0L.646 8.146a.5.5 0 0 0 .708.708L8 2.207l6.646 6.647a.5.5 0 0 0 .708-.708L13 5.793V2.5a.5.5 0 0 0-.5-.5h-1a.5.5 0 0 0-.5.5v1.293L8.707 1.5Z" />
                      <path d="m8 3.293 6 6V13.5a1.5 1.5 0 0 1-1.5 1.5h-9A1.5 1.5 0 0 1 2 13.5V9.293l6-6Z" />
                    </svg></i>Home</router-link>
              </li>
              <li class="nav-item list-unstyled" style="margin-right: 50px;">
                <router-link to="/AnnouncementsComponent" class="nav-link text-white"
                  @click="setActiveTab('AnnouncementsComponent')"
                  :class="{ active: activeTab === 'AnnouncementsComponent' }"><i class="mx-1"><svg
                      xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-send-fill" viewBox="0 0 16 16">
                      <path
                        d="M15.964.686a.5.5 0 0 0-.65-.65L.767 5.855H.766l-.452.18a.5.5 0 0 0-.082.887l.41.26.001.002 4.995 3.178 3.178 4.995.002.002.26.41a.5.5 0 0 0 .886-.083l6-15Zm-1.833 1.89L6.637 10.07l-.215-.338a.5.5 0 0 0-.154-.154l-.338-.215 7.494-7.494 1.178-.471-.47 1.178Z" />
                    </svg></i>Announcements</router-link>
              </li>
              <li class="nav-item list-unstyled" style="margin-right: 50px;">
                <router-link to="/SchedulesComponent" class="nav-link text-white"
                  @click="setActiveTab('SchedulesComponent')" :class="{ active: activeTab === 'SchedulesComponent' }"><i
                    class="mx-2"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-calendar-week-fill" viewBox="0 0 16 16">
                      <path
                        d="M4 .5a.5.5 0 0 0-1 0V1H2a2 2 0 0 0-2 2v1h16V3a2 2 0 0 0-2-2h-1V.5a.5.5 0 0 0-1 0V1H4V.5zM16 14V5H0v9a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2zM9.5 7h1a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-1a.5.5 0 0 1-.5-.5v-1a.5.5 0 0 1 .5-.5zm3 0h1a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-1a.5.5 0 0 1-.5-.5v-1a.5.5 0 0 1 .5-.5zM2 10.5a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-1a.5.5 0 0 1-.5-.5v-1zm3.5-.5h1a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-1a.5.5 0 0 1-.5-.5v-1a.5.5 0 0 1 .5-.5z" />
                    </svg></i>Schedules</router-link>
              </li>
              <li class="nav-item list-unstyled" style="margin-right: 50px;">
                <router-link to="/ContactsComponent" class="nav-link text-white"
                  @click="setActiveTab('ContactsComponent')" :class="{ active: activeTab === 'ContactsComponent' }"><i
                    class="mx-1"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-telephone-fill" viewBox="0 0 16 16">
                      <path fill-rule="evenodd"
                        d="M1.885.511a1.745 1.745 0 0 1 2.61.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z" />
                    </svg></i>Contacts</router-link>
              </li>
              <li class="nav-item list-unstyled" style="margin-right: 50px;">
                <router-link to="/StudentDirectoryComponent" class="nav-link text-white"
                  @click="setActiveTab('StudentDirectoryComponent')"
                  :class="{ active: activeTab === 'StudentDirectoryComponent' }"><i class="mx-1"><svg
                      xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-person-vcard-fill" viewBox="0 0 16 16">
                      <path
                        d="M0 4a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2zm9 1.5a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 0-1h-4a.5.5 0 0 0-.5.5M9 8a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 0-1h-4A.5.5 0 0 0 9 8m1 2.5a.5.5 0 0 0 .5.5h3a.5.5 0 0 0 0-1h-3a.5.5 0 0 0-.5.5m-1 2C9 10.567 7.21 9 5 9c-2.086 0-3.8 1.398-3.984 3.181A1 1 0 0 0 2 13h6.96c.026-.163.04-.33.04-.5M7 6a2 2 0 1 0-4 0 2 2 0 0 0 4 0" />
                    </svg></i>Student Directory</router-link>
              </li>
              <li class="nav-item list-unstyled" style="margin-right: 50px;">
                <router-link to="/ComposeComponent" class="nav-link text-white" @click="setActiveTab('ComposeComponent')"
                  :class="{ active: activeTab === 'ComposeComponent' }"><i class="mx-1"><svg
                      xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-rocket-takeoff-fill" viewBox="0 0 16 16">
                      <path
                        d="M12.17 9.53c2.307-2.592 3.278-4.684 3.641-6.218.21-.887.214-1.58.16-2.065a3.578 3.578 0 0 0-.108-.563 2.22 2.22 0 0 0-.078-.23V.453c-.073-.164-.168-.234-.352-.295a2.35 2.35 0 0 0-.16-.045 3.797 3.797 0 0 0-.57-.093c-.49-.044-1.19-.03-2.08.188-1.536.374-3.618 1.343-6.161 3.604l-2.4.238h-.006a2.552 2.552 0 0 0-1.524.734L.15 7.17a.512.512 0 0 0 .433.868l1.896-.271c.28-.04.592.013.955.132.232.076.437.16.655.248l.203.083c.196.816.66 1.58 1.275 2.195.613.614 1.376 1.08 2.191 1.277l.082.202c.089.218.173.424.249.657.118.363.172.676.132.956l-.271 1.9a.512.512 0 0 0 .867.433l2.382-2.386c.41-.41.668-.949.732-1.526l.24-2.408Zm.11-3.699c-.797.8-1.93.961-2.528.362-.598-.6-.436-1.733.361-2.532.798-.799 1.93-.96 2.528-.361.599.599.437 1.732-.36 2.531Z" />
                      <path
                        d="M5.205 10.787a7.632 7.632 0 0 0 1.804 1.352c-1.118 1.007-4.929 2.028-5.054 1.903-.126-.127.737-4.189 1.839-5.18.346.69.837 1.35 1.411 1.925Z" />
                    </svg></i>Compose</router-link>
              </li>
              <li class="nav-item list-unstyled">
                <router-link to="/CreateTeacherAccount" class="nav-link text-white"
                  @click="setActiveTab('CreateTeacherAccount')" :class="{ active: activeTab === 'CreateTeacherAccount' }"><i
                    class="mx-2"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-person-fill-add" viewBox="0 0 16 16">
                      <path
                        d="M12.5 16a3.5 3.5 0 1 0 0-7 3.5 3.5 0 0 0 0 7m.5-5v1h1a.5.5 0 0 1 0 1h-1v1a.5.5 0 0 1-1 0v-1h-1a.5.5 0 0 1 0-1h1v-1a.5.5 0 0 1 1 0m-2-6a3 3 0 1 1-6 0 3 3 0 0 1 6 0" />
                      <path
                        d="M2 13c0 1 1 1 1 1h5.256A4.493 4.493 0 0 1 8 12.5a4.49 4.49 0 0 1 1.544-3.393C9.077 9.038 8.564 9 8 9c-5 0-6 3-6 4" />
                    </svg></i>Create Teacher Account</router-link>
              </li>
            </q-tabs>
          </div>
        </q-toolbar>
            </q-header>

            <q-page class="body">
            </q-page>
        </q-page-container>
    </q-layout>
</template>

<script>
import { checkIfUserIsAuthenticated, simulateLogout } from 'src/router/auth.js'
import 'bootstrap/dist/css/bootstrap.min.css'
import 'bootstrap/dist/js/bootstrap.bundle.min.js'

export default {
    data() {
        return {
            activeTab: 'CreateTeacherAccount',
        };
    },
    methods: {
        setActiveTab(CreateTeacherAccount) {
            this.activeTab = CreateTeacherAccount
        },
        logout() {
            simulateLogout()
            this.$router.push({ name: 'LoginComponent' });
        },
        beforeEnter: (to, from, next) => {
            if (checkIfUserIsAuthenticated()) {
                next();
            } else {
                next('/');
            }
        },
    },
}
</script>


<style scoped>
img {
    width: 100px;
    margin-bottom: 20px;
}

.body {
    background-color: #292a2d;
    height: 100vh;
    margin: 0;
    font-family: 'Product Sans', sans-serif;
    color: white;
    display: flex;
}

.header {
    background-color: #1f1f1f;
    color: white;
    width: 100%;
    font-family: 'Product Sans Black', sans-serif;
}

.column {
    width: 50%;
    padding: 10px;
}

.nav-bar {
    font-family: 'Product Sans Medium', sans-serif;
}

.nav-link {
    color: white;
    text-decoration: none;
    padding: 8px;
    transition: background-color 0.3s;
    border-radius: 10px;
}

.nav-link:hover,
.active {
    background-color: #595959;
    color: #ebebeb;
    border-radius: 10px;
}</style>
