<!-- App.svelte -->
<script lang="ts">
  import { invoke } from '@tauri-apps/api/tauri';
  import { writable } from 'svelte/store';

  const network = writable('testnet');

  async function handleSwitch() {
    const newNetwork = $network === 'testnet' ? 'mainnet' : 'testnet';
    network.set(newNetwork);
    await invoke('switch_network', { network: newNetwork });
  }

  function getRpcConfig() {
    return {
      host: '127.0.0.1',
      port: $network === 'mainnet' ? 27486 : 18843,
      user: 'rpcuser',
      password: 'rpcpassword'
    };
  }
</script>

<button on:click={handleSwitch}>
  Switch to {$network === 'testnet' ? 'Mainnet' : 'Testnet'}
</button>

<!-- You can use getRpcConfig() in your components as needed -->

// src-tauri/src/main.rs
use tauri::Manager;

#[tauri::command]
fn switch_network(network: String, app_handle: tauri::AppHandle) {
    // Update the network in your Rust state
    // You might want to store this in a mutex-protected variable or similar
    println!("Switching to network: {}", network);

    // Reconnect to the appropriate RPC here
    // This is where you'd implement the logic to reconnect to the new network
}

fn main() {
    tauri::Builder::default()
        .setup(|app| {
            // Any setup code can go here
            Ok(())
        })
        .invoke_handler(tauri::generate_handler![switch_network])
        .run(tauri::generate_context!())
        .expect("error while running tauri application");
}

