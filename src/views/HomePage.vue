<script setup lang="ts">
import Hero from '@/components/Hero.vue'
import Navigation from '@/components/Navigation.vue'
import About from '@/components/About.vue'
import Projects from '@/components/Projects.vue'
import Experience from '@/components/Experience.vue'
import Testimonials from '@/components/Testimonials.vue'
import Contact from '@/components/Contact.vue'
import Footer from '@/components/Footer.vue'

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    const offset = 80
    const elementPosition = element.getBoundingClientRect().top
    const offsetPosition = elementPosition + window.pageYOffset - offset

    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth',
    })
  }
}
</script>

<template>
  <div class="min-h-screen bg-background">
    <Navigation />

    <main>
      <Hero
        :on-projects-click="() => scrollToSection('projects')"
        :on-contact-click="() => scrollToSection('contact')"
      />
      <About />
      <Projects />
      <Experience />
      <Testimonials />
      <Contact />
    </main>

    <Footer />
  </div>
</template>
