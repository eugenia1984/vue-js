<template>
  <div>
    <Nav />
    <MainHeader />
    <Presentation oriented="left" />
    <Presentation oriented="right" />
    <Stats />
    <Tabs />
    <Footer />
  </div>
</template>

<script setup>
import { MainHeader, Nav, Presentation, Stats, Tabs, Footer } from "../components";
</script>
