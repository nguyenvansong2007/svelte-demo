<script>
  import { page } from "$app/stores";
  import { onMount } from "svelte";
  import {goto } from "svelte/navigation"

  let user = {};
  async function handleSave() {
    let res = await fetch(`http://10.0.2.14:3000/user/${page.params.id}`, {
      method: "PUT",
      body: JSON.stringify(user),
      headers: { "Content-Type": "application/json" },
    });
  }
  if (res.ok) {
    goto("/quanLyNguoiDung");
  } else {
    alert("Error");
  }
  console.log(res);

  onMount(async () => {
    const res = await fetch(`http://10.0.2.14:3000/user/${page.params.id}`);
    user = await res.json();
    console.log(user);
  });
</script>


<form action="" on:submit={handleSave}>
  <label for="full-name">Ho va ten</label>
  <input type="text" name="" id="" bind:value={user.full_name} />
  <label for="username">ten dang nhap</label>
  <input type="text" name="" id="" bind:value={user.username} />
  <label for="email">email</label>
  <input type="email" name="" id="" bind:value={user.email} />
  <label for="password">mat khau</label>
  <input type="password" name="" id="" bind:value={user.password} />
  <button type="submit">Save</button>
</form>
