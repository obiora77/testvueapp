<template>
  <footer class="techflow-footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-section">
          <h3>TechFlow</h3>
          <p>Innovating the future of technology.</p>
        </div>
        <div class="footer-section">
          <h4>Quick Links</h4>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>Contact Us</h4>
          <p>Email: info@techflow.com</p>
          <p>Phone: +1-234-567-8900</p>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2025 TechFlow. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter'
}
</script>

<style scoped>
   .techflow-footer {
   background: linear-gradient(135deg, var(--primary-700), var(--primary-900));
   color: #fff;
   padding: 2rem 0;
   margin-top: 2rem;
   }
   .container {
   max-width: 1200px;
   margin: 0 auto;
   padding: 0 1rem;
   }
   .footer-content {
   display: flex;
   justify-content: space-between;
   flex-wrap: wrap;
   gap: 2rem;
   }
   .footer-section {
   flex: 1;
   min-width: 200px;
   }
   .footer-section h3 {
   font-size: 1.5rem;
   margin-bottom: 1rem;
   }
   .footer-section h4 {
   font-size: 1.2rem;
   margin-bottom: 1rem;
   }
   .footer-section ul {
   list-style: none;
   padding: 0;
   }
   .footer-section ul li a {
   color: #bbb;
   text-decoration: none;
   }
   .footer-section ul li a:hover {
   color: #fff;
   }
   .footer-bottom {
   text-align: center;
   margin-top: 2rem;
   border-top: 1px solid #333;
   padding-top: 1rem;
   }
</style>