<script setup>

import { ref, onMounted } from 'vue'
import { Client } from 'xrpl'

// Grab XRP testnet wallet address from .env (Vite exposes this at import.meta.env)
const envWallet = import.meta.env.VITE_XRP_TESTNET_WALLET_ADDRESS

const address = ref('')
const balance = ref(null)
const loading = ref(false)
const showAddress = ref(false)

// Load env wallet address if present
onMounted(() => {
  if (envWallet) {
    address.value = envWallet
  }
})

const getXrpBalance = async () => {
  try {
    loading.value = true
    const client = new Client('wss://s.altnet.rippletest.net:51233')
    await client.connect()

    const accountInfo = await client.request({
      command: 'account_info',
      account: address.value,
      ledger_index: 'validated'
    })

    balance.value = accountInfo.result.account_data.Balance / 1_000_000 + ' XRP'
    await client.disconnect()
  } catch (error) {
    console.error('Error getting the XRP wallet balance:', error)
    alert('Failed to get XRP wallet balance')
  } finally {
    loading.value = false
  }
}
</script>

<template>
  <div class="container">
    <div class="logo">  

      <h1><img src="/icon-ripple-xrp-app.png" alt="logo" />Ripple Testnet Transactions App</h1>
    </div>

    <div class="api-key-container">
      <label for="wallet-address">XRP Testnet wallet address:</label>
      <div class="input-wrapper">
        <input      
          :key="showAddress"   
          id="wallet-address"
          :type="showAddress ? 'text' : 'password'"
          v-model="address"
          :readonly="!!envWallet"
          placeholder="Enter your XRP Testnet Wallet Address"
        />
        <button @click="showAddress = !showAddress" class="eye-btn">
          {{ showAddress ? '🔒' : '👁️' }}
        </button>
      </div>
    </div>

    <div class="form">
      <button @click="getXrpBalance" :disabled="loading">
        {{ loading ? 'Loading...' : 'Get Balance' }}
      </button>
    </div>
    <p v-if="balance"><strong>Balance:</strong> {{ balance }}</p>
  </div>
</template>


<style scoped>
#app {
  min-height: 100vh;
  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f9fafb;
  display: block;
  text-align: left;
}

.container {
  max-width: 1000px;
  margin: 2rem auto; /* Center the container horizontally */
  padding: 1.5rem;
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  text-align: left;
}

h2 {
  color: #4f46e5;
  margin-bottom: 1rem;
}

.input-button-wrapper {
  display: flex;
  justify-content: flex-start;
  gap: 1rem;
}

input {
  width: 70%;
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
}

button {
  background-color: #4f46e5;
  color: white;
  border: none;
  padding: 0.6rem 1rem;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

button:hover {
  background-color: #3730a3;
}

p {
  font-size: 1rem;
  color: #333;
  margin-top: 0.8rem;
}

.logo {
  display: block;
  margin: 0 auto;
  text-align: left;
  
}

.logo img {
  width: 80px;
  padding-right: 10px;
}

.form {
  display: flex;
  justify-content: flex-start;
  gap: 1rem;
  margin-top: 1rem;
}

</style>