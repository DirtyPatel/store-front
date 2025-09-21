# Store-Front

The store-front is the Vue.js frontend that allows users to select products and place orders.

## Requirements

- Node.js
- Vue CLI

## Setup Instructions

1. Navigate to the `store-front` directory:
   ```bash
   cd store-front
2. Install Vue CLI 
   ```bash
   npm install @vue/cli-service@latest
3. Install dependencies:
   ```bash
   npm install
4. Run the store-front:
   ```bash
   npm run serve
   ```

- The service will be running on `http://localhost:8080` if installed locally or on `http://<your-vm-public-ip>:8080` if installed on Azure VM

## Important: Required change for Store-Front when running on the VM
In the `Store-Front`, the default code points to `localhost` (your own machine).
When running on the VM, change it to use the VM’s public IP so the browser can reach the backend services.
1. Open `store-front/src/components/OrderForm.vue`
2. Find and replace the two `fetch(...)` calls:
   - Products API
      ```
      - const response = await fetch('http://localhost:3030/products');
      + const response = await fetch('http://<VM-PUBLIC-IP>:3030/products');
      ```
   - Orders API
      ```
      - const response = await fetch('http://localhost:3000/orders'
      + const response = await fetch('http://<VM-PUBLIC-IP>:3000/orders'
      ```
**Why this matters:**
Your browser is running on your laptop, not inside the VM. localhost would point to your laptop, where those services aren’t running. Using the VM’s IP sends requests to the VM’s Order/Product services.