
<template>
  <footer class="bg-gray-100 mt-auto">
    <div class="container mx-auto px-6 py-8">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
        <!-- Company Info -->
        <div>
          <h3 class="text-lg font-semibold mb-4">Cleaning EDGE</h3>
          <p class="text-gray-600">Professional cleaning services for your home and business.</p>
        </div>
        
        <!-- Dynamic Quick Links -->
        <div>
          <h3 class="text-lg font-semibold mb-4">Quick Links</h3>
          <nav class="flex flex-col space-y-2">
            <router-link 
              v-for="link in quickLinks" 
              :key="link.to" 
              :to="link.to"
              class="text-gray-700 hover:text-primary transition-colors"
            >
              {{ link.text }}
            </router-link>
          </nav>
        </div>

        <!-- Portals Section -->
        <div>
          <h3 class="text-lg font-semibold mb-4">Portals</h3>
          <nav class="flex flex-col space-y-2">
            <router-link to="/login" class="text-gray-700 hover:text-primary transition-colors">Client Portal</router-link>
            <router-link to="/worker/login" class="text-gray-700 hover:text-primary transition-colors">Worker Portal</router-link>
            <router-link to="/management/login" class="text-gray-700 hover:text-primary transition-colors">Management Portal</router-link>
          </nav>
        </div>

        <!-- Social Media Section -->
        <div>
          <h3 class="text-lg font-semibold mb-4">Connect With Us</h3>
          <div class="flex space-x-4">
            <a 
              v-for="(link, index) in socialLinks" 
              :key="index" 
              :href="link.url" 
              target="_blank"
              class="text-gray-600 hover:text-primary"
            >
              <i :class="link.iconClass"></i>
            </a>
          </div>
        </div>
      </div>
      
      <!-- Footer Bottom -->
      <div class="border-t border-gray-200 mt-8 pt-8 text-center">
        <p class="text-gray-600">© {{ currentYear }} Cleaning EDGE. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script>
import { computed } from 'vue';

export default {
  name: 'Footer',
  setup() {
    const quickLinks = [
      { to: '/', text: 'Home' },
      { to: '/services', text: 'Services' },
      { to: '/about', text: 'About' },
      { to: '/contact', text: 'Contact' }
    ];

    const socialLinks = [
      { url: 'https://facebook.com/cleaningedge', iconClass: 'fab fa-facebook' },
      { url: 'https://instagram.com/cleaningedge', iconClass: 'fab fa-instagram' },
      { url: 'https://linkedin.com/company/cleaningedge', iconClass: 'fab fa-linkedin' }
    ];

    const currentYear = computed(() => new Date().getFullYear());

    return {
      quickLinks,
      socialLinks,
      currentYear
    };
  }
};
</script>

<style scoped>
footer a {
  transition: color 0.3s ease;
}
</style>
