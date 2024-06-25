<template>
  <q-layout view="hHh lpR fFf">
    <q-drawer show-if-above elevated class="text-white" side="left" width="250px">
      <q-list>
        <q-item clickable tag="router-link" to="/">
          <q-item-section>
            <q-item-label
            style="
            font-weight: 700;
            font-size: 50px;
            margin: 0 auto;">☁️</q-item-label>
          </q-item-section>
        </q-item>
        <q-expansion-item 
        style="
        font-size: 20px;
        color:#373A40;
        font-weight: 400;"
        label="Tugas" expand-separator>
          <q-list>
            <q-item clickable tag="router-link" to="/tugas1">
              <q-item-section>
                <q-item-label>Tugas 1</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable tag="router-link" to="/tugas2">
              <q-item-section>
                <q-item-label>Tugas 2</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable tag="router-link" to="/tugas3">
              <q-item-section>
                <q-item-label>Tugas 3</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable tag="router-link" to="/tugas4">
              <q-item-section>
                <q-item-label>Tugas 4</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable tag="router-link" to="/tugas5">
              <q-item-section>
                <q-item-label>Tugas 5</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable tag="router-link" to="/tugas6">
              <q-item-section>
                <q-item-label>Tugas 6</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-expansion-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

</script>

<style scoped>
#app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  text-align: center;
}

.no-scroll {
  overflow: scroll;
}

.q-layout {
  background-color:white; 
  background-size: cover;
  background-position: center;
}

.q-item:hover {
  font-weight: 700;
  background-color: #FF6969;
  color:white;
}

.q-btn.red-btn .q-btn__content {
  background-color: red;
  color: white;
}

.q-btn.search-btn .q-btn__content {
  text-transform: none;
}

.text-center {
  text-align: center;
}

.q-page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  padding: 0;
}

.q-page-container {
  overflow: hidden;
}

</style>
