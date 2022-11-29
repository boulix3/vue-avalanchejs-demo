<script setup lang="ts">
import { Avalanche } from "avalanche/dist"
import type { AVMAPI, KeyChain, KeyPair } from 'avalanche/dist/apis/avm'
const ip: string = "localhost"
const port: number = 9650
const protocol: string = "http"
const networkID: number = 1337
const avalanche: Avalanche = new Avalanche(ip, port, protocol, networkID)
const xchain: AVMAPI = avalanche.XChain()
const keychain: KeyChain = xchain.keyChain()
const keypair: KeyPair = keychain.makeKey()
function GetKeyPair(): string {
  var address = keypair.getAddressString();
  var publicKey = keypair.getPublicKeyString();
  var privateKey = keypair.getPrivateKeyString();
  return address + " - " + publicKey + " - " + privateKey;
}
</script>

<template>
  <div class="greetings">
    <h1>Avalanche JS MakeKey test</h1>
    <h3>{{ GetKeyPair() }}</h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
